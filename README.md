# Dashboard ยอดปล่อยสินเชื่อ

Dashboard ผลการดำเนินงานปล่อยสินเชื่อ (สินเชื่อทั่วไป ยกเว้นปุ๋ย และสินเชื่อปุ๋ย) แยกภาค / พื้นที่ / เดือน
เป็นไฟล์ HTML ไฟล์เดียว ไม่ต้องมี server ไม่ต้อง build

## วิธีใช้
1. เปิดหน้าเว็บ แล้วกด **อัปโหลดไฟล์ข้อมูลใหม่** (หรือลากไฟล์ .xlsx มาวาง)
2. เลือกเดือน / ภาค / ประเภทสินเชื่อ / ธีม
3. กด **ดาวน์โหลด Excel / PowerPoint / PDF**

ไฟล์ข้อมูลถูกประมวลผลในเบราว์เซอร์ของผู้ใช้เท่านั้น ไม่ถูกส่งขึ้น server
ข้อมูลล่าสุดถูกจำไว้ในเบราว์เซอร์นั้น (localStorage) กด **ล้างข้อมูล** เพื่อลบ

### คอลัมน์ที่ต้องมีในไฟล์ Excel
เดือน, ภาค, เขต, กลุ่ม, พื้นที่, เป้าหมายสินเชื่อ(ประเภทอื่นๆ ยกเว้นสินเชื่อปุ๋ย), สาขาทำได้ยกเว้นสินเชื่อปุ๋ย,
เป้าหมายสินเชื่อปุ๋ย, สาขาทำได้สินเชื่อปุ๋ย, NPL (ถ้ามี) — ปี พ.ศ. อ่านจากชื่อไฟล์ เช่น `ยอดปล่อย_2569.xlsx`

## Deploy ด้วย GitHub Pages
1. สร้าง repository ใหม่บน GitHub (แนะนำให้ตั้งเป็น Private ถ้าใช้ภายในองค์กร — หมายเหตุ: Pages ของ repo private ต้องใช้แพ็กเกจที่รองรับ)
2. อัปโหลดไฟล์ `index.html`, `README.md`, `.nojekyll` ไปที่ branch `main`
   (หน้า repo → **Add file → Upload files** หรือใช้ `git push`)
3. ไปที่ **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main` / `/ (root)` → **Save**
4. รอ 1–2 นาที จะได้ลิงก์ `https://<ชื่อผู้ใช้>.github.io/<ชื่อ repo>/`

### ด้วยคำสั่ง git
```bash
git init
git add index.html README.md .nojekyll
git commit -m "Loan dashboard"
git branch -M main
git remote add origin https://github.com/<ชื่อผู้ใช้>/<ชื่อ repo>.git
git push -u origin main
```

## ข้อควรระวัง
- **อย่า commit ไฟล์ข้อมูลจริง (.xlsx)** ขึ้น repo สาธารณะ — หน้าเว็บไม่ต้องใช้ ผู้ใช้อัปโหลดเองตอนเปิด
- หน้าเว็บโหลดไลบรารีจาก cdnjs.cloudflare.com (Chart.js, SheetJS, PptxGenJS, html2canvas, jsPDF) และฟอนต์จาก Google Fonts จึงต้องต่ออินเทอร์เน็ต
