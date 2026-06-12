---
title: "pulseaudio working but i cannot hear no sound"
date: 2009-05-02
forum: Multimedia Software
---

### Post by joeabiraad on 2009-05-02
Hi

i am having a problem with my sound.
I followed the guide here [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
and it didnt work.
I am on ubuntu 9.04

If i do these steps:
>    1. Close all applications that may be accessing the sound card.
   2. Open the "PulseAudio Device Chooser" from Applications/Sound & Video. Click on the applet icon, and click "Volume Control...". Click on the "Playback" tab.
   3. Launch the application you wish to test and allow it to play sound.
   4. Check PulseAudio Volume Control's Playback tab and see if the application displays an entry while the application is (or should be) playing audio.

I can see that the application does plays audio and does list an entry in the Playback tab.
```

jo@jo-desktop:~$ aplay -l
aplay: device_list:217: no soundcards found...
jo@jo-desktop:~$ 

```
```

jo@jo-desktop:~$ lspci -v > Desktop/lspci-v.txt
jo@jo-desktop:~$ 

```
check attachment for output.

I think i should install a driver for my soundcard... but i dont know which one.
Thanks
Jo

---

### Post by joeabiraad on 2009-05-02
Wootss

After checking my own lspci-v output I found the driver (hopefully) i should install 
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: fast devsel, IRQ 22
	Memory at 93100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: **snd-hda-intel**
```

So what i did is:
```
sudo modprobe snd-hda-intel
```

Now i have:
```
jo@jo-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jo@jo-desktop:~$ 

```

then edited
```
sudo nano /etc/modules
```
and added **snd-hda-intel** at the end of the file. SAVED and RESTARTED

but still when i try to play a video with totem i can see the video but NO SOUND.
All I head is a shushing sound everytime i play music... but not the music itself :S
```
jo@jo-desktop:~$ totem Desktop/s.wmv 
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested

```

Thanks

---

### Post by joeabiraad on 2009-05-02
Problem solved :D

All i had to do is 
```

sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras

```

:)
Jo

---

