# تركيب GitHub Contribution Graph

## الملفات
- `README.md` — النسخة المحدثة من البروفايل، وفيها الرسم بدل الرابط الوحيد.
- `assets/profile-hero.svg` — الهيدر الموجود من قبل؛ بدون تغيير.
- `.github/workflows/contribution-snake.yml` — Action تنتج صورتين SVG حسب ثيم GitHub.

## التفعيل لأول مرة (مهم)
1. افتح مستودع `youssif-Hy/youssif-Hy` وارفع **ملف الـworkflow أولًا فقط** إلى `.github/workflows/contribution-snake.yml` على فرع `main`.
2. افتح تبويب `Actions`، واختر **Generate GitHub Contribution Graph**.
3. اضغط **Run workflow** ثم **Run workflow** على فرع `main`.
4. تأكد من نجاح التنفيذ (علامة خضراء). سيظهر فرع `output` تلقائيًا ويحتوي:
   - `github-snake-dark.svg`
   - `github-snake-light.svg`
5. **بعد نجاح أول تشغيل فقط** ارفع ملف `README.md` الجديد، ومعه `assets/profile-hero.svg` إن لم يكن موجودًا بالفعل. هكذا لن يظهر رابط صورة مكسورة أثناء التثبيت.
6. ارجع لصفحة البروفايل واعمل Refresh؛ الرسم سيظهر داخل README تلقائيًا بحسب الثيم.

**ملاحظة:** الصورة لن تظهر قبل نجاح أول تشغيل لإنشاء فرع `output`، لأنها ليست ملفًا ثابتًا داخل فرع `main`.

## إذا فشل التشغيل
- لو ظهر `403` أو `Resource not accessible by integration`: راجع `Settings > Actions > General > Workflow permissions`. تأكد من السماح بصلاحيات الكتابة، إذا كانت سياسة المستودع/المؤسسة تسمح بها. الـworkflow نفسه يطلب `contents: write`.
- لو ظهرت صورة مكسورة بعد التشغيل الناجح: افتح فرع `output` وتأكد من وجود الملفات المكتوبة أعلاه؛ تأكد أن المستودع Public وأن الروابط صحيحة.
- أحيانًا صفحة GitHub تتأخر قليلًا في تحديث كاش الصور؛ جرّب تحديثًا قويًا.

## التحديث الدوري
الـworkflow يعمل يوميًا كما يمكن تشغيله يدويًا، باستخدام `Platane/snk/svg-only@v3` لتوليد رسوم مبنية على مساهمات GitHub الفعلية، ثم `crazy-max/ghaction-github-pages@v5` لنشرها في فرع `output` الخاص بك. الـREADME لا تعتمد على خدمة رسومية ديناميكية خارجية عند كل فتح للصفحة؛ الصور الناتجة تُخدَّم من مستودعك.
