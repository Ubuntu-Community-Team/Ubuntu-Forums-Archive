---
title: "blur windows"
date: 2009-05-08
forum: Multimedia Software
---

### Post by ledererster on 2009-05-08
I am using 9.04 and compiz. I turned on the "blur windows" and now all the windows and menus and everything are just black. sometimes they have weird colored lines through them. How do I reset that option through a terminal? Or is there another way that I can get it back to normal?  Thanks.

---

### Post by Longinus00 on 2009-05-08
> **ledererster said:**
> I am using 9.04 and compiz. I turned on the "blur windows" and now all the windows and menus and everything are just black. sometimes they have weird colored lines through them. How do I reset that option through a terminal? Or is there another way that I can get it back to normal?  Thanks.

Open a terminal and type ```
metacity --replace
```
After that you can re-enable compiz (with the default settings) by going to System->Preferences->Appearance, Clicking on the "Visual Effects" tab and selecting "Normal" or "Extra".

---

