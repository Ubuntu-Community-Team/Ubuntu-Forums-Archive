---
title: "Nvidia / AC'97 5.1 sound not working"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by TheShocker on 2007-12-13
Hello,

First off, sorry if this has been covered. I did some searching and wasn't able to find any solutions for my specific configuration. I made a thread in beginners forum without any results.

I have an AMD 64 X2 4200+ with an nForce4 motherboard which has Nvidia / AC'97 sound built in to the board. 5.1 works fine with XP. But with Ubuntu 7.10 64 bit, I only have 2.1 sound. I've tried fooling with alsamixer. No luck there.

Someone suggested this: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). So I did what it suggested:

```
sudo nano /etc/modprobe.d/alsa-base
```

and adding this as the last line:

```
"options snd-intel8x0 ac97_quirk=3"
```

(I did not include the quotes.) Still no 5.1.


Any help would be greatly appreciated. Thanks!


```
sudo lshw -C sound
  *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
```

---

### Post by TheShocker on 2007-12-14
Hmm. After doing a restart, now I have no sound whatsoever. Just a clicking noise. Any sound experts out there? Anyone who has gotten sound to work with this set-up?

Thanks

---

### Post by arman.haghi on 2008-02-09
One *Possible* Solution:

I have the same hardware (Abit Mobo with CK804 / AC'97 audio) and had the same problem; After ensuring Kubuntu was [_[COLOR="Blue"]recognising my hardware[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=205449") etc I kept searching for 'software' answers, but it turned out to be a hardware issue all along.

I was modding my box and had removed the front panel audio connections from my mobo. Having no connectors, I've learnt, disables the back panel audio unless you use jumpers across 5/6 and 9/10. Also, ensure that onboard sound is enabled (or auto) in your BIOS menu.

i.e.

If pins are

[FONT="Courier New"]: : : ' :[/FONT]

aka

[FONT="Courier New"]2  4  6  8  10
1  3  5     9 [/FONT]

then jumpers should be placed across 5/6 and 9/10

so

[FONT="Courier New"]: : | ' |[/FONT]

aka

[FONT="Courier New"]2  4  |  8  |
1  3  |     |[/FONT]


Hope this helps,

Arman.

NOTE: Check your motherboard manual first, hardware may vary.

My manual (ala example above) was at
[http://file.abit.com.tw/pub/download/manual/english/kn8-sli.zip]("http://file.abit.com.tw/pub/download/manual/english/kn8-sli.zip")

Solution Source
[http://forums.fedoraforum.org/showthread.php?t=171686]("http://forums.fedoraforum.org/showthread.php?t=171686")

---

