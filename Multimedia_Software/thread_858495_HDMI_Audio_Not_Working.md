---
title: "HDMI Audio Not Working"
date: 2008-07-13
forum: Multimedia Software
---

### Post by dan9186 on 2008-07-13
I have a MSI K9N2GM motherboard with HDMI output on it.  The board has a NVidia GeForce 8200 built on and I'm running the 177 beta drivers to try and get the audio to work.

A few things I have read have talked about having to direct the audio through the HDMI port and I've tried everything that I've seen suggested to no avail.  I've even checked to make sure that it wasn't something as simple as the audio being muted.

Has anyone else had any luck at getting audio to work on this motherboard or have any other suggestions to try?

Thanks in advance

---

### Post by dan9186 on 2008-07-13
Other added notes:

I can see and have the IEC958 switch checked in the mixer.
I've also double checked using alsamixer.
I've checked to make sure I have the latest alsa version.

Here's the output by typing aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

---

### Post by musta78 on 2008-07-14
Hi.

I'm having a huge problem getting it to show video through the hdmi.  Did you get yours working?  Can't find a thread about how to get it to work.  The only thing I found was something about installing both nvidia settings and nvtv.  Well I've done that but when I try to launch nvtv nothing happens!

Sorry for putting this is your audio post!

---

### Post by xc3RnbFO8P on 2008-07-14
In Terminal:
> nvidia-settings

---

### Post by xc3RnbFO8P on 2008-07-14
**dan9186**, its a Beta ,
you can read about how it goes here:
[http://www.nvnews.net/vbulletin/showthread.php?t=97993&page=3]("http://www.nvnews.net/vbulletin/showthread.php?t=97993&page=3")

---

### Post by musta78 on 2008-07-14
> **Ringi said:**
> In Terminal:

Well to save the file you need to write "sudo nvidia-settings"

But I don't get what to change in NVIDIA x settings.  Whatever I do I can't get an output.  Would you mind poste your xorg.cof file so I can run throug it.

---

### Post by xc3RnbFO8P on 2008-07-14
Show the output of **lspci** in Terminal.

---

### Post by dan9186 on 2008-07-17
Sorry it took so long to reply, I've had summer school going.  But it would seem that this is a good start for why things are not working.

```
00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0778 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)
05:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
```

---

### Post by musta78 on 2008-07-18
As far as I can see, mine is identical!

00:00.0 RAM memory: nVidia Corporation Unknown device 0754 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 075c (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0752 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0751 (rev a1)
00:01.3 Co-processor: nVidia Corporation Unknown device 0753 (rev a2)
00:01.4 RAM memory: nVidia Corporation Unknown device 0568 (rev a1)
00:02.0 USB Controller: nVidia Corporation Unknown device 077b (rev a1)
00:02.1 USB Controller: nVidia Corporation Unknown device 077c (rev a1)
00:04.0 USB Controller: nVidia Corporation Unknown device 077d (rev a1)
00:04.1 USB Controller: nVidia Corporation Unknown device 077e (rev a1)
00:06.0 IDE interface: nVidia Corporation Unknown device 0759 (rev a1)
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 075a (rev a1)
00:09.0 IDE interface: nVidia Corporation Unknown device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 0760 (rev a2)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 0569 (rev a1)
00:10.0 PCI bridge: nVidia Corporation Unknown device 0778 (rev a1)
00:12.0 PCI bridge: nVidia Corporation Unknown device 075b (rev a1)
00:13.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:14.0 PCI bridge: nVidia Corporation Unknown device 077a (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)

I have started to look at the Bios, but I can seem to find any thing wrong.  It looks like everyone has gotten this to work.  This is my second Abit AN78GS mainboard.  Thought the HDMI was not working somehow.  When I read the manual, it sais that to get HDMI working on Windows you need to activate the HDMI Sound, is there a configuration like this in linux?

---

### Post by xc3RnbFO8P on 2008-07-18
177 is a beta driver, and hopefully the audio will work.
It seems that 177 is the only driver that will support 8200.
Here is 3 useful links:
[http://albertomilone.com/wordpress/?p=212]("http://albertomilone.com/wordpress/?p=212")
[http://ubuntuforums.org/showthread.php?t=822315&page=2]("http://ubuntuforums.org/showthread.php?t=822315&page=2")
[http://www.nvnews.net/vbulletin/showthread.php?t=97993&page=3]("http://www.nvnews.net/vbulletin/showthread.php?t=97993&page=3")

---

### Post by dan9186 on 2008-07-18
Yeah I was reading another forum a little while back and came across the 177 driver.  I tried it but to no avail.

---

### Post by rkstech on 2008-07-25
I also had the same problem with the sound thro' HDMI. After some R&D figured out the following.

1. Do what is needed to enable ALSA
2. If using HDMI for audio - then enable the ICxxxx in volume control switches.
1. System->Pref->Sessions->Startup Programs - Disable the pulseaudio related process.
2. System->Pref->Sessions->Startup Programs - add a new one with command "killall pulseaudio"
4. Had to choose a default sound from System->Preferences->Default Sound.
Select HDMI.
This generates a file under a hidden dir (forgot the path/name)
5. System->Pref->Sound choose the audio over HDMI.

Now at this point u will not still hear the audio with the test button.
Might be because of this bug. The file I had mentioned generated un the hidden folder for default sound has the device id incorrect. In my case the the HDMI audio device number was #3 (alsa -l). So I had to manually fix this.

Once I did this the sound test works and all the sound is now directed thro HDMI.

May be this is a bug or may be I am not doing it correctly. But it works for me.

The file to modify with the device id is ~/.asound.asound.conf

The line I changed for HDMI audio to work is

defaults.pcm.device 3

It was 1 when saved GUI saves this file.

---

