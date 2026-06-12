---
title: "No Sound with Intel G45"
date: 2010-05-23
forum: Multimedia Software
---

### Post by dustin0 on 2010-05-23
I just got Ubuntu 10.04 installed and I seem to be having a problem as many others with the sound. Any advice because a laptop with no sound tends to be a wee bit boring :P

```

dustin@dustin-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

[IMG]http://uppix.net/9/d/7/f6dcb0289481d1a61ae8da276bbe2.png[/IMG]

[IMG]http://uppix.net/6/2/e/35284d9cf1cec26ac7ea14ddadd24.png[/IMG]

---

### Post by lidex on 2010-05-23
So you're trying to get surround out through the spdif connector, is that correct? If you want your laptop speakers to work, you'll need to use the other soundcard and select stereo-duplex.

---

### Post by dustin0 on 2010-05-23
> **lidex said:**
> So you're trying to get surround out through the spdif connector, is that correct? If you want your laptop speakers to work, you'll need to use the other soundcard and select stereo-duplex.

Im not sure what the first part is. Im just trying to get my laptop to emit sound. I did change it to the Stereo-duplex and still no sound. When I plug my headphones in you can barely hear the sound and my volume is at max.

---

### Post by lidex on 2010-05-23
In alsamixer, press F6 and select this soundcard> ALC269


Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by dustin0 on 2010-05-23
When I do the F6 in alsamixer I only get a HDA Intel option to show up. However when selected it shows the following
[IMG]http://uppix.net/5/0/3/8398ada81be8aba67019d3ceabcaf.png[/IMG]

```
dustin@dustin-laptop:~$ uname -a
Linux dustin-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux

```

```

dustin@dustin-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
dustin@dustin-laptop:~$ 

```

```

dustin@dustin-laptop:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX
dustin@dustin-laptop:~$ 

```

The laptop is a Sony Vaio model # VPCEM11FM

```

dustin@dustin-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dustin@dustin-laptop:~$ 

```

---

### Post by lidex on 2010-05-23
Try updating alsa to 1.0.23 via the alsa-upgrade link in my sig.

---

### Post by dustin0 on 2010-05-23
> **lidex said:**
> Try updating alsa to 1.0.23 via the alsa-upgrade link in my sig.

You sir are amazing
that script did it
:):KS:guitar:

---

### Post by ElSupra on 2012-07-21
The ALSA Upgrade works !!
Thank you !!!:popcorn:

---

### Post by wildmanne39 on 2012-07-21
Old thread closed.

---

