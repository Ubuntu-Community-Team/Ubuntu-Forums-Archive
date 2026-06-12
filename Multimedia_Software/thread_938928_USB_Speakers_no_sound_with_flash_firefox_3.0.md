---
title: "USB Speakers no sound with flash firefox 3.0"
date: 2008-10-05
forum: Multimedia Software
---

### Post by mnj1979 on 2008-10-05
Hello,
  I am trying to get sound to my usb speakers from flash firefox but it is not working. I tried asoundconf set-default-card Device but it didnt work.
Can you please help me find out how to get flash to recognize my usb speakers?
Thank you,
Mark

---

### Post by coolbrook on 2008-10-05
Is libflashsupport installed?  If not then close your browser.

```
sudo apt-get install libflashsupport
```

Try again.

---

