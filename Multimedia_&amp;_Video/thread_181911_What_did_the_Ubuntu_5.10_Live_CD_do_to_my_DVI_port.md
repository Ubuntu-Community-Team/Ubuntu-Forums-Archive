---
title: "What did the Ubuntu 5.10 Live CD do to my DVI port?"
date: 2006-05-25
forum: Multimedia &amp; Video
---

### Post by Tenchiro on 2006-05-25
I downloaded and burned the ISO for Ubuntu 5.10.  I booted from the new CD and all seeemed to go well. Until I rebooted...

As soon as it rebooted I was unable to get ANY video through my DVI port. Not when the BIOS posts or in Windows or even when booting from the Ubuntu CD.

I have a Radeon 9600 Pro, I have flashed the BIOS on it already and re-installed the latest drivers but am still unable to get any image through the DVI port.  The VGA port works fine though.

Any suggestions on getting my DVI video back?

---

### Post by IvoryTiger on 2006-05-25
Same problem here with a ViewSonic VA2012wb.  Worked fine with XP for a few months, installed the lastest version of Ubuntu, and after the system rebooted, I can't get any output from the DVI port on my nVidia 6600GT.

I exchanged the monitor and got a new one that worked fine with XP again including multiple reboots, but as soon as I rebooted out of Ubuntu, I lost the signal again.

So I can confirm the video card is still putting out a digital signal because I didn't have to reinstall any drivers with the newer monitor, I just plugged it in and it worked.

---

### Post by gitfiddler on 2006-05-25
Based on the description, it sounds like the DVI port is not affected, but the monitor is. Maybe there is a menu selection on the monitor that will reset it to the factory settings? Failing that, maybe Viewsonic can provide a solution.

---

### Post by Tenchiro on 2006-05-25
[QUOTE=IvoryTiger]Same problem here with a ViewSonic VA2012wb.  Worked fine with XP for a few months, installed the lastest version of Ubuntu, and after the system rebooted, I can't get any output from the DVI port on my nVidia 6600GT.[/QUOTE]

That is the same display that I have...

---

### Post by IvoryTiger on 2006-05-26
I ended up returning my to Costco and picked up a new one in exchange.  The new one worked fine on the DVI port first try with Grub and Windows, so I can defintely say it was the monitor and not the video card.  I will not boot into Ubuntu again until I find a defintive answer for this.  It's happened on two Viewsonic VA2012wb's and I doubt Costco would be happy about taking back a third because a configuration for X-Windows kills the DVI port.

---

### Post by MiD-AwE on 2006-05-27
[FONT=Arial][SIZE=3]I have the 6600gt but I run 2 CRTs with vgs converters, and I cant get Ubuntu to recognize my screen2. Could this be a bigger issue than newbe pains?[/SIZE][/FONT]

---

### Post by fvgm on 2006-11-03
Hi, i have a Radeon 9250 (rv280) agp card, and when X stars, everything go blank with DVI output (using fglrx). The DVI port work perfect over windows.. but in Ubuntu nothing..
Can anyone help me??

---

