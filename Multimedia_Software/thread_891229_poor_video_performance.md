---
title: "poor video performance"
date: 2008-08-15
forum: Multimedia Software
---

### Post by ProDigit on 2008-08-15
Hi,

I'm using a very old computer from 2000/2001 hardly able to run XP; here are the specs:

AMD Athlon 1240Mhz, 512 & 256 MB ram @ 100Mhz, 200 & 40 GB HD.
On board sound and video card.
Resolution set to 1024 x 768 @ 32bit or 1280 x 1024 @ 16bit colors.

I know it's an old PC, but under XP I am able to use this PC to download, browse, check mails, and watch simple DVD video's with resolutions upto 720x512 pix I suppose. DivX under Windows with resolutions 640x480 tested and worked fluently.

Under Linux however (Latest Xubuntu), when playing back the Nelson Mandela .ogg video provided in Ubuntu examples, the image barely gets 15-20 images, and at full screen it gets about 5 or less fps.

Is there something that can be done to make my video's run more smooth?

I'm into Xubuntu now, once I'm in Windows, I'll post the Graphic chip, since I can't seem to find it in here.(probably on generic)

---

### Post by overdrank on 2008-08-15
> **ProDigit said:**
> Hi,

I'm using a very old computer from 2000/2001 hardly able to run XP; here are the specs:

AMD Athlon 1240Mhz, 512 & 256 MB ram @ 100Mhz, 200 & 40 GB HD.
On board sound and video card.
Resolution set to 1024 x 768 @ 32bit or 1280 x 1024 @ 16bit colors.

I know it's an old PC, but under XP I am able to use this PC to download, browse, check mails, and watch simple DVD video's with resolutions upto 720x512 pix I suppose. DivX under Windows with resolutions 640x480 tested and worked fluently.

Under Linux however (Latest Xubuntu), when playing back the Nelson Mandela .ogg video provided in Ubuntu examples, the image barely gets 15-20 images, and at full screen it gets about 5 or less fps.

Is there something that can be done to make my video's run more smooth?

I'm into Xubuntu now, once I'm in Windows, I'll post the Graphic chip, since I can't seem to find it in here.(probably on generic)

Hi and you can find the graphics model with the command ```
lspci
``` in the terminal located under applications. And look for VGA

---

### Post by ProDigit on 2008-08-16
In windows the display adaptor is set to:
SIS 300/305/630/540/730

It's also using 64MB shared memory.

I'll updatee as soon as possible what Linux says using the command above, thank you.

---

### Post by ProDigit on 2008-08-16
I'm running Linux now, and the above lin. command gives me the following data:

```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)

```

---

### Post by ProDigit on 2008-08-26
bumpedy bump

---

### Post by overdrank on 2008-08-26
Hi and yes the [SiS] 630/730 PCI/AGP  are not supported well in linux. You can try and install displayconfig-gtk and then use the command ```

gksu displayconfig-gtk
``` to set the graphics driver and resolution.

---

### Post by ProDigit on 2008-09-04
Okay,
The display I have is a SIS 730. The driver installed is from a SIS 630.

So far 704x400 Divx plays back fluently.
640x480 divx, and xvid goes fluently as well...

XviD 864x474 goes at about 12fps.

720p video goes about 5-6fps full screen. Not fluently, but probably the max this gpu can handle...

The image card also seems to have issues with H264 848x480 pix (about 1fps full screen, and about the same or a bit more in 100% window playback).

it still has minor issues like I can't select 1280x1024 @ 75Hz for movie playback, or I get weird lines on my screen.
However I'm very happy most non-HD videos seem to playback fine on this system (with the exception of H264 encoded movies.
It seems I can play tuxracer on about 15FPS @ 800x600 res. so thanks for the help!

---

