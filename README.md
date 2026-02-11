# Python
Logs on working with and studying Python

# with文（コンテキストマネージャ）
with 文は内部的に try...finally と同等のクリーンアップ処理（終了時に必ずファイルを閉じる等）を自動で行ってくれるため、基本的には finally で手動クリーンアップを書く必要がない  
try...withには下記のメリットがある：
- **確実なクローズ**: `with`文を使うとブロックを抜ける斉木に正常終了、例外発生問わず、自動で`__exit__`メソッドが呼ばれ、ファイルが閉じてリソースが解放される。
- **定型処理の省略**: `try...finally...close()`で記述していたfinallyブロックが不要になる。
- **例外処理の併用**: `with`の前後に`try-except`を配置すると、ファイルを開く動作、開いた後のファイル操作のエラー処理を記述・実行可能。
``` python
try:
    with open("data.txt", "r") as f:
        content = f.read()
        # 読み込み中のエラーもここでキャッチできる
except FileNotFoundError:
    print("ファイルが見つかりません。")
except Exception as e:
    print(f"予期せぬエラー: {e}")
```
