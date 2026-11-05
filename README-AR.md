# House Design — تحويل البرنامج لتطبيق أندرويد

## اللي محتاجه على الكمبيوتر (مرة واحدة)
1. **Node.js** (نسخة LTS، 20 أو أحدث): https://nodejs.org
2. **Android Studio**: https://developer.android.com/studio (بيثبّت معاه الـSDK والـJava).

## الخطوات (من Terminal / CMD جوه فولدر المشروع ده)
```
npm install
npx cap add android
npm run icons
npx cap sync android
npx cap open android
```
- `npm run icons` بيولّد أيقونة التطبيق وشاشة الفتح من فولدر `assets/`.
- بعد ما يفتح Android Studio: استنى لحد ما يخلّص "Gradle sync" (أول مرة بياخد وقت).

## عمل ملف APK
من Android Studio: **Build ← Build Bundle(s) / APK(s) ← Build APK(s)**.
بعد ما يخلّص اضغط **locate** وهتلاقي `app-debug.apk`. ابعته لتلفونك (واتساب / كابل / Drive) وافتحه، ووافق على "التثبيت من مصدر غير معروف".

**أو** وصّل التلفون بكابل وفعّل "خيارات المطور ← تصحيح USB"، واضغط ▶ Run في Android Studio.

## تحديث التطبيق بعد أي تعديل
1. استبدل `www/index.html` بالنسخة الجديدة من البرنامج.
2. `npx cap sync android`
3. ابنِ APK تاني، وثبّته فوق القديم (بياناتك بتفضل، طالما نفس الـappId وبنفس طريقة التوقيع).

## مهم قبل ما تنقل
- **خد نسخة احتياطية** من البرنامج الحالي (الإعدادات ← تنزيل نسخة احتياطية). تطبيق الأندرويد بيخزّن بياناته منفصلة، فاستعدها فيه من (الإعدادات ← استعادة نسخة احتياطية).
- احتفظ برابط السكريبت والرمز السري عشان إيميل النسخ الاحتياطي.
- ملف الـAPK الـdebug مناسب لاستخدامك الشخصي. للنشر على Google Play بتحتاج ملف AAB موقّع (Build ← Generate Signed Bundle).

## الفولدرات
- `www/` : البرنامج نفسه (index.html + manifest + أيقونات).
- `assets/` : مصادر الأيقونة وشاشة الفتح.
- `capacitor.config.json` : اسم التطبيق (`House Design`) ومعرّفه (`com.housedesign.accounts`).
