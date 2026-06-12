---
title: "Asrock ION 330 as a HTPC, which way to go ?"
date: 2009-08-31
forum: Multimedia Software
---

### Post by azatot on 2009-08-31
Hello everyone!
 
Ive recently bought an Asrock ION 330 to use as a htpc with XBMC. First i tried windows xp but fortunately the sound via HDMI didnt work so i switched to Ubuntu which ive never tried before and love it!
 
HDMI-sound worked in ubuntu after unmuting everything in alsamixer and then i followed a guide on the XBMC-forum to setup xbmc on an asrock ion 330 with a desktop installation of the latest ubuntu. And everything seemed to work until i installed the latest nvidia graphics driver after which i got a terrible overscan when connected to my Samsung LE-40S71B LCD-TV (with HDMI). 
 
Apparently Samsung doesnt recommend using HDMI when connected to a PC, but the strange thing was that before i installed the nvidia drivers the picture was perfect (but .avi etc framedropped as h*ll) and no overscan at all, so im thinking its the nvidia drivers that screwed things up (it was the same thing in Windows XP when i installed the nvidia drivers but thats easily fixed with a slider to resize the image in nvidia control panel). I havent seen a fix for the overscan when searching (is there one?).
 
So im thinking which way to go from here, im a linux newbie. Should i:
 
