# 判断系ルーブリック項目は人間 Gold で較正した LLM ジャッジで評価する

ルーブリックの B群（atomicity・self-contained・own-words 等、Andy 自身が「決定的な litmus は無い」と認める判断項目）も binary gate に含める。自動テスト（Gold 評価）ではこれらを LLM ジャッジに y/n 判定させるが、ジャッジは Gold セット上で人間の y/n との一致率を測定し、閾値（例：Cohen's κ > 0.8）を超えたときのみ信用する。

理由：B群を gate から外すと atomicity・self-contained という evergreen の核を強制できず、「ルールは通るが中身は悪いノート」を通してしまう。一方、無較正の LLM ジャッジは「LLM が LLM の手抜きを判定する」構図で信頼できない。較正によって後者を防ぎつつ前者を守る。

帰結：Gold データには、B群各項目について**人間の y/n ラベル（較正セット）**を含める必要がある。
