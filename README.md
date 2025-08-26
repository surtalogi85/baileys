# <div align='center'>@Surtalogi85/Baileys</div>

<div align="center">

  <img src="https://raw.githubusercontent.com/surtalogi85/baileys/refs/heads/master/lib/Skirk.jpeg" />

  <a href="https://github.com/surtalogi85/baileys">
    <img src="https://img.shields.io/badge/GitHub-Repository-181717?logo=github&logoColor=white" alt="GitHub Repository" />
  </a>

  <a href="https://whatsapp.com/channel/0029VaEe0l9Au3aVRw2x2r0V">
    <img src="https://img.shields.io/badge/WhatsApp-Channel-25D366?logo=whatsapp&logoColor=white" alt="WhatsApp Channel" />
  </a>

</div>

## 📖 目次

- [重要なお知らせ](#重要なお知らせ)
- [インストール](#インストール)
- [追加機能と改善点](#-追加機能と改善点)
- [機能例](#機能例)
  - [ニュースレター管理](#ニュースレター管理)
  - [ボタンとインタラクティブメッセージ管理](#ボタンとインタラクティブメッセージ管理)
  - [AIメッセージアイコンのカスタマイズ](#aiメッセージアイコンのカスタマイズ)
  - [カスタムペアリングコード生成](#カスタムペアリングコード生成)
- [問題報告](#問題報告)
- [注意](#注意)
---

## 重要なお知らせ

このリポジトリは、元の作成者が削除した後、[WhiskeySockets](https://github.com/WhiskeySockets) に引き継がれました。その基盤の上で、いくつかの新機能や改善を加え、より強力で使いやすい機能を提供しています。

## インストール

`package.json` に追加:

```json
"dependencies": {
    "@surtalogi85/baileys": "github:surtalogi85/baileys"
}
````

またはターミナルで:

```bash
npm install github:surtalogi85/baileys
```

コード内で呼び出す方法:

```ts
// ESM タイプ
import makeWASocket from '@surtalogi85/baileys'
```

```js
// CJS タイプ
const { default: makeWASocket } = require("@surtalogi85/baileys")
```

## 追加機能と改善点

| 機能                         | 説明                                                          |
| :------------------------- | :---------------------------------------------------------- |
| 💬 **チャンネルへのメッセージ送信**      | テキストやメディアメッセージをチャンネルに送信可能。                                  |
| 🔘 **ボタン & インタラクティブメッセージ** | WhatsApp MessengerやWhatsApp Businessでボタンやインタラクティブメッセージ送信可能。 |
| 🤖 **AIメッセージアイコン**         | メッセージの表示にAIアイコンを追加してモダンな外観を提供。                              |
| 🖼️ **フルサイズのプロフィール画像**     | プロフィール画像を切り抜かずにオリジナルサイズでアップロード可能。                           |
| 🔑 **カスタムペアリングコード**        | 任意のペアリングコードを生成・設定可能。                                        |
| 🛠️ **Libsignalの修正**       | Libsignalのログを整理し、開発時の出力をより見やすく改善。                           |

## 機能例

### ニュースレター管理

```ts
// ニュースレター情報取得
const metadata = await sock.newsletterMetadata("invite", "xxxxx")
console.log(metadata)

// ニュースレター作成
const metadata2 = await sock.newsletterCreate("ニュースレター名", "説明文")
console.log(metadata2)
```

### ボタンとインタラクティブメッセージ管理

```ts
// ボタンメッセージ送信例
const buttons = [
  { buttonId: 'id1', buttonText: { displayText: 'ボタン1' }, type: 1 },
  { buttonId: 'id2', buttonText: { displayText: 'ボタン2' }, type: 1 }
]

const buttonMessage = {
    text: "こんにちは、ボタンメッセージです",
    footer: 'Footer',
    buttons,
    headerType: 1
}

await sock.sendMessage(id, buttonMessage, { quoted: null })
```

### AIメッセージアイコンのカスタマイズ

```ts
await sock.sendMessage(id, { text: "こんにちは", ai: true })
```

### カスタムペアリングコード生成

```ts
if(usePairingCode && !sock.authState.creds.registered) {
    const phoneNumber = await question('携帯番号を入力してください:\n');
    const code = await sock.requestPairingCode(phoneNumber);
    console.log(`ペアリングコード: ${code?.match(/.{1,4}/g)?.join('-') || code}`);
}
```

## 問題報告

問題が発生した場合は [GitHub Issues](https://github.com/surtalogi85/baileys/issues) に報告してください。

## 注意

上記の変更以外は元のリポジトリの機能と同じです。元のリポジトリは [WhiskeySockets](https://github.com/WhiskeySockets/Baileys) を参照してください。
