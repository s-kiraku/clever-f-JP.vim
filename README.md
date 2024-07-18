## Abstract
This is a fork of [clever-f](https://github.com/rhysd/clever-f.vim), supporting several Japanese *zenkaku* symbols.

## オリジナルからの変更点

### 英字以外の全角記号も半角記号で拾えるように migemo 辞書を拡張

migemo を有効化(`g:clever_f_use_migemo=1`) すると、英字の半角・全角以外にも、句点・読点等の記号も半角・全角が区別されなくなる。具体的には、
- `1` は `1` 自身と、全角の `１` にマッチ
- `.` は `.` 自身と、全角の `．` とさらに `。` にマッチ
- `!` は `!` 自身と、全角の `！` にマッチ
- `(` は `(` 自身と、全角の `（` と さらに `「` と、`【`、`〈`、`『` にマッチ
- `-` は `-` 自身と、全角の `ー` と `─` にマッチ
等。すべての設定は [autoload/clever_f/migemo/utf8.vim] 参照。

### `g:clever_f_chars_match_any_signs` にユーザ独自の設定を追加可能に

`g:clever_f_additional_signs` に任意の記号列を指定することで、`g:clever_f_chars_match_any_signs` を有効化している時に、それらもマッチするようになる。

例えば以下の設定を行っているとき
```
let g:clever_f_chars_match_any_signs=';'
let g:clever_f_additional_signs='「」。、…？！（）【】〈〉'
```
`<cursor>「【特売日！】」` に対して `f;` はそれぞれ `「` と、`【`、`！`、`】`、`」` にマッチする。
