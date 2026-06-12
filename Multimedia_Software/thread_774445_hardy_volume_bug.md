---
title: "hardy volume bug"
date: 2008-04-29
forum: Multimedia Software
---

### Post by AndThenWhat on 2008-04-29
Ok so I decided about 3 days ago to upgrade to Hardy Heron and for the most part it has worked awesome.  The only problem is my sound.  There is no sound when the master volume control is below 50%. Basically, 50% volume is actually 0% volume.  

Another weird thing is that when my sound is on **autodetect** under *system>preferences>sound* i don't have sound.  it only works when i set everything to **alsa**.

**lspci:**

```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

---

### Post by Deten on 2008-04-29
Same issue here, about 50% (maybe 45%?) I get zero sound :(

Also I can only have 1 sound play at any given time, so If I am listening to music and open a video on youtube, the video doesnt have sound :(

I am messing around trying to fix it.

---

### Post by jasreca on 2008-04-30
I'm having the same problem. 
I have my system hooked up on to my stereo, so it wasn't until yesterday, when I wanted to listen to an mp3 a bit louder than usual, that I noticed I had to pump the volume on the stereo up to -0 dB to hear it at the level it used to sound at around -28 dB on Gutsy... (that's all at 100% output)

SOLVED:
just ```
alsamixer
``` in terminal - then slide Front to max. :)

---

### Post by ndrone1 on 2008-06-11
Any solutions to this? I'm having the same 50%=0% issue with hardy 8.04 on my m1330. exciting stuff though, i have it all beautified.. now if I can only get my sound to work perfectly, I'll probably quit using vista.

anyone?

---

### Post by ndrone1 on 2008-07-05
> **ndrone1 said:**
> Any solutions to this? I'm having the same 50%=0% issue with hardy 8.04 on my m1330. exciting stuff though, i have it all beautified.. now if I can only get my sound to work perfectly, I'll probably quit using vista.

anyone?

by the way, the alsamixer "fix" doesn't work for me. someone? please help? need all 100% range! :)

---

### Post by IanW on 2008-07-05
Try double-clicking on the volume control widget on the panel.

I've found that Master will stay where you set it, but PCM sometimes defaults to about 40%, leaving things very quiet.

---

### Post by AndThenWhat on 2008-07-09
> **IanW said:**
> Try double-clicking on the volume control widget on the panel.

I've found that Master will stay where you set it, but PCM sometimes defaults to about 40%, leaving things very quiet.

Thanks, but this definitely seems to be some sort of bug.  I have tried everything under the sun that I could in the GUI and found no fix yet.

---

### Post by ndrone1 on 2008-07-20
> **AndThenWhat said:**
> Thanks, but this definitely seems to be some sort of bug.  I have tried everything under the sun that I could in the GUI and found no fix yet.

Yes indeed. How do we make this an official "bug," then? 

Thanks for someone finally agreeing with me that adjusting the volume levels won't fix it...

---

### Post by Deten on 2008-07-30
Ive messed with everything and no fix?

DO we all have laptops? I am using sony vaio vgn-fe790p

---

### Post by AndThenWhat on 2008-08-04
I have a Gateway Laptop with an Intel Centrino Duo Processor and 2.0 GB RAM.  I am running Hardy Heron 8.04 on the Linux 2.6.24-19-generic kernel.

---

### Post by Deten on 2008-08-23
Any news on this?

---

### Post by Deten on 2008-11-25
any news again?

---

### Post by AndThenWhat on 2009-06-05
the problem is solved for me in intrepid

---

