---
title: "[SOLVED] Beginner. No sound in lenovo n200 on 8.04 lts"
date: 2008-06-27
forum: Multimedia Software
---

### Post by sarthorks on 2008-06-27
Hello, I am extremely new to linux.
i have installed hardy heron (8.04 lts)
on my lenovo n200 notebook.

specs are: 1.66 GHz, Intel Core 2 Duo T5450, L2 Cache Size 2 MB, fsb 667 MHz
i am single booting to ubuntu.
I have ALC861VD audio chipset.

aplay -l gives
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0

and

lspci -v gives

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Lenovo Unknown device 384e
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at fc300000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

(for audio)

I dont find drivers for ICH8 [here:http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")


Please help me!

---

### Post by satish.bty on 2008-06-30
same problem with same configuration with me also do you got some help?

---

### Post by FlyingWV on 2008-06-30
Take this advice with a grain of salt, mind you, because I am new as well.

But if the issue is that ALSA does not have an adequate, or any, driver for your sound card, this solution may very well work for you. 

From checking the supported devices list of OSS 4.0 (An alternative to ALSA) your device (or at least it's family) is supported.

hdaudio	pci8086,2668	Intel High Definition Audio (ICH6)
hdaudio	pci8086,27d8	Intel High Definition Audio (ICH7)
hdaudio	pci8086,269a	Intel High Definition Audio (ESB2)
**hdaudio	pci8086,284b	Intel High Definition Audio (ICH8 )**
hdaudio	pci8086,293e	Intel High Definition Audio (P35)
hdaudio	pci8086,293f	Intel High Definition Audio (ICH9)

So you may want to do what I did and try switching to OSS, I had to as well because my sound card was not supported well by ALSA (Creative X-Fi).

To implement this switch, use this brilliant How-to by Temüjin, [http://ubuntuforums.org/showthread.php?t=780961]("http://ubuntuforums.org/showthread.php?t=780961") Post #2

I hope it helps, and sorry for the long windedness.

---

### Post by sarthorks on 2008-06-30
Hey my sound's now working all right.
All I had to do was to add this line at the end of this file:
/etc/modprobe.d/alsa-base

Add this line:
```
options snd-hda-intel model=lenovo
```

(my notebook is lenovo n200..if yours is some other makers, use:

```
options snd-hda-intel model=auto
```

that should probly work)

Then reboot. If you've made everything full in alsamixer (go to terminal and type ```
alsamixer
``` and make everything full (dont forget to unmute everything using M), when your notebook starts again, you will hear a deafening sound. Go to alsamixer again and adjust the volumes.

You might have a problem saving the alsa-base file after you edit. If it is so (that you dont have the permissions to "write" in that file),
go to terminal and type:
```
  sudo chmod o+w /etc/modprobe.d/alsa-base

```

Then go and edit the file and save the file(over-write),

Later on ,when the sound has started working, you can go to terminal and type
```
 sudo chmod o-w /etc/modprobe.d/alsa-base
```
to make the file "un-writable" again..the original setting.

Hope this helps..its worked for many, should work for you too.

---

### Post by satish.bty on 2008-07-04
i tried this way but noe it says i do not have audio device can you help me?

---

### Post by satish.bty on 2008-07-05
it is sying that i do not have acees to this file and sound spplet on upper panel i do not have sound device

---

### Post by satish.bty on 2008-07-06
dear friend i did as you said .after many tries i got sound.i am the most happy person on earth.thank you very much.

---

### Post by dbuvens on 2008-07-11
super!! adding the line to the file did the trick!!  thanks a lot!!

---

### Post by sarthorks on 2008-07-12
It is my pleasure..even i went through a tough time when i had no sound. :)
I just compiled what all i learned after hours on the forum.

---

### Post by aSmL on 2008-08-22
It works for me to.Thanks and best regards :)

---

### Post by amer-sa on 2008-09-23
it doesn't wokr  for me
i am a noob in ubuntu and Linux altogether.

---

### Post by Quiver on 2008-09-25
Thanks Sarthorks. I also lost sound.  This worked for me too, but I didn't even have to modify the alsa-base file.  alsamixer alone did it.

---

### Post by taco24 on 2008-10-10
Thank you very much. I finally got the sound working.
I changed the following line in the file /etc/modprobe.d/options 

---------------------------------------

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

options snd-hda-intel model=lenovo

---------------------------------
before the model was something else but with model=lenovo it now works.
I also added this line to the file  /etc/modprobe.d/alsa-base 
as mentioned here in previous posts, but I had to change both files and then it finally worked.

---

