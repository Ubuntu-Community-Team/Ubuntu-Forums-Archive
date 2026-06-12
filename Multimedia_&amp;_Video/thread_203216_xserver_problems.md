---
title: "xserver problems"
date: 2006-06-24
forum: Multimedia &amp; Video
---

### Post by BToKiLL on 2006-06-24
Hi!
When i try to load the kubuntu cd, all seems to be fine, but at the end,no image, on screen.

I have a amd 3000+,mobo k8nxp-sli, and a gigabyte 6600 3d1.

Please help

---

### Post by Winblowz on 2006-06-25
I'd first try booting the live-cd in safe mode. If that doesn't work, then it sounds like it could have been a bad burn. 

How fast did you burn the iso image? I wouldn't burn it any faster than 4x.

---

### Post by BToKiLL on 2006-06-25
thx, for the hlep, but, i have boot the same cd in other pc, and everithing it´s ok. i think the problem maybe the vga, or something else. Do no what to do!!! :(

---

### Post by pjman on 2007-07-02
:p:p:p:p:p:p

Sorry for my enthusiasm but I'm glad I'm not alone with this :wink:

Take a look at [my thread]("http://ubuntuforums.org/showthread.php?t=465064") for a work-around on this issue.

Basically, the Ubuntu LiveCD is having a hard time choosing the correct bus identifier for the card. 

Someone on #ubuntu (sorry, I forgot who) told me that's it's unlikely to be fixed since the programming it too difficult for the LiveCD to detect which GPU to use on the card and a human interactive selection would have to be made on LiveCD bootup. I'm paraphrasing here.

One thing I don't get is why does the Knoppix LiveCD work fine with the GV-3D1 and not the Ubuntu LiveCD?

As stated in my thread, I've submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/119114") but I don't know what else the developers need to get it to work. Maybe the Knoppix devs can help?? ](*,)

---

