---
title: "ATI X1600 GPU Troubles"
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by sindrum_murdnis on 2006-11-29
Okay just recently i purchased a killer ATI X1600 GPU. The damn thing seems to work just fine with my windows hard drive but wouldn't allow Ubuntu to start or Ubuntu wouldn't let Ubuntu to start. Anyways so me being me reinstalled Ubuntu and it worked . So i spent a few hours setting up Ubuntu, reading setting up reading setting up(you know the deal). After i set it up the thing worked great(by the way i used the ATI drivers that came with Ubuntu), had no problems. Well being satisfied i jumped back over to my windows hard disk to play some games. Well heres were i started banging my head into the wall . I rebooted and started up Ubuntu, only to find out the damn thing doesn't work any more. When Ubuntu is starting up it gets to the part with the scrolling bar. It gets all messy looking and freezes. My system specs are like this

AMD 64 +3000
2.01 ghz
1.00 gig ram
ATI X1600 GPU

Hope theres a fix, thanks

---

### Post by theDentist on 2006-11-29
Am I right in thinking that you are using two hard drives, one with Ubuntu and another with Windows instead of a dual boot from a single drive?  If so you could be confusing the motherboard BIOS somehow. Just a thought.  [-( 
How to fix that, I have no idea.

---

### Post by redwinedrummer on 2006-11-29
Try entering Ubuntu in Recovery Mode via the GRUB menu. Input your root password then install (or reinstall) your fglrx drivers.

I've read some articles about dual-booting Windows and Ubuntu. It's never been flawless and pretty. There will always be some tinkering with files that can possibly make things look bloody. If you are using two different drives, there are safer alternatives to modifying your Windows or Ubuntu boot files. You can either manually set your primary boot hard drive in your BIOS or add a Windows entry to your GRUB menu. The disadvantage with the former is that you have to enter BIOS everytime you switch operating systems. With the other one, you will have to keep on waiting for the GRUB menu, press ESC and select your OS. Either way, I think it's better to go through extra steps than to damage your Master Boot Record or other essential system files, though. 

Hope this helps!

---

