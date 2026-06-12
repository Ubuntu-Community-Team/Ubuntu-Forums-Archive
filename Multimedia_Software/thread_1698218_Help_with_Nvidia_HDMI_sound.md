---
title: "Help with Nvidia HDMI sound"
date: 2011-03-01
forum: Multimedia Software
---

### Post by jocalafla on 2011-03-01
ASUS N53JQ-A1
Ubuntu 10.10
Intel Core i7-740QM
Nvidia GT425M

```

$ speaker-test -c 2 -r 48000 -D hw:1,7 
$ aplay -D hw:1,7 some_file.wav

```Both of the above work, but otherwise, I get no sound via HDMI. 

```

load-module module-alsa-sink device=hw:1,7
load-module module-alsa-source device=hw:1,7

```I tried loading the lines above into /etc/pulse.d/default.pa w/o success.

I'm lost and bewildered. Can someone help please?

---

### Post by lidex on 2011-03-02
What do you have selected in 'Sound Preferences' on the 'Hardware' tab, both for device and profile? Have you seen this:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)

---

### Post by jocalafla on 2011-03-02
Thanks for the link, that's a lot to absorb. Kernel patches, ugh. 

I have "HDA Nvidia Digital Stereo (HDMI) " as my chosen device and "Digital Stereo (HDMI)" as profile.

---

### Post by lidex on 2011-03-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Yeah, you could learn a lot on that thread. I don't use hdmi so I have to defer to the experts.

---

