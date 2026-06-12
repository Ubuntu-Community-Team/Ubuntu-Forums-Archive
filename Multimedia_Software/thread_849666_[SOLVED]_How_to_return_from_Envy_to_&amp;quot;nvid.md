---
title: "[SOLVED] How to return from Envy to &amp;quot;nvidia&amp;quot; driver from Ubuntu repo"
date: 2008-07-04
forum: Multimedia Software
---

### Post by warmrobot on 2008-07-04
Hello everybody!

Yesterday I tried to install Envy to fix games freezing. The bug still exist, and I've got a new one. You may be khow, that annoying bug, when you hold cursor over buttons, the top of the window glitching and loose its color. [IMG]http://warmrobot.com/i/temp/ubuntu_lose_color.png[/IMG] 

I am pretty sure that on *nvidia-glx-new* does ot have this bug. So I deside to return to *nvidia-glx-new* But xserver do not use my xorg.conf when I uninstall Envy drivers and try to use *nvidia-glx-new*. And even in jockey-gtk I didn't see anything. As my system don't have any proprietary driver at all!

I think "nv" driver doesn't work too. Only VESA with 800x600 max resolution.
Please help me to return things back to default.

My videocard NVIDIA 6600GT
Monitor Dell 2007WFP

Thank you!

---

### Post by ubuntu-freak on 2008-07-04
Did you remove Envy completely with:
 
**sudo envy --uninstall-all**
 
?

---

### Post by warmrobot on 2008-07-05
Yes, I did. Exactly like in manual. May be I must to do some changes in *xorg.conf*? However there Driver "nvidia", and here Driver "nvidia" so what's the differ?

---

### Post by ubuntu-freak on 2008-07-05
What happens when you enable the proprietary driver in System > Administration > Hardware Drivers?
 
Your games may stop freezing if you disable effects in System > Preferences > Appearance > Effects.

---

### Post by warmrobot on 2008-07-05
When I uninstalled Envy drivers,  System > Administration > Hardware Drivers show NO any drivers at all. Before I install Envy everything was correct.

---

### Post by ubuntu-freak on 2008-07-05
> **warmrobot said:**
> When I uninstalled Envy drivers,  System > Administration > Hardware Drivers show NO any drivers at all. Before I install Envy everything was correct.

 
Hmm I'm not sure then. Have you tried installing nvidia-glx-new manually?

---

### Post by warmrobot on 2008-07-06
Yes, I did it by Synaptic. The thing that I found weird is why "nv" does't work too. Only Vesa. And why System > Administration > Hardware Drivers is empty.

---

### Post by TVC15 on 2008-07-06
Hello,

I am experiencing a similar problem.
I can't get the Extra Visual Effects activated.  So I tried using Envyng, following the manual.
I think that installed a newer driver than the one I had, because I now have a problem I didn't have before.  My second display is out of sync because of an impossible refresh rate.  When I try to adjust it in "Screen and graphics", I am forced back to Vesa drivers, but they only give me 800x600 resolution.
Before I ran Envy, my secondary display was ok.

Now I still can't activate the Extra visual effects AND my second display doesn't work anymore

I am running Ubuntu 8.04 with Nvidia 7800GS 512MB AGP card.

---

### Post by warmrobot on 2008-07-07
By the way, I have found that problem with window titlebar is connected with new NVidia drivers and Compiz. So I surely need to get standard "nvidia" driver, not Envy.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/99508")

---

### Post by warmrobot on 2008-07-10
OK, finally I got "nvidia" driver. This [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") manual was very helpful.

All that I did is:

1) sudo depmod

2) Added following line to *Screen* section in *xorg.xonf*. 
```
Option "UseDisplayDevice" "DFP" 
```

And after starting X server everything is fine. Problem is solved.

---

### Post by ubuntu-freak on 2008-07-10
I'm glad you got it sorted. Strange you had to do that though.

---

