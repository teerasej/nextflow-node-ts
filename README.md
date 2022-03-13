
# ติดตั้ง TypeScript ใน Node Project ง่ายๆ 

## 1. Setup TypeScript in node project

1. สร้างโฟลเดอร์โปรเจค **nextlfow-node-ts**
2. รันทำคำสั่ง `npm init` เพื่อสร้างไฟล์ **package.json**
3. รันคำสั่งติดตั้ง typescript package 

```bash
npm install --save-dev typescript
```

4. สร้างไฟล์ **tsconfig.json** ไว้ในโฟลเดอร์โปรเจค และกำหนดการตั้งค่าตามด้านล่าง

```json
{
  "compilerOptions": {
    "module": "commonjs",
    "esModuleInterop": true,
    "target": "es6",
    "moduleResolution": "node",
    "sourceMap": true,
    "outDir": "dist"
  },
  "lib": ["es2015"]
}
```

5. เพิ่มและแก้ไขรายละเอียดในไฟล์ package.json 

```json
{
  ...
  "main": "dist/app.js",
  "scripts": {
    "start": "tsc && node dist/app.js",
    ...
  },
  ...
}
```

6. สร้างไฟล์ **app.ts** และเขียนโค้ดตามด้านล่าง

```ts
const username:string = 'Nextflow';
console.log(`Hello ${username}`);
```

7. ทดสอบโปรเจคโดยรันคำสั่งใน terminal 

```bash
npm start
```

## ใช้งาน Express แบบ TypeScript

1. ติดตั้ง `express` และ `@types/express` เพื่อให้มี profile ในการใช้งานและอ้างอิง type ได้

```bash
npm install express
npm install -save-dev @types/express
```

- package บางตัวจะมีการใส่ type มาใน package เลย ไม่ต้องติดตั้งแยก ควรศึกษาคู่มือแนะนำการใช้งาน package นั้นๆ ในการใช้งาน typescript

2. เขียนใช้งาน Express

เขียนใช้งาน Express ในไฟล์ `app.ts` 

```ts
import express, { Request, Response } from 'express'    

const app = express()

app.get('/', (req:Request, res:Response) => {
    res.send('Hello World!')
})

app.listen(3000, () => {
    console.log('Example app listening on port http://localhost:3000')
})
```
3. ทดสอบการทำงานโดยรันคำสั่ง `npm start` อีกครั้ง