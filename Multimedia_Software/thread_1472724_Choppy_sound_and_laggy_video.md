---
title: "Choppy sound and laggy video"
date: 2010-05-04
forum: Multimedia Software
---

### Post by Swinger7714 on 2010-05-04
Hello folks

I installed Ubuntu today. After installing the restricted package, I noticed that sound is not working by default. After randomly tweaking the sound options (seriously I have no idea what I did), I somehow got it to work, though very poorly. Sound is all choppy and glitchy, and the video freezes for a second now and there when playing.

Since I am a beginner with Linux, I continued to toy with the options, trying to get the problem fixed, but without success.

My sound device is: Intel 82801FB ICH6 - High Definition Audio Controller. Sound and video is working fine when loading WinXP.

Some more data about my system that will hopefuly help:

[IMG]http://i41.tinypic.com/23tf3eu.jpg[/IMG]

---

### Post by Swinger7714 on 2010-05-05
:(

---

### Post by lidex on 2010-05-06
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Swinger7714 on 2010-05-06
Thank you for your reply, here is the output you requested

```
Linux sergey-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Advanced Linux Sound Architecture Driver Version 1.0.21.

Codec: Realtek ALC880
```



>  Also helpful is the make/model of your PC/Laptop. 

I am not sure what do you mean by make/model... Do you mean the year i bought my PC? If so, It was  2005, five years ago exactly. If you mean the specific hardware i got, then i'v already posted it.

---

### Post by lidex on 2010-05-06
> **Swinger7714 said:**
> 
I am not sure what do you mean by make/model... Do you mean the year i bought my PC? If so, It was  2005, five years ago exactly. If you mean the specific hardware i got, then i'v already posted it.

No, manufacturer and model no. I don't see that anywhere.

---

### Post by Swinger7714 on 2010-05-06
Sorry, I still dont get it. There is no specific manufacturer or model number. Its not a Dell or HP premade computer. Its just a regular PC I ordered from the local computers shop, with hardware I chose myself , and they put it together in a nice box with lights for me in the shop.

---

### Post by lidex on 2010-05-06
Ahh...gotcha. Can you give me a count of the analog audio jacks?
And digital, separately?

---

### Post by Swinger7714 on 2010-05-06
> **lidex said:**
> Ahh...gotcha. Can you give me a count of the analog audio jacks?
And digital, separately?

Its pretty standart. Three jacks in rear. Green for out put, pink for Microphone, and a blue one for i dont know what. Two more jacks in front, one green one pink.

No digital jacks that i know of.

---

### Post by lidex on 2010-05-06
Are you using the nvidia-current driver? Also how many memory sticks are installed?

Edit: according to intel website the correct codec is ALC860. You should probably update the bios as this is an old board. Also states: > Desktop boards D915PCY and D915PCM support dual or single channel memory configurations
defined in Table 6.
Table 6.
Desktop Board D915PCY/D915PCM Memory Configurations
Memory Speed Processor FSB Frequency (MHz) Memory Speed Outcome (MHz)
DDR2 533 Pentium 4 processor 800 533
533 533
DDR2 400 Pentium 4 processor 800 400
533 400

Intel Desktop Board D915PGN/D915PSY/D915PCY/D915PCM Product Guide
Four 240-pin Double Data Rate 2 (DDR2) SDRAM Dual Inline Memory Module (DIMMs)
connectors with gold-plated contacts.
&#8226; Support for:
Unbuffered, non-registered single or double-sided DIMMs
Serial Presence Detect (SPD) memory only
Non-ECC RAM
1.8 V memory
Memory configuration listed below:
&#8226; Up to 4.0 GB utilizing 512 Mb or 1 GB technology
&#8226; Up to 2.0 GB utilizing 256 Mb technology

What is the output of:
```
sudo lspci -nn | grep VGA
lsmod | grep snd
```

Product page:
[http://www.intel.com/p/en_US/support/highlights/dsktpboards/d915pcy]("http://www.intel.com/p/en_US/support/highlights/dsktpboards/d915pcy")

---

### Post by Swinger7714 on 2010-05-06
Yes i am using the Nvidia current driver.

I have one memory stick with 1G on it.

```

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV37GL [Quadro FX 330/GeForce PCX 5300] [10de:00fc] (rev a2)

```


Maybe if i install Ubuntu with Wubi rather then dual boot, the problem will solve it self? is it possible?

p.s I really rather not mess with the Bios.

edit: I have a friend who got the same problem when using Win7. He says it happens when his CPU usage goes high. Maybe Ubuntu doesn't devote enough CPU power to the sound devices when needed. Its just an hypothesis.

---

### Post by lidex on 2010-05-06
How about:
```
lsmod | grep snd
```

---

### Post by Swinger7714 on 2010-05-07
Hi, sorry it took me so long, I removed Ubuntu from dualboot and reinstalled it with wubi, but the problem is still the same. Here is the output you requested:

```
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm

```

---

### Post by Swinger7714 on 2010-05-08
Up up

---

### Post by oxman on 2012-05-22
Same issue. Any help is greatly appriciated.

12.04 clean install

---

