---
title: "Wireless stopped working after graphics card update?"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by Holyaxe on 2009-08-09
I installed Ubuntu 9.04 (32-bit) on my Acer Aspire 5520. I had problems with resolution and wireless, so I first installed ath5k drivers and worked perfectly. Then I installed NVIDIA graphics card drivers, also works... but the wireless stopped working after that. Now I can't get it to work anymore. I even tried recompiling and installing ath5k, didn't do anything. Could somebody help?

Oh, and I don't have access to a wired network, so I have to install everything from my USB stick.

---

### Post by MadHatter21 on 2009-08-09
Ok so are you sure that the update was only for graphics? So what happened to me is that there was a sort of kernel update. After this update i had no wireless. What i had to do is reinstall the drivers and all to get it working. To see if this applies to you:

On boot up hit:
```
esc
```

after hitting escape it will bring you to a menu. In this menu there will be a list of options like 
```
Kernel 2.x.x.x generic
Recovery mode
Kernel 2.x.x.x generic

```
Try booting up off of the second latest version. So if the first one is e.g 2.6.29.30 generic and the second is 2.6.29.29 (one version lower) then go down to the second option and hit enter. 

Do you know what card you have and what driver you are using. I know you are using ath5k but where did you get the driver.

MadHatter21

---

### Post by Holyaxe on 2009-08-09
I managed to solve the problem. I installed madwifi drivers and now it works perfectly. Thanks for the help anyway. :)

This can be closed.

---

