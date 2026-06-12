---
title: "How can I install realtek sound driver?"
date: 2008-09-02
forum: Multimedia Software
---

### Post by clapton on 2008-09-02
Hello people!
I buy a board Asus P5K/SE-EPU with Realtek sound (on)board.
becomes with drivers on cd, but on the script execute alsaconf which ubuntu doesn't have!
How can I install drivers? I want to use 5.1 sound system at kubuntu.

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by saltydog on 2008-10-23
Have you tried with the Realtek drivers?
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

---

### Post by markbuntu on 2008-10-23
You can try editing your ~/.asoundrc file like the people in this thread:

[http://ubuntuforums.org/showthread.php?t=899139](http://ubuntuforums.org/showthread.php?t=899139)

---

