# DESIGN.md — 行政書士 渥美洋行 政策法務研究所

> このファイルはAIエージェントが正確な日本語UIを生成するためのデザイン仕様書です。
> セクションヘッダーは英語、値の説明は日本語で記述しています。

---

## 1. Visual Theme & Atmosphere

- **デザイン方針**: 伝統的で堅実な「信頼感」と、モダンな「先進性」の調和。士業としての厳格さを崩さず、親しみやすさと情報の見やすさを両立させる。
- **密度**: 中〜高密度。公益認定等の複雑な法的手続きを解説するため、情報量は多いが、十分な余白と整然としたグリッドで圧迫感を排除。
- **キーワード**: 信頼（Prestige）、厳格（Strict）、透明感（Glassmorphism）、洗練（Sophisticated）

---

## 2. Color Palette & Roles

色はすべて Tailwind CSS のテーマ設定および実画面のスタイルに基づく。

### Primary（ブランドカラー）

- **Primary / Prestige Gold** (`#C5A059`): ブランドのシンボルカラー。重要な強調、アクセント枠線、ホバー時のインタラクション等に使用。
- **Primary Dim / Gold Hover** (`#B08D47`): ゴールドのホバーまたはトーンを落としたゴールド。

### Neutral（ニュートラルカラー）

- **Text Primary / Dark Navy** (`#0b1c30`): 本文テキスト、主要なヘッダー。黒に近い濃紺を採用し、コントラストを和らげつつ強い信頼感を表現。
- **Text Secondary** (`#45464d`): 補足テキスト、ラベル。
- **Background** (`#f8f9ff`): ページ背景。わずかに青みがかった白を採用し、清潔感とデジタルな見やすさを両立。
- **Surface / White** (`#ffffff`): カード、モーダル等の背景。
- **Surface Slate** (`#F8FAFC`): 薄いグレー背景のセクション用。

### Semantic（意味的な色）

- **Error** (`#ba1a1a`): 警告、エラー。

---

## 3. Typography Rules

### 3.1 和文フォント

- **ゴシック体**: `Noto Sans JP` (Google Fonts), `Hiragino Kaku Gothic ProN` (Mac), `Meiryo` (Windows)
- ※ 明朝体は読みやすさとモダンなトーンを重視するため、Webサイト内では原則として使用しない。

### 3.2 欧文フォント

- **サンセリフ**: `Helvetica Neue`, `Arial` (システム標準)
- ※ **注意**: 本サイトでは欧文に `Jost` などのオープンフォントを**あえて指定していません**。公的機関の手続きを扱う士業サイトとしての厳格さを保ち、不要な装飾性を抑え、どのような環境でも意図通りに描画されるようにするためです。

### 3.3 font-family 指定

```css
/* 本文・見出し共通 */
font-family: "Noto Sans JP", "Hiragino Kaku Gothic ProN", "Hiragino Kaku Gothic Pro", "Meiryo", "Helvetica Neue", "Arial", sans-serif;
```

### 3.4 文字サイズ・ウェイト階層

Tailwind CSS のテーマ定義と実実装に基づく階層構造。

| Role | Token | Size | Weight | Line Height | Letter Spacing | 備考 |
|------|-------|------|--------|-------------|----------------|------|
| Display | `display-lg` | 48px | 700 (Bold) | 64px | 0.02em | ヒーローエリアのメインコピー |
| Heading 1 | `headline-lg` | 32px | 700 (Bold) | 44px | 0.01em | セクションの大見出し |
| Heading 1 (Mobile) | `headline-lg-mobile` | 24px | 700 (Bold) | 34px | — | セクションの大見出し（スマホ用） |
| Heading 2 | `headline-md` | 24px | 600 (Semibold) | 36px | — | カード内の見出し等 |
| Body Large | `body-lg` | 18px | 400 (Regular) | 30px | — | 導入文や強調したい段落本文 |
| Body Medium | `body-md` | 16px | 400 (Regular) | 26px | — | 通常の段落本文 |
| Label Medium | `label-md` | 14px | 500 (Medium) | 20px | 0.05em | テーブルのヘッダー、メタ情報等 |
| Label Small | `label-sm` | 12px | 600 (Semibold) | 16px | 0.08em | バッジ、小さな注記、フォームの補助ラベル |

### 3.5 行間・字間

- **日本語本文の行間 (line-height)**: `1.625` 以上 (16px に対し 26px / 18px に対し 30px)。和文は行間を広めにとることで可読性が著しく向上します。
- **日本語本文の字間 (letter-spacing)**: ラベルや見出しには `0.05em`〜`0.08em` を適用し、文字と文字の間に適切な空気感を持たせます。

---

## 4. Component Stylings

### Glassmorphism Panel (ガラス質感カード)

本サイトの最大の特徴である「透明感と洗練」を体現するコンポーネント。

- **Background**: `rgba(255, 255, 255, 0.85)` または `bg-surface-container-lowest/80`
- **Backdrop Filter**: `blur(12px)`
- **Border**: `1px solid rgba(100, 116, 139, 0.2)`
- **Shadow**: `box-shadow: 0 20px 40px -10px rgba(19, 27, 46, 0.05)` (Ambient Shadow)

### Buttons

- **Primary Button (ゴールドグラデーション)**
  - Background: Prestige Gold グラデーション (例: `from-amber-600 to-amber-700` に近い Prestige Gold カスタムカラー)
  - Text: `#ffffff`
  - Border Radius: `rounded-full` (円形)
  - Hover: 少し浮き上がり、背景色の輝度が上がるエフェクト

---

## 5. Layout Principles

Tailwind CSS のカスタムスペーシングトークンに基づく。

### Spacing Scale

- **margin-mobile**: `16px` (モバイル時のコンテナ左右余白)
- **margin-desktop**: `48px` (デスクトップ時のコンテナ左右余白)
- **container-max**: `1200px` (コンテンツエリアの最大幅)
- **gutter**: `24px` (グリッドの列間隔)
- **section-gap**: `80px` (セクション間の縦方向の余白)
- **unit**: `8px` (デザインの基本単位。余白等はすべて 8px の倍数で構築する)

---

## 6. Do's and Don'ts

### Do（推奨）

- フォントスタックには必ず `Noto Sans JP` を最優先で指定する。
- 階層に応じた `letter-spacing` を適用し、詰まった印象を与えないようにする。
- 余白設計には必ず Spacing Scale (8px 単位) を使用する。
- コントラスト比を意識し、暗い背景に薄いテキストなどを置かない（ダークモードの残骸に注意）。

### Don't（禁止）

- **欧文フォントに `Jost` やその他のデザイン性の強いWebフォントを新規で導入しない。**
- 見出し等に明朝体（`Noto Serif JP` 等）を使用しない。
- `letter-spacing` を指定せずに日本語長文を配置しない。
- コンテナ幅 `1200px` を超える固定幅レイアウトを定義しない。
- 原則として、ヘッダー・フッターにコントラストの低い白文字（`text-white` / `dark:text-...`）を白背景上に重ねない。
