---
title: "Boot hang after adding ATI 3650"
date: 2009-07-27
forum: Multimedia Software
---

### Post by Drone022 on 2009-07-27
Hey peoples,

I was running Ubuntu 8.10 for a while without a graphics card, my old one snuffed it but Ubuntu seemed to handle it pretty well and worked fine with my motherboard's on-board graphics which I believe was ATI (my old graphics card was NVidia).

I just got given and ATI 3650, plugged it in booted into Windows installed the drivers and it was all good (set it up even though I havent used Windows for about 3 months).

Then restarted and booted up ubuntu but it froze at the ubuntu loading/splash screen. I then did the recovery boot, it seemed to hang for about 2-3 mins then took me to the menu where I was going to go for the xfix option (I had to do this with my NVidia card also) but my keyboard wouldnt work at all.

So in normal boot it just freezes and in recovery it eventually reaches the menu but I cant choose any of the options, I cant drop to a console or anything.

Anyone got any ideas?

[I might remove the card, pull all my stuff off Ubuntu and then re-install from scratch, I'd rather not though]

Thanks!

---

### Post by cozmicharlie on 2009-07-27
> **Drone022 said:**
> Hey peoples,

I was running Ubuntu 8.10 for a while without a graphics card, my old one snuffed it but Ubuntu seemed to handle it pretty well and worked fine with my motherboard's on-board graphics which I believe was ATI (my old graphics card was NVidia).

I just got given and ATI 3650, plugged it in booted into Windows installed the drivers and it was all good (set it up even though I havent used Windows for about 3 months).

Then restarted and booted up ubuntu but it froze at the ubuntu loading/splash screen. I then did the recovery boot, it seemed to hang for about 2-3 mins then took me to the menu where I was going to go for the xfix option (I had to do this with my NVidia card also) but my keyboard wouldnt work at all.

So in normal boot it just freezes and in recovery it eventually reaches the menu but I cant choose any of the options, I cant drop to a console or anything.

Anyone got any ideas?

[I might remove the card, pull all my stuff off Ubuntu and then re-install from scratch, I'd rather not though]

Thanks!

It may be that you have conflicts with the old NVIDIA drivers.  If you have an embedded card you may want to pull out the video card and see if it boots using the on-board video card.  If it lets you boot you can then remove the NVIDIA drivers and go back to the VESA driver then format it for your ATI card (load the drivers).

---

### Post by Drone022 on 2009-07-28
Hey thanks for the suggestion, I'll try removing the drivers and then I'll see how it goes.

Much appreciated.

---

### Post by Drone022 on 2009-09-15
Oddly, my computer would boot but it would take 4-5 minutes. I also noticed my usb ports wern't working properly.

I then replaced my wireless usb dongle with a proper PCI wireless NIC and now everything boots normally. Now that I have no usb devices plugged in at boot.

Seems my ATI card and belkin usb dongle didnt like each other.

Wierd.

Gonna try other usb devices now and see if they work ok.

---

### Post by markbuntu on 2009-09-16
That sounds like an IRQ conflict.

---

### Post by Drone022 on 2009-09-17
Thanks, I'll look into that. I had a wireless usb dongle plus a usb keyboard and mouse, all of which I have replaced with non usb alternatives (I shouldve got a PCI NIC ages ago anyway).

---

