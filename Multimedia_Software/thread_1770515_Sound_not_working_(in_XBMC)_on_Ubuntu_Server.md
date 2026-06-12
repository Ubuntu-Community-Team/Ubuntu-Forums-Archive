---
title: "Sound not working (in XBMC) on Ubuntu Server"
date: 2011-05-29
forum: Multimedia Software
---

### Post by G-forze on 2011-05-29
Hello,

I've been trying for a day to get sounds working on my HTPC which is running Ubuntu Server (Natty) and XBMC from the repositories. I have so far had no luck, with not so much as a peep on any channel - analog, optical or over HDMI.

My setup is a ASUS AT3IONT-I with an Intel Atom CPU. I think this is a common configuration which should not require any special treatment, and I also have a friend with the same hardware and no problems running XBMC on OpenSUSE. 

XBMC is installed according to the instructions here [http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide) with a user named xbmc etc. It works wonderfully in every aspect except that the sound is missing alltogether.

I've been following [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) for troubleshooting but have now run out of ideas, which is why I'm asking you.

```
aplay -l
``` gives me 

```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC887 Analog [ALC887 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC887 Digital [ALC887 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and 

```
lspci
``` gives me

```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```

From this it is clear that the system correctly recognizes the hw.

Trying to play something with aplay generates an error, however.

```

xbmc@Outpost:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:660: audio open error: No such file or directory

```

This error also appears in the XBMC logs.

Another oddity is that my /dev/audio is missing, as well as /dev/mixer and /dev/dsp which I think should be there.

I've also tried resetting alsa using 

```

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

```

but it changes nothing. 

I tried filling in with all the details I could think of, but if you wish to know something more I'll be glad to provide it. This is really giving me a headache and I have a feeling I am only missing some small detail. Any help will be much appreciated!

---

### Post by ghostborg on 2011-05-29
I had a Jetway Mini-top that I upgraded from 10.10 to 11.04 and had sound problems/ no sound. It turned out to be some bug. I lived with that for about a week or two and one day an update came down. Crossed my fingers and blamo everything worked. For the life of me I cannot remember the exact problem but I think it had to do with the Nvidia chipsets. I gave up trying to resolve the issue once I found a bug report that described my problem and others had the same issue. So my point is you might want to search and read some of those reports as things may be out of your control to fix them.
I wasted a week off and on trying to resolve it.

Good Luck to you and hope it is something simple.

---

### Post by G-forze on 2011-05-31
Thank you ghostborg for the response.

I have not yet found a solution to my problem. I will give it a rest and have another look at it in a few days, then maybe I will get som new ideas.

I'll also go look through the bug reports to see if I find something that fits.

---

### Post by hvc123 on 2011-05-31
have u tried headphones in the audio jack ?

i only ask as i had the same problem with my htpc and my samsung series6 tv. when plugged into the vga or hdmi/dvi slot the sound (ANALOGUE) would not work. 
the only way i got it to work was to go ito the tv service menu and change the hdmi/dvi port audio from auto to dvi. as soon as the tv rebooted i had sound from the tv

---

### Post by lidex on 2011-05-31
have a look here:
[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

---

