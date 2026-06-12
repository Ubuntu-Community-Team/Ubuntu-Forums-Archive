---
title: "IVTV drivers problem with Kernel 2.6.20-15"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by SadaraX on 2007-08-06
I just installed MythTV in Ubuntu Feisty (kernel 2.6.20-15-generic). I am using a PVR-150 Hauppauge. There is just ***one problem***. 

I cannot get the card to recognize channels above 13. Scanning for channels does not work, since it stops at 13, and even manually going higher just gives me static and noise and no picture. All channels from 2 to 13 work just fine. 

I tested the hardware by swapping into my old computer with its installation of KnoppMyth, and the hardware works just fine. I have installed Ubuntu on that machine to test, and the channel bug returned, so I am fairly certain it is a difference in software and kernel with Ubuntu.

While looking through various packages for the IVTV drivers, I found that it seems the drivers for MythTV in Ubuntu are out of date and do not work for the current Ubuntu kerne. This is according to the developers statements on [ivtvdriver.org]("ivtvdriver.org").

Does anyone have a solution for using MythTV with PVR-150/250/350 on Ubuntu? I really want this to work in Ubuntu.

---

### Post by Krikke_wl on 2007-08-08
Why don't you update your machine? I got feisty with the 2.6.20-16 kernel and a Hauppauge PVR-500 running smooth...

Regards,
Krikke

---

### Post by SadaraX on 2007-08-08
> **Krikke_wl said:**
> Why don't you update your machine? I got feisty with the 2.6.20-16 kernel and a Hauppauge PVR-500 running smooth...

Regards,
Krikke

I tried doing that, but my PVR-150 never worked properly. I do not know what the problem is. For a while I thought the issue was the IVTV kernel module, which according to the ivtvdriver.org website is not correct for the Ubuntu/Debian kernel version. Yet that same driver works under KnoppMyth. I am not sure what the problem is.

---

### Post by Krikke_wl on 2007-08-09
Well for a while I had a PVR-150, which I borrowed from a friend. In my pc I had no problem at all, but he had jitter on his image, with the same card. The rest of his setup was identical to mine... 
So maybe there isn't really a solution for your problem, sorry.

Regards

---

### Post by SadaraX on 2007-08-09
> **Krikke_wl said:**
> Well for a while I had a PVR-150, which I borrowed from a friend. In my pc I had no problem at all, but he had jitter on his image, with the same card. The rest of his setup was identical to mine... 
So maybe there isn't really a solution for your problem, sorry.

Regards

While I do not have a solution for using either Ubuntu or Debian Etch, I just used KnoppMyth and did some light boot scripting to make it comply with GRUB. That is a functioning workaround but not a solution. Hopefully one day I will find a fix for the real problem.

---

