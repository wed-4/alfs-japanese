# AFLS(Automated Linux Form Scratch) ドキュメント　非公式日本語訳

Automated Linux From Scratch (ALFS)は、LFSシステムを自動的に構築するプロジェクトである。また、BLFSブックからパッケージをビルドすることもできるが、これには手作業が必要だ。

## ALFSを使う理由

LFSとBLFSの本を2、3回以上読んでいると、自分のシステムに必要なソフトウェアをコンパイルする作業を自動化できることにすぐに気づくだろう。
ALFSの目標は、LFSシステムの作成プロセスを自動化することだ。XMLソースから直接命令を抽出することで、この本にできる限り忠実に従うようになっている。このため、現在の書籍の説明のテストとしても使用できる。

## 導入方法

ALFSの公式実装はjhalfsと呼ばれる。元々はJeremy Huntworkによって作られ、その後Manuel Canales Esparcia、George Boudreau、Thomas Pegg、Pierre Labastieによって開発・保守されている。LFSビルドを自動化する軽量で実用的な方法となっている。これはBashシェルスクリプトで、Gitとxsltprocを利用して、まず『Linux From Scratch』本のXMLソースをダウンロードし、必要なコマンドを抽出して実行可能なシェルスクリプトに配置する。システム上に必要なソース・パッケージがまだない場合は、jhalfsがそれらを取得する。最後に、jhalfsはシェルスクリプトの実行を制御するMakefileを生成し、ビルドがエラーに遭遇した場合のリカバリーを可能にしている。Pierre Labastie氏によってパッケージ管理のフレームワークが追加された。
以下のようなコマンドで入手できる。

    git clone https://git.linuxfromscratch.org/jhalfs.git jhalfs
このコマンドによってjhalfsがgitからダウンロードされる。

## スクリプトの改良
BLFSブックのパッケージのビルドを自動化するALFSの拡張がjhalfsに含まれるようになった。主にブックのレイアウトが標準と異なる場合に、いくつかのスクリプトを編集する必要がある。

