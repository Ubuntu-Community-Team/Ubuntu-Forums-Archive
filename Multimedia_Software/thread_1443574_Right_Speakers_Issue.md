---
title: "Right Speakers Issue"
date: 2010-03-31
forum: Multimedia Software
---

### Post by MSOlhao on 2010-03-31
I'm having a strange issue on my front right and rear right speakers.
I don't know exactly how to explain this, but my left, rear left and center speakers has a nice sound but the rear right and front right speaker has a strange noise when i play audio files or movies.
I attach some audio files for you guys understand the problem.

***aplay Output: ***
>  
 **** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
***lspci Output: ***
>  
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)


***Note:*** I know, the sound is a crap but was the first ogg file I found. ;)

---

### Post by MSOlhao on 2010-03-31
If you need more info about my system please let me know.

---

### Post by RedSingularity on 2010-03-31
I know this sounds obvious but are the speakers plugged in properly?

---

### Post by MSOlhao on 2010-04-01
Yes, they are.
When I test it with ***speaker-test -Dplug:surround51 -c6 -l1- twav***, the sound is good, but with audio files or video I got this strange noise.

---

### Post by RedSingularity on 2010-04-01
How does it sound when you test it in "sound preferences"?

---

### Post by MSOlhao on 2010-04-01
In *sound preferences* if I test it with ***Analog Stereo Output*** profile, the sound is good, but only plays the Font Left and the Front Right, no Center and Rears speakers.
Otherwise if I try it with ***Analog Surround 5.1 Output*** the sound plays in every speakers but with this strange noise from Rear Right and Front Right speakers. :confused:

---

### Post by lyall on 2010-04-01
check **SurroundSound** in Community Documentation
[https://help.ubuntu.com/community/SurroundSound]("https://help.ubuntu.com/community/SurroundSound")

it should help you

good luck and have fun learning

---

### Post by MSOlhao on 2010-04-02
Thanks for the answer.
I did what's in that guide without success.
I got good sound on every speakers when I use the speaker-test command, but in other applications, the annoying noise is there.

---

