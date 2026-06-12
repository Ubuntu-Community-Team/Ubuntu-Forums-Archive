---
title: "Can't change to 1440x900"
date: 2009-08-25
forum: Multimedia Software
---

### Post by loosemoose on 2009-08-25
We have an HP w1907 Monitor. Unbuntu did not detect it and states its an unknown monitor. It will only allow us to set it to 800x600 but the monitor can go to 1440x900 so I think we need to download a different monitor driver or whatever we need to go up to 1440x900. Can someone tell us what we have to do to get there? Thank you

---

### Post by Wiebelhaus on 2009-08-25
boy , I thought this was resolved....


**YO SON! bring back the displayconfig-gtk!**

j/k 


You'll need to manually configure xorg , [this is not easy]("http://ubuntuforums.org/showthread.php?t=788765") for a new guy.

---

### Post by loosemoose on 2009-08-25
Do not understand the response "I thought this issue was resolved. No it has not been resolved. We just installed Ubuntu yesterday and joined this forum today?

---

### Post by Wiebelhaus on 2009-08-25
> **loosemoose said:**
> Do not understand the response "I thought this issue was resolved. No it has not been resolved. We just installed Ubuntu yesterday and joined this forum today?

*I was referring to the mis-detection* of some LCD's , See mate , two or three revisions ago we had this "[displayconfig-gtk]("http://www.phoronix.com/scan.php?page=article&item=814&num=1")" and it worked fantastic , you could literally after installing your gfx drivers , manually configure your monitor. It was discontinued because the guy that's in charge of this area felt strongly that it caused more problems then it was worth and it was voted out.

*_It was an joke about an old tool that I used religiously. _*

But in any case , you'll need to [manually configure your monitor]("http://ubuntuforums.org/showthread.php?t=83973").

---

### Post by peepingtom on 2009-08-26
Hi, there may be an easier way to solve this problem but we need more information. Could you please go into a terminal and post the results of running ```
lspci |grep VGA
``` Stuff in terminal is CaSE SenSItIve, by the way. If you have trouble copying it, copy in gnome-terminal is shift-ctrl-c , or you can highlight and right click to copy/paste.

When asking for help with video stuff, we need to know what drivers your card runs, things are different between nvidia, ati, intel and others. Best of luck!

---

### Post by Wiebelhaus on 2009-08-26
If you want us to walk you through it , we'll need hardware information and could we assume that you installed your graphic driver via the restricted-manager?

---

