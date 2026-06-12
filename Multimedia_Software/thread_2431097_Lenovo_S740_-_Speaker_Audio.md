---
title: "Lenovo S740 - Speaker Audio"
date: 2019-11-11
forum: Multimedia Software
---

### Post by hartland08 on 2019-11-11
Hi All,

I recently purchased a **Lenovo IdeaPad s740** and installed Ubuntu on it without issue. However, for whatever reason the only thing that seems not to be working is the speaker output. The computer plays audio through the headphone jack without issues. I've gone through a list of audio troubleshooting steps, but nothing has seemed to work. Not sure if the drivers are setup wrong with the speakers as the computer just came out and all?

I have also tried updating to kernel 5.3.10, but no luck. 

```
Audio:     Device-1: Intel Cannon Lake PCH cAVS vendor: Lenovo driver: snd_soc_skl v: kernel 
           bus ID: 00:1f.3 chip ID: 8086:a348 
           Sound Server: ALSA v: k5.3.10-050310-generic 
```

---

### Post by mörgæs on 2019-11-12
A question like this has better chances of finding an answer in the multimedia forum.

If you click 'report' you can ask a moderator to move it.

---

### Post by jeremy31 on 2019-11-12
Moved to multimedia

---

### Post by hartland08 on 2019-11-15
Anyone know if HDA Analyzer would be of help? The project seems abandoned and was curious to test some things out. Tried messing around with HDAJackRetask to no avail.

[https://www.alsa-project.org/wiki/HDA_Analyzer](https://www.alsa-project.org/wiki/HDA_Analyzer)

---

### Post by paapu on 2019-12-22
Same problem here (Lenovo S740-15IRH), ubuntu 19.10

---

### Post by paapu on 2019-12-25
I reported this at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1857552](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1857552)

---

