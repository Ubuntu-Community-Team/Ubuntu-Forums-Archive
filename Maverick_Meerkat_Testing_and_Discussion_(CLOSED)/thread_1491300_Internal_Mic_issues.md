---
title: "Internal Mic issues"
date: 2010-05-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by vikrant82 on 2010-05-23
Hello guys,

I seem to be having problems with internal mic, in maverick. The external mic works fine. This is an hp laptop.

```
sudo lshw -class multimedia
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:30 memory:e4804000-e4807fff
```

I have made sure nothing's muted etc.

---

### Post by zaphod777 on 2010-05-24
take a look at this thread this is how I fixed it.

[http://ubuntuforums.org/showthread.php?t=1466096](http://ubuntuforums.org/showthread.php?t=1466096)

---

### Post by topcoder on 2010-05-24
Am on a Compaq CQ45 laptop. Same issues here. Internal mic worked well with Karmic, which used ALSA. Now with Pulseaudio, the internal mic is not even seen.

---

### Post by vikrant82 on 2010-05-24
> **zaphod777 said:**
> take a look at this thread this is how I fixed it.


Thanks, but it doesn't help. It was working fine on default configurations but probably got broken on some maverick updates.

> Am on a Compaq CQ45 laptop. Same issues here. Internal mic worked well with Karmic, which used ALSA. Now with Pulseaudio, the internal mic is not even seen.

topcoder, yours is a different issue altogether, I can see my mic. It worked perfectly for me on lucid. Did you try basic troubleshooting like ones here : [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

By the way I raised a bug for my issue:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/584670](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/584670)

---

### Post by vikrant82 on 2010-05-25
Guess what! It doesn't work in windows as well :-) Have asked for HP service, since the laptop is in HP care plan.

It was funny explaining him that the mic actually broken. At first I didnt want to tell him that I dual boot with Ubuntu, so I had comply whatever stupid troubleshooting he asked me to. Driver updates, system restore etc. 

Finally when I got bugged up, I told him that Boss, it stopped working, in another OS, Linux installed on the system.

So pooor guy, finally comes up - "Sir, we don't advise installing Linux on same system with windows, as this messes up with the drivers." :) 

Anyways, I finally managed to get myself an onsite engineer visit. These customer care guys can be tricky. :)

---

