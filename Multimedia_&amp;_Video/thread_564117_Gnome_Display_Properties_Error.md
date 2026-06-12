---
title: "Gnome Display Properties Error"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by mliving on 2007-09-30
Just installed Ubuntu 7.04 on a spare PC with an ATI Radeon 700X video card.

Downloaded all updates required for the restricted driver manager and have enabled the ATI driver.

But when I go to change my resolution from 1024 x 768 I receive the following ERROR message:

**Error Message**
An error occurred while loading or saving configuration information for gnome-display-properties. Some of your configuration settings may not work properly.

**Under Advanced:**
Bad key or directory name: "/desktop/gnome/screen/(none)/0/resolution": `(' is an invalid character in key/directory names

My display is a BENQ 23" Wide Screen so you can imagine how bad ubuntu looks at 1024!

Any assistance would be greatly appreciated

Thanks

---

### Post by mliving on 2007-09-30
I forced the ATI driver install using:

sudo sh ./ati-driver-installer-8.40.4-x86.x86_64.run
sudo aticonfig --initial --force

I now have the resolutions I need but I still receive the gnome properties error.

Would like to know how to fix it if possible.

Thx

---

