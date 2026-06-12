---
title: "Omnivision Technologies USB Webcam Mic Not Working"
date: 2009-02-21
forum: Multimedia Software
---

### Post by genesis2seven on 2009-02-21
I have a fresh install of Ubuntu 8.10 on a Dell XPS 630i and everything is working great except for the mic for the USB webcam that is embedded in my Dell SP2208WFP Monitor isn't working. It works fine under my Vista partion and the microphone on my headset works when I plug it in to the mic jack on the front of my box but I would ideally like to be able to use the one built into the monitor.

I've tested under ekiga, skype, and sound recorder. When I open System>Preferences>Sound my settings are as follows:

-----Scenario 1-----

Sound Events

  Sound playback: Autodetect

Music and Movies

  Sound playback: Autodetect

Audio Conferencing

  Sound playback: Autodetect
  Sound capture: Mic-OmniVision Technologies, Inc.53802640-07.08.07.6 Monitor Webcam (SP2208WFP) USB Audio (ALSA)

Clicking the Test button gives the error: gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not get/set settings from/on resource.

-----Scenario 2-----

Sound Events

  Sound playback: Autodetect

Music and Movies

  Sound playback: Autodetect

Audio Conferencing

  Sound playback: Autodetect
  Sound capture: Mic-OmniVision Technologies, Inc.53802640-07.08.07.6 Monitor Webcam (SP2208WFP) OSS Control Device (OSS)

Clicking the Test button I get a brief bleep of static through the speakers and then the Testing Pipeline window opens and displays a moving progress bar but nothing else ever happens.

lspci | grep -i audio

Provides the following:

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

And the full output of lspci is:

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)


Any help would be greatly appreciated. I have also tried an exhaustive combination of un-muting etc in the volume control panel. My default Device listed in Volume Control is HDA NVidia (Alsa mixer).

---

### Post by genesis2seven on 2009-02-26
Bump. Bueler, Bueler? Anyone?

---

### Post by genesis2seven on 2009-02-27
One more time.... Anyone at all. Hardware gurus out there anywhere?

---

### Post by erlguta on 2009-03-30
I have exactly the same problem with the same Dell Monitor. Webcam works fine, but not the mic.
I don't know what to try...i think i have tried everything in the sound properties.

---

### Post by genesis2seven on 2009-03-30
I still have not found a solution but it looks like it is somehow connected to the problems with alsa/pulse audio. From what I've been reading on the brainstorm website etc. I'm hopeful that it is going to be fixed/seamless in the 9.04 release in a few weeks as it seems to have gotten quite a bit of traction in the way user requests for a fix.

---

### Post by erlguta on 2009-03-30
> **genesis2seven said:**
> I'm hopeful that it is going to be fixed/seamless in the 9.04 release in a few weeks as it seems to have gotten quite a bit of traction in the way user requests for a fix.

I hope it so. If not, maybe this is a good starting point:
[http://audacityteam.org/wiki/index.php?title=USB_mic_on_Linux](http://audacityteam.org/wiki/index.php?title=USB_mic_on_Linux)

Is there any request in Dell ideastorm to make pressure about this on Dell? Do you have any link?
Where did you find that users requests for this problems?

Thank you

---

### Post by genesis2seven on 2009-04-27
Ok so once again fresh install of ubuntu 9.04 and webcam works great out of the box but the mic does not work at all. Have found a lot of people with the same problem via googling but no one with a solution yet. I tried both 64 bit and 32 bit ubuntu. I've tried adding myself to the pulse audio groups. I tried removing pulse audio. Tried calling Dell premium tech support but they were worthless. Nothing has helped. Assistance would be greatly appreciated.

current lspci output for my now 9.04 32bit install.

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:05.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 9800 GT (rev a2)
03:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

---

### Post by erlguta on 2009-10-24
Yuhuuu!.
It works perfectly in Karmic!

---

### Post by ubushtu on 2009-12-24
Same problem here.  I'm running Karmic (upgrade from 9.04) and my SP2208WFP webcam works great, but not the embedded mic.  I realized it when I went to Skype with my sister tonight.

Can anyone else attest that this mic works in 9.10?

---

### Post by ubushtu on 2009-12-25
Doah, nevermind my previous post.  My mic is actually working just fine in 9.10  Just had to bump the input volume way up on it.

---

### Post by wheezer on 2010-10-07
I have karmic and this dell 2208 monitor that fails. Can someone tell me precisely how to configure both the cam and mic? That includes any applicable setting, as something is obviously wrong.  Is this some new pulse audio fail that makes me wish I bought a mac?

---

