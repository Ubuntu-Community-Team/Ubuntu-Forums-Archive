---
title: "PepperFlash on Google Chrome"
date: 2012-06-29
forum: Multimedia Software
---

### Post by lovinglinux on 2012-06-29
Google has released version 11.3.31.109 of PepperFlash, which will be the only actively supported version of Flash for Linux. Other browsers are still and will remain using the regular NPAPI Flash 11.2, that will only receive security updates for 5 years.

[http://www.muktware.com/3778/chrome-20-google-takes-over-adobe-flash-linux-development](http://www.muktware.com/3778/chrome-20-google-takes-over-adobe-flash-linux-development)

If you are using Chrome, just update it to version 20.0.1132.47 using the update manager to get the new PepperFlash. It seems PepperFlash is selected by default, but to make sure it is used by Chrome, you can disable the NPAPI flash in the chrome://plugins/ page. If you don't use other browser or application that depends on flash, you can even remove flashplugin package entirely.

I don't think PepperFlash will be shipped with Chromium, as it is not open source.

Performance of the new plugin is good, but I am experiencing issues with fullscreen, which doesn't get focus when activated.

---

### Post by vasa1 on 2012-06-29
> **lovinglinux said:**
> Google has released version 11.3.31.109 of PepperFlash, ...

Some people are having problems that are being attributed to the newer Flash:
[https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)
[http://code.google.com/p/chromium/issues/detail?id=128870](http://code.google.com/p/chromium/issues/detail?id=128870)
[http://ubuntuforums.org/showthread.php?t=2011882](http://ubuntuforums.org/showthread.php?t=2011882)

---

### Post by lovinglinux on 2012-06-30
> **vasa1 said:**
> Some people are having problems that are being attributed to the newer Flash:
[https://code.google.com/p/chromium/issues/detail?id=134940](https://code.google.com/p/chromium/issues/detail?id=134940)
[http://code.google.com/p/chromium/issues/detail?id=128870](http://code.google.com/p/chromium/issues/detail?id=128870)
[http://ubuntuforums.org/showthread.php?t=2011882](http://ubuntuforums.org/showthread.php?t=2011882)

Thanks for the warning and links. I have posted a suggestion there, since I am not experiencing any issues:

[http://ubuntuforums.org/showthread.php?p=12065543#post12065543](http://ubuntuforums.org/showthread.php?p=12065543#post12065543)

---

### Post by jejones3141 on 2012-07-04
I am definitely having problems. I hate to have to admit to playing any Zynga games, but--since installing Version 20.0.1132.47 of Chrome, they almost always crash.

---

