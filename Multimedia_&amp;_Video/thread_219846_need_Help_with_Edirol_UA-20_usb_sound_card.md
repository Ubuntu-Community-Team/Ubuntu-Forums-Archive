---
title: "need Help with Edirol UA-20 usb sound card"
date: 2006-07-20
forum: Multimedia &amp; Video
---

### Post by alexx on 2006-07-20
Hello,
I am long time Debian user and just tried Ubuntu these days. I like it very much it's rocking.

Only one problem unsolved:
Edirol UA-20 usb audio interface not working with Ubuntu 6.06 on Sony Vaio laptop.

I searched the forums and saw several people having problems with UA-25 device. Some said it's working and others not.

Things that I noticed at a glance:
1) device is recognized and can be selected from the System->Preferences->Sound menu. After selection as a default sound card and opening again sound preferences the selection is reverted to the laptop card.

2) when the device is plugged in GNOME could not start.
3) unplugging the device GNOME starts successfully

On the forums one person said it has been working with a patched kernel.
```

alexx@forsythe:~$ uname -a
Linux forsythe 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux

alexx@forythe:~$ dmesg
.............
[17191520.992000] usb 2-1: new full speed USB device using ohci_hcd and address 2
[17191521.780000] usbcore: registered new driver snd-usb-audio
[17191717.756000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17191717.756000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[17191717.756000] agpgart: Putting AGP V2 device at 0000:01:05.0 into 1x mode
[17191717.984000] [drm] Setting GART location based on new memory map
[17191717.984000] [drm] Loading R200 Microcode
[17191717.984000] [drm] writeback test succeeded in 1 usecs
[17191776.216000] usb 2-1: USB disconnect, address 2
[17191776.216000] cannot submit datapipe for urb 0, error -19: no device
[17191776.216000] cannot submit datapipe for urb 0, error -19: no device
[17191776.216000] cannot submit datapipe for urb 0, error -19: no device
[17191776.216000] cannot submit datapipe for urb 0, error -19: no device
[17191776.216000] cannot submit datapipe for urb 0, error -19: no device
[17191776.216000] cannot submit datapipe for urb 0, error -19: no device
[17191776.216000] cannot submit datapipe for urb 0, error -19: no device
[17191776.216000] cannot submit datapipe for urb 0, error -19: no device
.............

```

Can you point me how to make this device working? I am planning to try it with some music production software. I will post more details if needed.

TIA.

---

### Post by alexx on 2006-07-20
at [http://www.ubuntuforums.org/showthread.php?t=155534](http://www.ubuntuforums.org/showthread.php?t=155534) I see

> Changes by Daniel T. Chen
..........
blacklist
..........
* sound/usb: **Fix Edirol UA-20**; Add Edirol UM-3ex/PC-50/UM-1EX/UM-2EX,

What is supposed to mean that? I don't quite understand.
There is a problem with Edirol UA-20 that has not been / can not be fixed so the device is blacklisted? Is that right?

---

### Post by drkmtr on 2006-11-07
I'm having an identical problem I believe, but I'm going to follow the ALSA config guide on this forum before I ask too many more questions to see whether I can get anywhere.

I'll post what I've already posted on LinuxForums.org:

> The problem I'm having is with my Edirol UA 20 USB audio interface. The system recognizes it to some extent, as when I plug it in a prompt comes up. Also, when I try a "lsusb" it can see it (Bus 001 Device 002: ID 0582:0025 Roland Corp. - in case that helps).

The problem is that I'm not 100% sure I've got my ALSA drivers installed correctly, and I can't get any sound playing through the USB interface (the onboard Realtek AC97 works OK).

I've found some mention of it in a search - a link here:
[http://www.cs.fsu.edu/~baker/devices...sb/usbquirks.h](http://www.cs.fsu.edu/~baker/devices...sb/usbquirks.h)

Seems to suggest that there is a patch of sorts. I'm not experienced with the technicalities, but would I be right in thinking that there might be a way to incorporate this code into the ALSA driver package, compile it, and then install the package to get things working?

I'm very new to this so it's really hard to experiment with compiling things and testing because I don't even know how to compile from the makefile or get any settings to reside in the correct place on the system.

If anyone could suggest any ideas for troubleshooting USB interfaces, or just point me in the right direction so I can learn more about the role of '.h' extension files in compiling source code so I can play around, I'd be forever grateful! 

I'd love to replace Windows completely, but at the moment it looks like I'll have to stick with dual boot using Windows for music production until I get some cash for a more widely supported card. It's a shame the manufacturers (Edirol or others in general) aren't more supportive in terms of giving developers the necessary development specs - it would be in their best interests really!

Thanks in advance for any help.

Cheers, Tom.

And an update I've just posted today:

> I just found this page:
[http://www.alsa-project.org/changes/...v1-0-11rc1.txt](http://www.alsa-project.org/changes/...v1-0-11rc1.txt)

Which says:
" + USB generic driver
- Summary: Remove xxx_t typedefs: USB-Audio
Remove xxx_t typedefs from the USB-Audio driver.
- Summary: usb-audio: fix Edirol UA-20 support
Somebody at Edirol f**ked up and released a new revision of the UA-20
without class-specific descriptors, so now we have to hard-code the
sample format."

Does this mean I have to hard code my preferred sample format myself somehow, some where in the ALSA configuration, or is it already done in an ALSA fix?

Any help would be much appreciated as this is really doing my head in!

If I find anything out I'll let you know mate, this is really confusing me!

---

