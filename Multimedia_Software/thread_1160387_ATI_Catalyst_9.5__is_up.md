---
title: "ATI Catalyst 9.5  is up"
date: 2009-05-15
forum: Multimedia Software
---

### Post by ebucha on 2009-05-15
The 9.5 driver is officially up on the ATI servers.  They have yet to link it on the download page (as of this writing).  Here is the link if anyone is interested: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-5-x86.x86_64.run)

Initial Observations:
1) Xinerama is still borked - I think this is an issue with Xorg and Xinerama at this point
2) Monitor setup in CCC is working better but still not what I would call finished (especially for multi-monitor setups)
3) Using Aticonfig with multi-head still doesn't work very well
4) There are a few graphical anomalies (courser and redraw weirdness)
5) User prompts and dialogs now show up in the middle of a monitor when using a virtual screen for multi-monitor (they used to show up in the center of the virtual screen)
6) Application maximization now works properly by default - maximize to monitor not screen 

Overall I'd say it's a good improvement. Assuming you have a working Xorg.conf this release should only make your system work better.  I used my old Xorg.conf and had no problems getting a dual display setup running with an HD 2600xt.

[B]If you're having problems with the installation check out the fglrx wiki installation guide for Jaunty:
 [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
If you follow this guide you can be sure that all required packages will get installed.
[/B]

---

### Post by pmalvr on 2009-05-16
Can you activate the visual effects? I tried catalyst 9.5 from the link you posted and i was not able to do it? Any suggestion?

Thanks in advance

---

### Post by DangerIsGo on 2009-05-16
Well, unfortunatly, still doesn't work with my 4870x2.  I get the same thing as if I installed with 9.4.  Works on Intrepid, but not Jaunty.

---

### Post by ebucha on 2009-05-16
I'd run fglrxinfo to ensure that the fglrx driver is being used properly.  Assuming the driver is loading properly you should have no problems with compiz, it works fine for me.  If you haven't installed the driver a few times before I'd check the unofficial fglrx wiki installation guide for Jaunty:
**[http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)**

I've used the guide a few times and it works fine.  Just keep in mind that you may need to use a recovery mode root console to complete the update procedure in the guide (since your xorg.conf will be pointing to the uninstalled fglrx driver).

---

### Post by dany74q on 2009-05-17
I hope it will support my 3870x2.
I have this card like a year now,and still,no official support.
My next card would be Nvidia,not doubt.

---

### Post by oldrocker99 on 2009-05-17
I'm stuck with a laptop with an ATI chipset which is no longer suppported past 9.03. And the non-fglrx drivers are 9.04 plus.:mad:

I am seriously considering resurrecting my old single-core A64 3800 which blessedly has a nVidia card.

And I will never, ever buy any machine with ATI graphics again.:mad::mad:

:guitar:

---

### Post by pmalvr on 2009-05-17
I already was able to activate the visual effects... but the problems like the maximizing slow process of windows still exist. Does anyone more noticed the same? Thanks

---

### Post by ebucha on 2009-05-17
I did notice that the window animations are still a little slow.  They seem better to me than 9.4, but still nowhere near what they should be.

---

### Post by csaw on 2009-05-18
> **DangerIsGo said:**
> Well, unfortunatly, still doesn't work with my 4870x2.  I get the same thing as if I installed with 9.4.  Works on Intrepid, but not Jaunty.

Yup, same here. 4870X2 on ubuntu 64-bit behaves exactly as 9.4, i.e. corrupted screen & then hangs

---

### Post by Zero Prime on 2009-05-18
Thank God for this.  An update just borked my video before reading this.  All is better now.

---

### Post by TeleTommy on 2009-05-19
could you guys please tell me the "cleanest" way to install the new driver in my ubuntu 9.04 system?

---

### Post by dany74q on 2009-05-19
No 3870x2 support yet.
Damn!

---

### Post by keypox on 2009-05-19
did it fix the issues wtih 4800s?

---

### Post by kakemann on 2009-05-19
Yeah, still have the same problem with my 4870x2........

---

### Post by clhsharky on 2009-05-19
Thanks for the heads up

   Jaunty 64 ext4, kernel v2.6.29.3, ATI 3650, Cat 9.5.
No problems that I can find, at least not yet.

Sharky

---

### Post by A7llaman on 2009-05-21
Ati Driver 9.5 work fine with HD 4870 on Jaunty :) 

[IMG]http://i40.tinypic.com/16bgin9.jpg[/IMG]

---

### Post by johnjohn2 on 2009-05-21
My ATI card is up for sale and the new Nvidea is working like it bloody should!

---

### Post by keypox on 2009-05-21
> **A7llaman said:**
> Ati Driver 9.5 work fine with HD 4870 on Jaunty :) 




LOL, yes we call can get a clean desktop, but try playing a video, you will get tearing.  Or moving around a cube you will also get tearing.  Lets see you use a 3d app, like google earth, it will not work.  

But it is a improvement and the xorg problems have seemed to go away.

---

### Post by DangerIsGo on 2009-05-21
> **keypox said:**
> LOL, yes we call can get a clean desktop, but try playing a video, you will get tearing.  Or moving around a cube you will also get tearing.  Lets see you use a 3d app, like google earth, it will not work.  

But it is a improvement and the xorg problems have seemed to go away.

Do you have a 4870 or 4870x2?  We know it works with the 4870 but not the 4870x2

---

### Post by dvalphen on 2009-06-12
Catalyst 9.4 is working for 4870X2 under Jaunty, so use that in the meantime. see the wiki at [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)

---

