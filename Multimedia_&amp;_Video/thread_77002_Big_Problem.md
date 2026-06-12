---
title: "Big Problem"
date: 2005-10-16
forum: Multimedia &amp; Video
---

### Post by ojpd on 2005-10-16
Well, I hope somebody can get a clear picture of what my problem is, so here it goes.. 

I really dont know what is causing the problem but my suspects are either it is my video card or my monitor. I have an Nvidia geforce2 MX400 with 64mb of ram, and a DTS Monitor but it comes out as Generic of course.. The problem is everytime I boot up, as in just when i power up the pc, when it conducts memory tests and other booting stuff my screen resolution messes up as in the PIN CUSHION setting of my monitor automatically sets itself into 80 where it was and always was supposed to be only set to 50 and despite of all the adjustments and stuff it still goes to 80 everytime I boot up. All I know is this only happened after I installed Ubuntu 5.10.. and even if I tried reinstalling both Ubuntu and XP (dual boot).. It still behaves this way. I never experienced this with Hoary but now that I have breezy this problem occurs not only when I boot into my Ubuntu installation but also started causing with my XP installation. This happened when I tried to reconfigure X on my ubuntu setup because it wasnt able to detect my video card at first. Now I really dont know what to do since after reinstalling ubuntu more than 5 times it finally detected my supposed to be normal resolution... is this something that was caused by reconfiguring X on ubuntu because i NEVER had this problem before. Now despite of several attempts to reformat everything the problem with the Pin Cushion setting occurs everytime I boot up. 

PS: Would flashing the BIOS help resolve this problem? PLEASE ANYBODY!! HELP!!!

---

### Post by ojpd on 2006-01-20
[QUOTE=ojpd]Well, I hope somebody can get a clear picture of what my problem is, so here it goes.. 

I really dont know what is causing the problem but my suspects are either it is my video card or my monitor. I have an Nvidia geforce2 MX400 with 64mb of ram, and a DTS Monitor but it comes out as Generic of course.. The problem is everytime I boot up, as in just when i power up the pc, when it conducts memory tests and other booting stuff my screen resolution messes up as in the PIN CUSHION setting of my monitor automatically sets itself into 80 where it was and always was supposed to be only set to 50 and despite of all the adjustments and stuff it still goes to 80 everytime I boot up. All I know is this only happened after I installed Ubuntu 5.10.. and even if I tried reinstalling both Ubuntu and XP (dual boot).. It still behaves this way. I never experienced this with Hoary but now that I have breezy this problem occurs not only when I boot into my Ubuntu installation but also started causing with my XP installation. This happened when I tried to reconfigure X on my ubuntu setup because it wasnt able to detect my video card at first. Now I really dont know what to do since after reinstalling ubuntu more than 5 times it finally detected my supposed to be normal resolution... is this something that was caused by reconfiguring X on ubuntu because i NEVER had this problem before. Now despite of several attempts to reformat everything the problem with the Pin Cushion setting occurs everytime I boot up. 

PS: Would flashing the BIOS help resolve this problem? PLEASE ANYBODY!! HELP!!![/QUOTE]


I still have this problem even though I already bought a new Video Card.. What did ubuntu do to my beast... huhuhuhu any experts out there. Please HELP!! :confused:

---

### Post by gitfiddler on 2006-01-20
ojpd, I might be able to help, but I'm not sure I understand your problem completely. The pincushion setting on your monitor seems to change, so that the image is distorted. Does it seem to straighten out by the time the login screen is displayed? Or do you have to manually reset it every time you boot up? If it is the former, your solution may be a simple setting on your monitor's menu. Please let me know.

---

### Post by wrtrdood on 2006-01-20
If it's still happening with a different video card then it sounds like the monitor may have a problem and it could well be hardware related.  Probably the NVR.  I'd try unplugging the monitor and letting it sit for a while (15 mins or so) to see if it has some sort of setting that's not getting cleared.  Sometimes this can help.  You might also try selecting the Reset or Default setting that most modern monitors have to see if it will clear up.

---

### Post by ojpd on 2006-03-12
[QUOTE=gitfiddler]ojpd, I might be able to help, but I'm not sure I understand your problem completely. The pincushion setting on your monitor seems to change, so that the image is distorted. Does it seem to straighten out by the time the login screen is displayed? Or do you have to manually reset it every time you boot up? If it is the former, your solution may be a simple setting on your monitor's menu. Please let me know.[/QUOTE]

Oh my god, Im so sorry I wasnt able to check back here but yes this is exactly the problem. It straightens out by the time the login screen is displayed. Funny coz I never had this problem before I installed ubuntu. Please please please if you can help me out with this big problem. Im just living with it everyday now coz i dont seem to find a solution to this anywhere. Im just wondering, if it is hardware related why did it just start when I installed ubuntu?

---

### Post by gitfiddler on 2006-03-20
[QUOTE=ojpd]Oh my god, Im so sorry I wasnt able to check back here but yes this is exactly the problem. It straightens out by the time the login screen is displayed. Funny coz I never had this problem before I installed ubuntu. Please please please if you can help me out with this big problem. Im just living with it everyday now coz i dont seem to find a solution to this anywhere. Im just wondering, if it is hardware related why did it just start when I installed ubuntu?[/QUOTE]
Sorry that I didn't get back to you sooner.

Since you've replaced your video card, you've probably figure out by now that the problem resides in the monitor, but it should be easy to fix.

Your monitor stores seperate screen geometry settings (height, width, centering, *pincusion* etc) for _every resolution that it is capable of displaying_. Your computer starts up in one resolution (maybe 640x480) and during the boot process switches to another. There's no problem with the higher resolution, just the lower one. Changing the screen settings after Ubuntu has booted will do no good.

If the problem is there when the Grub screen is displayed, you need to get the computer to pause there, maybe by using the cursor keys to stop the timer that chooses your default OS.  If you can't get it to pause there, try pressing the "Pause" key before the Grub menu is displayed. Then you should be able to go into the monitors menu and correct the pincushion adjustments.

I think it's just a coincidence that this happened when you installed Breezy. I've seen these setting change during a power outage, or sometimes for no reason at all.

I hope this helps.

---

