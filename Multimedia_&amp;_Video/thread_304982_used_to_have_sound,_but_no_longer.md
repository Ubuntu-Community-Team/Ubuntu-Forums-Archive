---
title: "used to have sound, but no longer"
date: 2006-11-22
forum: Multimedia &amp; Video
---

### Post by linuxted on 2006-11-22
I've almost given up on this, I'm desperate here.  I've tried the "Comprehensive Sound Solution Guide", I 've tried the Ubuntu Edgy known bugs and I've tried using bugzilla (both searching and submitting).  It's been two updates since I've had sound running on this system (yes, the system I am on had sound working with one of the Ubuntu (Dapper?) versions).  And I triple checked that the speakers are on and connected to the audio port.  

While I love Ubuntu, this sticking point is driving me nutso.  ](*,) 

Here's some potentially useful info:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lspci -v 
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems Unknown device 1891
        Flags: bus master, medium devsel, latency 32, IRQ 217
        I/O ports at e000 [size=256]
        I/O ports at e100 [size=128]
        Capabilities: <access denied>

everything appears to be unmuted in alsamixer

Thanks in advance for your help

---

### Post by finferflu on 2006-11-22
Are you by any chance using a laptop?

---

### Post by willca on 2006-11-22
I upgraded from Dapper to Edgy and I also lost my sound. Funny thing is the system still recognizes my audio hw and alsa seem to think its working. But their is nothing coming out of my speakers.

Thinking about getting the latest alsa drivers and load it up from stock.

-W

[http://www.boondoons.com](http://www.boondoons.com)

---

### Post by linuxted on 2006-11-22
> **finferflu said:**
> Are you by any chance using a laptop?

Actually, no it is a desktop computer.


Thanks for taking the time to reply.

linuxted

---

### Post by linuxted on 2006-11-22
> **willca said:**
> I upgraded from Dapper to Edgy and I also lost my sound. Funny thing is the system still recognizes my audio hw and alsa seem to think its working. But their is nothing coming out of my speakers.

Thinking about getting the latest alsa drivers and load it up from stock.

-W

[http://www.boondoons.com](http://www.boondoons.com)

Please let us know how that works for you (and what procedure you used).

Thanks,
linuxted

---

### Post by Bezmotivnik on 2006-11-22
See [this thread]("http://www.ubuntuforums.org/showthread.php?t=304575").

Some "update" helpfully turned off sound.  Alsamixer showed the problem and took care of it.

---

### Post by linuxted on 2006-11-22
> **Bezmotivnik said:**
> See [this thread]("http://www.ubuntuforums.org/showthread.php?t=304575").

Some "update" helpfully turned off sound.  Alsamixer showed the problem and took care of it.

Unfortunately, alsamixer doesn't show an issue (all outputs unmuted and set to ~80%).  I've tried a few permutations with no luck.

:-k

---

### Post by Bezmotivnik on 2006-11-22
> **linuxted said:**
> Unfortunately, alsamixer doesn't show an issue
There's a lot of other things to try in that linked article.

Other than that, I got nothin'.  Sorry.  :(

---

### Post by subspawn on 2006-11-23
Also check this other [thread]("http://www.ubuntuforums.org/showthread.php?t=283610")  where I posted how I fixed my troubles.

---

