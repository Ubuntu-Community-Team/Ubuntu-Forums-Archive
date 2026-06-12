---
title: "Frequent crashes: hardware problem?"
date: 2016-01-21
forum: Mythbuntu
---

### Post by Adam_Jacobs on 2016-01-21
In the last few days, my MythTV system has been crashing with alarming frequency. When it crashes, the system is completely unresponsive. I can't do anything with the keyboard, nor can I ssh to it. The only way to reboot is with the power switch.

This feels like a hardware problem. I've noticed the following entries in my syslog:

```
Jan 21 16:13:51 htpc kernel: [   15.653505] nouveau  [  PTHERM][0000:02:00.0] FAN control: none / external
Jan 21 16:13:51 htpc kernel: [   15.653522] nouveau  [  PTHERM][0000:02:00.0] fan management: automatic
Jan 21 16:13:51 htpc kernel: [   15.653526] nouveau  [  PTHERM][0000:02:00.0] internal sensor: yes
Jan 21 16:13:51 htpc kernel: [   15.653538] nouveau  [     CLK][0000:02:00.0] 0f: core 500 MHz shader 1200 MHz 
Jan 21 16:13:51 htpc kernel: [   15.653546] nouveau  [  PTHERM][0000:02:00.0] temperature (87 C) hit the 'fanboost' threshold
Jan 21 16:13:51 htpc kernel: [   15.653558] nouveau  [     CLK][0000:02:00.0] --: core 350 MHz shader 800 MHz vdec 350 MHz

```
Similar things have been popping up quite often since the problem started.

There is nothing that consistently appears in the logs at the point of crashing, though sometimes I get just ^@ repeated many times over, in the syslog, the mythbackend log, and the mythfrontend log.

If something is hitting 87 C that sounds quite hot to me. If I run lm-sensors shortly after booting from cold, I get this:

```
it8718-isa-0290
Adapter: ISA adapter
in0:          +1.07 V  (min =  +0.00 V, max =  +4.08 V)
in1:          +1.94 V  (min =  +0.00 V, max =  +4.08 V)
in2:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in3:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
in4:          +3.06 V  (min =  +0.00 V, max =  +4.08 V)
in5:          +2.99 V  (min =  +0.00 V, max =  +4.08 V)
in6:          +0.10 V  (min =  +0.00 V, max =  +4.08 V)
in7:          +3.10 V  (min =  +0.00 V, max =  +4.08 V)
Vbat:         +3.17 V  
fan1:           0 RPM  (min =    0 RPM)
fan2:         894 RPM  (min =    0 RPM)
temp1:        +30.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:        +34.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp3:        +31.0°C  (low  = +127.0°C, high = +70.0°C)  sensor = thermal diode
cpu0_vid:    +1.250 V
intrusion0:  OK


nouveau-pci-0200
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

```

After a fairly short period of time (maybe just 10 min or so), the last of those temperatures (under PCI adapter) has risen to 80 + C.

The system seems particularly prone to crashing when watching live TV or playing back a recording, but it has also crashed at other times.

Does this sound more like a hardware problem than a software one?

As for software, I'm running MythTV 0.27 on Ubuntu 14.04.

Perhaps more relevantly, the relevant bits of my hardware setup are as follows:

Gigabyte GA-M78SM-S2H motherboard with onboard graphics

TBS6285 TV tuner card

What might it be that's overheating? The sensors output mentions PCI adapter for the bit that's getting hot. That would make the TV tuner card a suspect. I did wonder if it might be something to do with the onboard graphics, given that it's more likely to crash when the graphics is doing something.

I did think that maybe I could try fitting a graphics card, though that's a bit tricky as my motherboard only has 1 PCI-E slot, and that has the TV tuner card in it.

I have checked the case fans and they seem to be working.

Or is the temperature a red herring and something else could be causing the problem?

I'm kind of stumped by this, so any suggestions would be very welcome.

---

### Post by Adam_Jacobs on 2016-01-21
Wait, I stand corrected. I think I do have 2 PCI-E slots after all. One of them is a little mini one (I think it's a x1 slot to be technical), and I think (though I'm not sure without trying) that the TV tuner card will fit in that, so I might be able to try a new graphics card if there's a chance that would solve the problem.

---

### Post by deadflowr on 2016-01-21
Is this what your card is:
[https://www.linuxtv.org/wiki/index.php/TBS6285](https://www.linuxtv.org/wiki/index.php/TBS6285)

If so, then yes, it'll fit in the pci-e x1 slot.

For what it's worth.

---

### Post by Adam_Jacobs on 2016-01-22
Yep, that's my card. So I guess trying a new graphics card would be possible, though I'm not sure I really know at this stage whether it's even worth trying.

---

### Post by Adam_Jacobs on 2016-01-22
OK, I think I've figured this out. It does seem as if it's the motherboard's on-board graphics that was at fault.

As luck would have it, I had a spare graphics card. When I used that, everything seemed to behave itself. Unfortunately there wasn't room for that and the TV tuner card: although I do have 2 PCI-E slots, I have a rather large fanless CPU cooler which encroaches on the space needed for one of them, so I only have one usable one.

But luckily, I had an old PCI TV tuner card, and have reverted to that. I no longer have my HD TV channels, but I can live without that until I get round to buying a new motherboard.

---

### Post by Adam_Jacobs on 2016-01-30
OK, no more crashes since I put in the graphics card, so I'm marking this one as solved.

---

