---
title: "HDMI-Audio skips"
date: 2012-07-20
forum: Multimedia Software
---

### Post by Zephalon on 2012-07-20
Hi,

im running Ubunutu 12.04 (64bit) on a AMD E450 platform. I´ve installed the latest Catalyst (12.6) to run HD videos.

Now i´ve a problem i just can´t fix... and i tried for hours. The sound skips a second every 5 seconds to 10 minutes. It´s really annoying :(. The picture is flawless.

There´s no difference between MP3 oder (HD) video, also it doesn´t matter what player i use (VLC or XBMC). The system is pretty much stock.

I hope you have any suggestions :/

---

### Post by jmfal on 2012-07-20
Welcome to Ubuntu Forums

What worked for me  was installing ubuntu-restricted-extras,

It's in the software center,synaptic or from the terminal

```
 sudo apt-get install ubuntu-restricted-extras    
```

---

### Post by Zephalon on 2012-07-20
Thanks for the suggestion, but i´ve already installed them. 

There´s no skipping if i use the headphone jack, so the problem must be located somewhere else. Maybe it´s the driver or Pulse Audio... ?

---

### Post by jmfal on 2012-07-20
You can try turning down the s/dif and maybe the pcm if you have one.

---

### Post by jmfal on 2012-07-20
You can try turning down the s/dif and maybe the pcm if you have one.

```
 libdvdcss2  
```

Might help if thats not installed

---

