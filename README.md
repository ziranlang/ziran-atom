# language-ziran

Ziran (`.zi`) syntax highlighting for the [Atom](https://atom-editor.cc/)
editor, ported from the [ziran-vscode](https://github.com/ziranlang/ziran-vscode)
extension (version 0.6.3).

- `grammars/ziran.json` is the extension's `syntaxes/ziran.tmLanguage.json`
  with Atom's `fileTypes` added. The scope name is the same, `source.ziran`,
  so any syntax theme colours it the way it colours VS Code's tokens:
  directives (`#import`, `#foreign`, ...), line and block comments, strings,
  declarations (`Name :: (...)` as functions, `Name :: value` as constants),
  scalar types, `struct`/`enum`, capitalised type names, numbers, keywords
  and operators.
- `settings/language-ziran.cson` carries the editor rules from
  `language-configuration.json`: `//` line comments (Ctrl+/) and brace-based
  auto-indent. Bracket and quote auto-closing is Atom's default
  `bracket-matcher` behaviour.

The extension's other features (`ziran check` diagnostics, the Run pane, the
`.zir` viewer, Kryon preview) are VS Code extension code and are not part of
this package.

## Install

Clone this repository into Atom's packages folder, then reload Atom
(Ctrl+Shift+F5) or restart it:

```sh
git clone https://github.com/ziranlang/ziran-atom ~/.atom/packages/language-ziran
```

On Windows the packages folder is `%USERPROFILE%\.atom\packages`. `.zi` files
then open with the Ziran grammar; it is also selectable from the grammar
picker (Ctrl+Shift+L) as "Ziran".

## Keeping the grammar in sync

When ziran-vscode changes `syntaxes/ziran.tmLanguage.json`, copy it over
`grammars/ziran.json` and re-add the `"fileTypes": ["zi"]` entry. The upstream
grammar tests (`tests/grammar.test.mjs` in ziran-vscode, run with
`vscode-textmate` and `vscode-oniguruma`) pass unchanged against this copy;
Atom's TextMate engine uses the same Oniguruma regex library.

## License

MIT, like ziran-vscode. See [LICENSE](LICENSE).
