---
title: "Laptop headhpone jack"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by CharlieM on 2006-09-17
I have an Acer Travelmate 270 laptop with Dapper on it. Alsa audio works fine accept as soon a pair of headphones is pugged in all audio stops. The socket its self works fine in windows. When you only just plug in the headphones you can hear it out the internal speakers and the headphones. As soon as it pushed in proply all sound stops. 

I have done a bit of reading about the problem. Apprently many drivers have faulty Jack Sense so overiding it in the Alsa mixer solves the issue. Unfortunatly my dirvers don't present a Jack Sense option. There is nothing headphone or line out related in the mixer.

I have tried updating the installed Alsa drivers. Although I can't be confident its using the ones I compiled (any one know how to tell the version that is loaded). I followed this procedure:
[http://alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+PCI+X+%28Dell+OEM%29.&chip=SB0200&module=emu10k1x](http://alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+PCI+X+%28Dell+OEM%29.&chip=SB0200&module=emu10k1x)

What should I try next. I want to hook my laptop up to my HiFi, but I want to use MythTv so I have to use linux either way.

The laptop uses the fairly common Realtek ALC202 chipset for audio.

Charlie

---

### Post by saracen on 2007-04-02
I'm having the exact same problem with Feisty.  Can anyone shed some light on this?  I noticed that the snd_intel8x0 module is being loaded for sound - is that the right driver?

---

### Post by saracen on 2007-04-22
anyone?

---

### Post by Mujaheiden on 2007-06-05
same here; an acer travelmate 273XC with feisty and

```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Acer Incorporated [ALI] Unknown device 001a
        Flags: bus master, medium devsel, latency 173, IRQ 5
        I/O ports at 8800 [size=256]
        I/O ports at 9080 [size=128]
        Capabilities: <access denied>
```

---

### Post by CharlieM on 2008-02-02
I am still having the same problems as before. This seems to effect all versions of Ubuntu right through to Gutsy.

It also effects fedora as well so its clearly an ALSA problem rather than an Ubuntu specific one. I did read someone claiming it used to work on an earlier version of Ubuntu (4. some thing I think they said) apparently.

I did open a ticket in launchpad about it, but it got closed due to lack of activity. 

Did anyone else ever find a solution?

Charlie M

---

### Post by myddewji13 on 2008-02-07
I have the exact same prob...so if anyone finds out ans...pls help!!!!

---

