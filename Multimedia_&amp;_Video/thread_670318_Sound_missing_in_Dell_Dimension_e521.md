---
title: "Sound missing in Dell Dimension e521"
date: 2008-01-17
forum: Multimedia &amp; Video
---

### Post by Method9455 on 2008-01-17
I have a Dell Dimension e521-n with Ubuntu Feisty running and it doesn't have any any sound. I've seen two wikis that say it should work, but it doesn't, so it must be a config on my computer. I check alsamixer and the normal volume controls in Gnome. Everything was unmuted. I'm using a known to be good pair of headphones and it doesn't work out of the front or back jack.

lspci
lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


lscpi -v

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
Subsystem: Dell Unknown device 01ed
Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

Are there other logs that can help? I checked out a couple guides and wikis and got no where.

---

### Post by balaknair on 2008-01-17
could you type this in a terminal and post the output
aplay -l

---

### Post by Method9455 on 2008-01-17
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by balaknair on 2008-01-17
Hi
Sorry for the delay
I was going through the ALSA documentation and the Dell Linux support wiki.
I think the HDA intel module should work for you.
 In a terminal type
sudo modprobe snd-hda-intel

Next find your specific card codec by typing
cat /proc/asound/card0/codec#* | grep Codec

It should be STAC92__ (need the last two digits)
Now go to this page [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

and find the card codec on it and look at the model descriptions alongside. find the one which matches your system closest.

Then enter
sudo nano /etc/modprobe.d/alsa-base

and paste this as the last line(use the down arrow to scroll down till you you reach the bottom of the page) depending on whether you have 
options snd-hda-intel model=MODEL

(replace MODEL with your model description from the earlier link)
Save and exit
Reboot

These steps are based largely on the HDA-Intel howto at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
It's an excellent guide
You can look it up in case of any doubts

All the best

---

### Post by Method9455 on 2008-01-17
Wow balaknair that was an awesome how to, it worked perfectly first try. Thanks a lot! i spent a lot of time this morning trying to get this going and I couldn't get there, I really appreciate the time you spent to help.

---

### Post by Yellow Pasque on 2008-01-17
Please mark thread as SOLVED

---

### Post by balaknair on 2008-01-20
@Method9455
Thanks buddy, glad to have been able to help
My way of repaying those who helped me in Ubuntuforums
Hope you'll be able to help others in turn
Have fun

---

