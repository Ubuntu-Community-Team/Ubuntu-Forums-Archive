---
title: "RecordMyDesktop Soundcard Issue"
date: 2008-04-23
forum: Multimedia Software
---

### Post by dbee on 2008-04-23
So I've installed RecordMyDesktop and it seems to work fine. Apart from the fact that it won't accept my alsa driver sound card. Pls note that sound input works fine for other applications such as Skype. I don't think it's an ALSA config issue ...

Run with default sound device....

```

babo@eire:~/Desktop$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:800
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:800
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device.

```

Check for sound devices on my system

```

babo@eire:~/Desktop$ sudo asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
Intel

```

Run, supplying Intel sound device to RecordMyDesktop

```

babo@eire:~/Desktop$ recordmydesktop -device Intel
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:800
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:800
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM Intel
Couldn't open PCM device Intel
Error while opening/configuring soundcard Intel
Try running with the --no-sound or specify a correct device.

```

Pls note, that Skype uses HDA Intel as it's sound device setting, so I've used that and a number of other variations eg. 'HDA Intel', HDA etc...

Do any ALSA / RecordMyDesktop pro's out there know what could be the solution to my problem ... ?

Thanks,

---

### Post by dbee on 2008-04-24
Anyone ?

---

### Post by the_hack on 2008-11-07
Same issue here.

---

### Post by Intrepid Ibex on 2008-12-19
What is the soution?!

I'm also having this issue!

---

### Post by markbuntu on 2008-12-19
There is probably a much easier way than this but it is something I found that actually does work;


[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

---

### Post by andr3w on 2009-01-27
> **markbuntu said:**
> There is probably a much easier way than this but it is something I found that actually does work;


[http://ubuntuforums.org/showthread.php?t=986966](http://ubuntuforums.org/showthread.php?t=986966)

Doesn't work for me! :D

---

### Post by Rhemat on 2009-11-08
I'm having the same issue.  I should note that my Video Card (MSI RX2400Pro w/ ATi HD2400 chipset) has audio hardware, and gets grabbed some times.  So in my case, it might be using the video card.  It could also be using the mainboard's audio, but I think I shut that down in BIOS.  I'm trying to use my Ensoniq PCI sound card.  Here is my lspci output:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
01:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:05.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
02:0a.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)

---

### Post by TrippMan668 on 2013-02-15
Time to re-vamp this old thread!  
 Same issue here. Worked last night. Don't memb how I got it to work. But I don't think I did anything special. Now this afternoon, it's not working again.

"Initial recording window is set to:
X:0   Y:0    Width:1600    Height:900
Adjusted recording window is set to:
X:0   Y:2    Width:1600    Height:896
Your window manager appears to be compiz


Detected compositing window manager.
Reverting to full screen capture at every frame.
To disable this check run with --no-wm-check
(though that is not advised, since it will probably produce faulty results).

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device."

---

