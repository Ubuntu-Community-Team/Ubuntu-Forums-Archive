---
title: "Playing Windows .wmv and Quicktime .mov files - Solved"
date: 2008-07-06
forum: Multimedia Software
---

### Post by weedwacker on 2008-07-06
I just did a fresh install of Hardy 8.04 and after loading all the necessary restricted files in order to view Quicktime movie trailers (.mov) as well as Windows video files (,wmv) I found I could not view them.  I would get the MPlayer plugin showing on the screen and audio, but no video.

After struggling with this issue for a while, I remembered that during the install of Hardy I was offered the option of installing the proprietary Hardware Driver for my ATI graphics card: [COLOR="Blue"]**xorg-driver-fglrx**[/COLOR] which I did.

I uninstalled this driver from System>Administration>Hardware Drivers, rebooted and found that I had no further problems viewing Quicktime and Windows video files.

My graphics card is the ATI Radeon 9800 on my ASUS/AMD computer.

I have another computer: an HP Presario that has a mother board with an internal graphics card (ATI RS480 (Raden Xpress 200G Series) and I have the **[COLOR="Blue"]xorg-driver-fglrx[/COLOR]** installed and I have no problems viewing .wmv and .mov files. Go figure!

Hope this helps someone. :KS

---

