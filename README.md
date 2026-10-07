# XdwToPdf (DocuWorks to PDF Converter)

Fujifilm DocuWorks ファイル (`.xdw`) を PDF 形式へ一括変換する Windows 向けデスクトップアプリケーションです。

---

## 🌟 主な特徴

- **ドラッグ＆ドロップ対応**: ファイルやフォルダを画面にドラッグ＆ドロップするだけで簡単にリスト追加できます。
- **一括・個別変換に対応**: 1ファイル選択時は保存先・ファイル名を個別指定、複数ファイル選択時は保存先フォルダを一括指定して高速変換できます。
- **DocuWorks 印刷連携**: Windows の印刷エンジンおよび Microsoft Print to PDF と連携し、忠実に PDF へ出力します。
- **起動時自動アップデート**: [Velopack](https://velopack.io/) を搭載。最新バージョンを自動チェックし、ワンクリックで最新版へ更新・再起動できます。
- **二重起動防止**: ミューテックス（Mutex）制御により、アプリの複数同時起動によるコンフリクトや予期せぬ動作を防止します。

---

## 💻 動作環境・前提条件

本アプリは、PCにインストールされた DocuWorks の印刷機能（関連付け）を利用して PDF を生成します。そのため、**実行するPCに DocuWorks 環境が必須**となります。

| 項目 | 要件 |
| :--- | :--- |
| **対応OS** | Windows 10 / Windows 11 (64-bit) |
| **必須ソフトウェア** | **富士フイルム DocuWorks**（製品版）<br>または **DocuWorks Viewer Light**（[公式無料ビューア](https://www.fujifilm.com/fb/support/software/docuworks)） |
| **必須Windows機能** | **Microsoft Print to PDF**（Windows 標準機能） |
| **.NET ランタイム** | .NET 8.0 Desktop Runtime |

> [!IMPORTANT]
> **DocuWorks が未インストールの環境について**  
> `.xdw` は富士フイルム独自のファイル形式であるため、DocuWorks（または無料の Viewer Light）がインストールされていない PC では `.xdw` の解析・印刷が行えず、変換が失敗します。必ず事前にインストールをお願いいたします。

---

## 🚀 インストール手順

1. [Releases](../../releases) ページから最新の `XdwToPdfSetup.exe` をダウンロードします。
2. ダウンロードした `XdwToPdfSetup.exe` をダブルクリックして実行します。
3. 自動的にインストールが完了し、デスクトップおよびスタートメニューにショートカットが生成されます。

> [!NOTE]
> **ダウンロード時・起動時の警告について**  
> コード署名未設定のため、Windows SmartScreen やブラウザにより「安全ではない可能性がある」と警告が表示される場合があります。  
> 実行する場合は、画面上の **「詳細情報」➔「実行」**（またはダウンロード保持）を選択してください。

---

## 📖 使い方

1. **ファイル・フォルダの追加**
   - 画面中央の領域へ `.xdw` ファイル（またはフォルダ）をドラッグ＆ドロップします。
   - または「ファイルを選択」ボタンから対象の `.xdw` ファイルを選択します。
2. **変換実行**
   - 「変換実行」ボタンをクリックします。
   - **単一ファイルの場合**: PDF の保存先ファイル名ダイアログが開きます。
   - **複数ファイルの場合**: 変換後 PDF をまとめて保存するフォルダ選択ダイアログが開きます。
3. **処理完了**
   - リスト上のステータスが「完了」になり、指定場所に PDF が生成されます。

---

## 🔄 アプリの更新（アップデート）

「最新バージョンを確認」ボタンを押すことで最新リリースをチェックします。
新バージョンが検出された場合は更新確認ダイアログが表示され、**「はい」** を選択するだけで自動ダウンロード＆再起動が行われ、最新版へ更新されます。

---

## 🛠️ 技術構成 (Tech Stack)

- **Framework**: .NET 8 (WPF)
- **Architecture**: Single-Instance App (`System.Threading.Mutex`)
- **Print Engine**: ShellExecute (`print` / `printto`) + Microsoft Print to PDF
- **Deployment & Update**: Velopack + GitHub Actions CI/CD


