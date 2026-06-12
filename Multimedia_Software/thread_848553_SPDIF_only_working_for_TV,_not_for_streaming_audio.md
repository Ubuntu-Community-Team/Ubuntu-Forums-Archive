---
title: "SPDIF only working for TV, not for streaming audio/video, MP3's, etc."
date: 2008-07-03
forum: Multimedia Software
---

### Post by Bigfork on 2008-07-03
Strange problem here.  I have a 8.04 running with the latest MythTV version and I only have sound when using live TV or watching my recorded shows.  All other sound i.e. streaming radio, YouTube, etc. will not output to the SPDIF.  It does go to the analog jacks but my Myth box is in the basement and the only audio output I have to the entertainment center is via coax from the SPDIF connection.  I had it working 3 weeks ago and all of a sudden it stopped.  Not sure what I did.  All sound out of the SPDIF does work in XP so I know it's just a config issue somewhere in Ubuntu.  It's an Nvidia nForce 630/7150 chipset.  

So how do I get all audio to output through the SPDIF?  How can I reinstall just the audio drivers?  Also, I have checked to see nothing is muted in alsamixer and aplay-l gets me:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Thanks,
Tony

---

### Post by Bigfork on 2008-07-09
Any ideas?  I've been hitting my head against this wall for over a month now.  I think I'll try buying a dedicated sound card and try that :/

---

### Post by Trollslayer on 2008-07-13
This is a recurring problem with Linux.
Does [COLOR="Blue"]aplay -L[/COLOR] show IEC958? 
Also, have a look at [http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound](http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound)

---

### Post by Bigfork on 2008-07-13
> **Trollslayer said:**
> Does [COLOR="Blue"]aplay -L[/COLOR] show IEC958?

Nope, aplay -l gets me what I posted above still.  How would I add this?

Thanks,
Tony

---

### Post by Bigfork on 2008-07-13
Also, when running alsamixer the IEC958 channel doesn't have a volume bar.  It's unmuted but I have no way to change the level.

Tony

---

### Post by yuqin513 on 2008-07-13
[www.Jordan9.com](www.Jordan9.com) discount cheap nike jordan gucci prada shoes lacoste puma trainers at china factory 
Welcome to visit [www.jordan9.com,We](www.jordan9.com,We) are a professional shoes and sneaker Industrialcompany, and as af([www.jordan9.com](www.jordan9.com)) amous nike shoes factory & Stores and wholesale company.([www.google.com](www.google.com)) air force one

---

### Post by Bigfork on 2008-07-13
> **Trollslayer said:**
> Does [COLOR="Blue"]aplay -L[/COLOR] show IEC958?

Ah, sorry, didn't realize there was a difference between aplay -l and -L.  Here is what I get with aplay -L:
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


Tony

---

### Post by Bigfork on 2008-07-13
> **Bigfork said:**
> Also, when running alsamixer the IEC958 channel doesn't have a volume bar.  It's unmuted but I have no way to change the level.

Here's a screen shot:

[IMG]http://www.pbase.com/bigfork/image/100089891/medium.jpg[/IMG]

Tony

---

### Post by Bigfork on 2008-07-13
Does it matter that my /proc/asound/card0/codec#0 file is empty?  Shouldn't it be ALC888 (for my hardware at least)?

Thanks,
Tony

---

### Post by Bigfork on 2008-07-13
Double post.

---

### Post by Trollslayer on 2008-07-17
See below for a thread about hardware configureation, it solved my problem:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

