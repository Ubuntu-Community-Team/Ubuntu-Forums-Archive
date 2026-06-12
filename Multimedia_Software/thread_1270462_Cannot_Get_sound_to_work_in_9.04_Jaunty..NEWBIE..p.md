---
title: "Cannot Get sound to work in 9.04 Jaunty..NEWBIE..plz help"
date: 2009-09-19
forum: Multimedia Software
---

### Post by harkkam on 2009-09-19
Hi guys I am newbie to Linux and Ubuntu itself. I am running Ubuntu version 9.04 with all the latest updates. Currently I hear no operating sounds or when I click on the Aespo fables music file and open it I hear no sound.

Currently my sound preferences say

Sound Events:
Nvidia CK804 with ALC850 Nvidia CK804 (ALSA) (Custom) 

When I click on the sound test...I DO...hear a sound....I used a gstreamer or something to fix that, but all I hear is the test sound nothing else still.

Music and Movies

Nvidia CK804 with ALC850 Nvidia CK804 (ALSA)

When I click the test audio button I get

"Audiotestsrc wave=sine freq=512! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback"

Default Mixer track 
Nvidia CK804 (Alsa) Mixer


I ran ```
aplay -l
``` and

> lspci
I got

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


THEN

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
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GT] (rev a1)
05:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)




Guys can someone plz help me I love ubuntu I just cant get the sound to work. I would hate to have to go back to XP because of sound...Thank you

I have no tried anything yet out of fear of courrupting the files thank you.

---

### Post by kostkon on 2009-09-19
I can see that you have 2 audio devices. Which one do you want to use?

Nevertheless, set everything to *Autodetect* and then try to set a default audio device using the *PulseAudio Device Chooser* utility.

More info [here]("http://ubuntuforums.org/showthread.php?t=1130384").

Also, if you can see a speaker icon in your system tray, click on it to access the volume control and then check the volume levels of your audio devices.

---

### Post by harkkam on 2009-09-20
hmm

I couldnt find the pulse audio driver utility mentioned. Also should I follow all the instructions with the link you have provided me with.

I want to use the NVIDA sound card. The M-audio one has not been connected to my speaker system.

Thx

---

### Post by kostkon on 2009-09-20
> **harkkam said:**
> hmm

I couldnt find the pulse audio driver utility mentioned. Also should I follow all the instructions with the link you have provided me with.

I want to use the NVIDA sound card. The M-audio one has not been connected to my speaker system.

Thx
You need to search for “PulseAudio Device Chooser” in *Synaptic* or *Add/Remove* to find it and install it. It's a utility, an application. If you check the link I have given you above, you will learn how to set a default card for your system using this utility.

Hope that helps.

---