1. Continue trying to find a fix for the overscan via HDMI
2. Switch to a VGA-VGA cable and in that case how should i connect the sound? (HDMI, SPDIF, regular green audio output) And also is the VGA-solution as good as the HDMI-solution image-wise? I only need like 50cm of VGA-cable. Is the difference big between a cheap vs expensive VGA-cable when its only ~50cm long?
3. Go back to Windows :(
 
 
Would appreciate some input on this matter.
 
Best regards
Azatot, king of HTPC

---

### Post by steefjeqv on 2009-09-01
Hi,

Some pointers :

- Doesn't XBMC have an option to resize the overscan ?

- You can use a modeline in your xorg.conf.
[http://www.xbmc.org/forum/showthread.php?t=54685]("http://www.xbmc.org/forum/showthread.php?t=54685")

- I'm using a vga cable connected to a large crt monitor and the quality is quite good. The vga option might be the easiest way to go.

Greetings,
Steven

---

### Post by panasonicyouth on 2009-09-01
Hello,

I too am an Ubuntu noob, but more to the point one with a brand new Asrock Ion 330 intended as an XBMC HTPC.

I've gone a completely different root to you - started out with ubuntu and spent ages trying to install nvidia drivers (easily most complicated thing I've done since having the Asrock and ironically the very first thing I had to do!) and only THEN did I get the correct resolution. Bizarrely sounds like it's the other way round for you - maybe the drivers didn't install properly, like I said it was a huge pain for me to get done.

The way I'm connected is using the HDMI to DVI adapter as provided with the Asrock. DVI, to best of my knowledge, offers same qualiy as HDMI but obviously no sound. I chose this because I heard of HDMI sound problems v/and also because for some reason HDMI would only let me have a 1080 resolution - the TV/Monitor I'm using has max of 1440 x 900 (another coincidence here, it's also a samsung!).

So my route was that - I think the amount of image quality you lose between VGA and HDMI/DVI is relative to how much of a conniseur of such things you are. I can jus about tell the difference. If your TV has a DVI I would try that just to see. Oh and for sound I am using 3.5mm to 2 phono so I can connect it to my Hi Fi. All working rather well too!

My only concerns have been gaming with the Asrock under Ubuntu considering under XP it has been shown to run Call of Duty with ease wheras I have been choking with Team Fortress. Bit of a shame but the VDPAU under XBMC evens it out.

---

### Post by forumache on 2009-09-11
It might help:

I installed everything (including NVIDIA drivers) while Asrock Ion 330 was connected to a LCD (DVI).

Then I connected it to the TV in the living room, via HDMI.
The TV is Samsung LE40A656. I had overscan.

Then I remembered. In my Samsung manual it was written: When you connect a PC over HDMI you have to connect it on HDMI2 (I did this) *and* rename HDMI2 to PC (In the Samsung Menu/Sources). Immediately when I selected PC from the Samsung Menu on the TV screen, everything fit perfectly, no overscan.

So, in my case, the one which needed adjustment was the TV, not PC. And it was documented in the manual.

Try it. HDMI2 connection *and* rename HDMI2 source to PC.

---

### Post by ThinkDave on 2009-10-16
> **forumache said:**
> It might help:

I installed everything (including NVIDIA drivers) while Asrock Ion 330 was connected to a LCD (DVI).

Then I connected it to the TV in the living room, via HDMI.
The TV is Samsung LE40A656. I had overscan.

Then I remembered. In my Samsung manual it was written: When you connect a PC over HDMI you have to connect it on HDMI2 (I did this) *and* rename HDMI2 to PC (In the Samsung Menu/Sources). Immediately when I selected PC from the Samsung Menu on the TV screen, everything fit perfectly, no overscan.

So, in my case, the one which needed adjustment was the TV, not PC. And it was documented in the manual.

Try it. HDMI2 connection *and* rename HDMI2 source to PC.

You sir WIN at the internet. 1000 gold stars for you, I'm so glad your mother gave birth to you. :P

Cheers for the tip made my ASRock look crystal clear not sure what Samsung were thinking with that strange setup.

---

### Post by forumache on 2009-10-16
@ThinkDave,

I am glad that it is working for you. I received your Private Message too. You are welcome.

I discovered an even better solution, if you want to improve your setup:
In the manual it says to connect to HDMI2 and rename it to PC if your computer has 1920x1080@60Hz. This was what I recommended before.

But now, since I wanted to be able to play movies at 24Hz (better synchronisation), I changed my setup to allow output to different refresh rate:

- let it connect to HDMI2 but this is not required anymore.
- removed the PC name, leaving --- (no name)
- Select the HDMI source (1,2,3,4) then, in TV Menu, Picture, select More, you'll see Picture Options. Select Size: "Just Scan"

from the manual: just scan: use the function to see full image without cutoff when hdmi signals are input

Exactly what I need. This will allow me to get the same perfect image but without being restricted to a specific HDMI port and without being forced to used the fixed frequency of 60Hz

Enjoy.

---

### Post by perevera on 2010-01-07
I have a Pioneer PDP-428XD, the only hint I can find is regarding the audio supported at the HDMI inputs:

PCM stereo with sampling rates: 32 KHz, 44,1 KHz, 48 KHz.

This looks very standard and I guess this is supported by ALSA, right?

I installed ALSA version 1.0.22.1, but with 'alsamixer' I cannot find a track like 'HDMI' or not even 'IEC958' to unmute them.

In summary, I still don't have sound at the HDMI output, although I have sound at the analog stereo output ('front').

Some info about my system:

perevera@minipc:~$ lspci
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
**00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)**
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

perevera@minipc:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: ALC889A Analog [ALC889A Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 1: ALC889A Digital [ALC889A Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: NVidia [HDA NVidia], dispositivo 3: [B]NVIDIA HDMI [NVIDIA HDMI]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0[/B]
perevera@minipc:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=NVidia
    HDA NVidia, ALC889A Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
[B]hdmi:CARD=NVidia,DEV=0
    HDA NVidia, NVIDIA HDMI
    HDMI Audio Output[/B]

---

### Post by Pavel Moukhataev on 2011-03-28
I had the same overscan problem with Samsung TV and intel integrated HDMI video (G41 / GMA X4500). And found that pressing "p.size" button on TV solves this problem. This TV has resolutions like "16:9", "4:3", something else and last resolution is "move picture" and in this mode there is no overscan. I am happy.

---

