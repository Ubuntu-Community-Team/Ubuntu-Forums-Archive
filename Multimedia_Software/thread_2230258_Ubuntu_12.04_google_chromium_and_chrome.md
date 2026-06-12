---
title: "Ubuntu 12.04 google chromium and chrome"
date: 2014-06-18
forum: Multimedia Software
---

### Post by deerhunter0210 on 2014-06-18
I'm using chromium on 12.04. There seems to be an issue with the flash, some images and videos are coming up as distorted red and green colours. They just look terrible. Has anyone else seen this, it does the same on chrome, 
Please if someone could help, that would be great

---

### Post by ajgreeny on 2014-06-18
Sounds like an old bug to do with graphics acceleration in flash, though I thought that had long been overcome.

Try turning off hardware acceleration in flash by right-clicking in a flash window and choosing settings.
See [https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/967091)
and
[http://ubuntuforums.org/showthread.php?t=1977105](http://ubuntuforums.org/showthread.php?t=1977105)

What hardware are you using?

---

### Post by deerhunter0210 on 2014-06-18
I tried turning off acceleration but with the image or video being distorted it won't allow me to edit the settings, is there another way of turning it off. Graphics is intel 865Gx86/MMX/SSE2

---

### Post by slickymaster on 2014-06-18
> **deerhunter0210 said:**
> I tried turning off acceleration but with the image or video being distorted it won't allow me to edit the settings, is there another way of turning it off. Graphics is intel 865Gx86/MMX/SSE2


[LIST=1]
[*]Open the **about:flags** in your address bar
[*]Look for [B]Override software redendering list
[/B]
[*]Click '**Enable**' and the value will change to 'Disable'
[*]Restart Chrome/ium
[/LIST]

---

### Post by deerhunter0210 on 2014-06-18
tried that, still the same, dont know how to add a screenshot to this post

---

### Post by deerhunter0210 on 2014-06-18
is it something with 12.04, if i upgrade to 12.10 would that solve anything???

---

### Post by monkeybrain20122 on 2014-06-18
This may help [http://sepirothemgnu.wordpress.com/2013/12/11/corregir-problemas-con-video-intel/](http://sepirothemgnu.wordpress.com/2013/12/11/corregir-problemas-con-video-intel/)

BTW, 12.10 has reached end of life so that would not work. You can try with Ubuntu 14.04 but test it out on a live usb first. And don't "upgrade", backup the data and do a fresh install if you are satisfied with the life session.

---

