---
title: "No sound after fresh install - sound card not recognised?"
date: 2006-02-14
forum: Multimedia &amp; Video
---

### Post by gingermark on 2006-02-14
Hi there,

I have an ASRock 939NF4G-SATA2 motherboard. Its onboard sound is described by ASRock as being "Realtek ALC850 7.1channel AC'97 audio codec".

After a fresh install of Kubuntu Breezy, I have no sound. KMix has no mixer listed in the drop-down box, which makes me think the sound card was not detected.

Previous installs of Breezy (with different hardware) have never had a problem before, so I have no clue how to approach this.

Any help would be most appreciated - I need my music! :-D 

Best regards,
gingermark.

EDIT: I typed "lspci" in Konsole, and got the following output:
> 0000:00:00.0 RAM memory: nVidia Corporation: Unknown device 02f1 (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation: Unknown device 02fa (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation: Unknown device 02fe (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 02f8 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation: Unknown device 02f9 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation: Unknown device 02ff (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation: Unknown device 027f (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation: Unknown device 027e (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation: Unknown device 02fc (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation: Unknown device 02fd (rev a1)
0000:00:04.0 PCI bridge: nVidia Corporation: Unknown device 02fb (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation: Unknown device 0242 (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation: Unknown device 0270 (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation: Unknown device 0261 (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation: Unknown device 0264 (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation: Unknown device 026d (rev a2)
0000:00:0b.1 USB Controller: nVidia Corporation: Unknown device 026e (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation: Unknown device 0265 (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation: Unknown device 0266 (rev a1)
0000:00:10.0 PCI bridge: nVidia Corporation: Unknown device 026f (rev a2)
0000:00:10.2 Multimedia audio controller: nVidia Corporation: Unknown device 026b (rev a2)
0000:00:14.0 Bridge: nVidia Corporation: Unknown device 0269 (rev a1)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:04:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Oh, and when I typed 'alsamixer' in Konsole I got:
> alsamixer: function snd_ctl_open failed for default: No such file or directory

Hopefully some of that might help.

---

### Post by gingermark on 2006-02-15
I noticed my Southbridge was an nForce 410MC, so installed the official nForce drivers. So now KMix seems to recognise something. Still no sound though, and I'm not sure if the drivers are just confusing my system into partly believing it recognises the sound card.

Please help.

---

### Post by gingermark on 2006-02-15
More information:

I checked out the "sound" section in KInfoCenter and it states that my Audio Devices, Synth Devices, Timers and Mixers are all "Not enabled in Config".

Any idea which file I would have to edit in order to enable them?

It says I am currently using the 3.8.1a-980706 (ALSA v1.0.9 emulation code) Sound Driver.

If anyone needs any further information in order to help I'll only be too happy to provide it. I just really need to get this working - it's driving me mad!

---

### Post by gingermark on 2006-02-15
SOLVED:

I was actually pretty close, the key was to change the Sound System's audio device to Open Sound System (OSS). Unfortunately, I had reinstalled stuff for other reasons, so had to begin again.

Basically, for anyone who cares, I grabbed the nForce driver I needed from [here](http://www.nvidia.com/object/linux_nforce_1.0-0310.html) then used [this thread]("http://ubuntuforums.org/showthread.php?t=75074") to obtain the additional packages I needed (so Method 2, steps 2, 4 to 9) and then did
```
CC=gcc-3.4
export CC
```
and then did ```
sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run
```
and then followed the instructions in [this thread](http://ubuntuforums.org/showthread.php?t=96370) regarding nvmixer and OSS.

Hello multimedia! :D

---

