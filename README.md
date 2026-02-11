# 2026年 衆議院選挙 統計分析

2026年衆議院選挙の開票データを用いた統計分析プロジェクトです。

## 公開レポート

**[チームみらいの得票数は統計的に説明できるか — GitHub Pages で公開](https://[username].github.io/2026_shuugiin_senkyo/)**

> GitHub Pages を有効化したら上記 URL の `[username]` をリポジトリオーナーのアカウント名に書き換えてください。
> Settings > Pages > Source: `main` ブランチの `/docs` フォルダを選択。

---

## 分析概要

### 比例代表分析：チームみらい（東京）

**「チームみらいの得票数は統計的に説明できるか」**

2026年衆院選 東京比例ブロックにおいて、チームみらいが獲得した得票数（約81万票、東京全体の約10.6%）と、
選挙直前（2026年1月15日）の時事通信世論調査支持率（0.2%）の乖離を、ベイズ統計で検証します。

| 項目 | 内容 |
|------|------|
| 手法 | ベイズ線形回帰・MCMC・事後予測チェック（PPC） |
| 対象 | 2026年衆院選 東京比例代表ブロック（61市区町村 × 11政党） |
| データ | 東京都選挙管理委員会「令和8年衆議院議員総選挙 比例代表 東京 開票結果」(r08shu_hkai_036.pdf) |
| ソース | `pr_tokyo/report_mirai_r2.Rmd` |

---

## フォルダ構成

```
2026_shuugiin_senkyo/
├── .gitignore
├── README.md
├── 2026_shuugiin_senkyo.Rproj
│
├── docs/                              # GitHub Pages 公開用
│   └── index.html                     # チームみらい分析レポート（自己完結 HTML）
│
├── pr_tokyo/                      # 比例代表分析（メイン）
│   ├── report_mirai_r2.Rmd            # 最新レポートソース
│   ├── modern.css                     # レポート用スタイルシート
│   ├── 2026_衆院選_比例_東京_r.xlsx   # 分析データ（出典: 東京都選管）
│   └── output/
│       └── report_mirai_r2.html       # ローカル確認用 HTML
│
```

---

## レポートの再生成

```r
# pr_tokyo/ をカレントディレクトリにして実行
setwd("pr_tokyo")

# docs/index.html（GitHub Pages 用）を更新
rmarkdown::render("report_mirai_r2.Rmd", output_file = "../docs/index.html")

# ローカル確認用
rmarkdown::render("report_mirai_r2.Rmd", output_dir = "output")
```

---

## 環境

- R 4.x
- 主要パッケージ: `tidyverse`, `readxl`, `ggrepel`, `patchwork`, `knitr`, `kableExtra`, `DT`

---

## データ出典

- **東京都選挙管理委員会**「令和8年衆議院議員総選挙 比例代表 東京 開票結果」
  https://www.r8shugiinsen2.metro.tokyo.lg.jp/ippan/r08shu_hkai_036.pdf
- **時事通信社** 世論調査（2026年1月15日発表）

---

## ライセンス

分析コードは MIT ライセンス。
使用データの二次利用については各データソースの利用規約に従ってください。
