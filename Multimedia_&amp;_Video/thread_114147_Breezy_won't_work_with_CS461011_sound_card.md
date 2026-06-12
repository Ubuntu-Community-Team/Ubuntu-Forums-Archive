---
title: "Breezy won't work with CS4610/11 sound card"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by aka_strat on 2006-01-07
Semi-n00b here - third try at Linux.  Stupid stuff like this keeps me from sticking with it.  Hope I can overcome this silly-ass issue (with your help - I am googled out on this one).

Error at boot time:

Sound Fusion CS46xx: probe of 0000:00:0b.0 failed with error -5
ACPI: PCI interrupt for device 0000:00:0b.0 disabled
it is not probably bug, try to use CS4236 driver
create - never read codec ready from AC'97
ACPI: PCI interrupt 0000:00:0b.0[A] -> Link [LNKC]-> GSI 3 (level, low)-> IRQ3

However:

lspci | grep audio
0000:00:0b.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)

Nothing works, though.  The sound icon shows the device is muted.  If I try to turn it on, I get: No volume control elements and / or devices found

Also:

alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

Any suggestions?

Thanks,

Strat

---

### Post by FarEast on 2006-01-08
It may be worth trying this:???: 
```
$ sudo /sbin/modprobe snd-cs4236
```

---

### Post by Wulfrunner on 2006-01-29
I had a similar problem using an IBM 300PL Desktop with an integrated CS4235 sound card. It was not detected or installed automatically by Ubuntu. I solved the problem by using a command similar to the one described by FarEast, but found that I needed to run it every time I restarted the computer. I entered a line into /etc/modules ("snd-cs4236") to get sound working on startup.

---

### Post by Bill Chriss on 2006-05-14
I had the same problem on a 1998 vintage Dell Dimension XPS R450. Just like Wulfrunner, I entered a line into /etc/modules ("snd-cs4236") to get sound working on startup. (No quote marks needed in the file.)

---

### Post by kowal on 2008-05-27
Excelent! Works in Hardy too. Thanks!

---

