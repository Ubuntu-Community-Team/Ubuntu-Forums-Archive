---
title: "Analog Tuner Problems with HVR 3000"
date: 2008-05-23
forum: Mythbuntu
---

### Post by jawadde on 2008-05-23
Hi,

I have a weird problem with a 8.04 mythbuntu system.
I have 2 tuner cards in my system:

1 Hauppauge HVR3000 (Analog + DVB-S & DVB-T)
1 Medion SAA7134 Analaog Card

Everything seems to work fine, except for the following:

When I tune to a channel on the Medion card, I get Picture + Audio, when I tune the same (analog) channel on the Hauppauge card I get "snow". The realy weird thing is that this is only happening on some channels, and not all of them.

Also, when switching from one channel to another on the Hauuppauge card, I sometimes loose the sound (being replaced with noise). after switching back and forth a couple of times to other channels on the Hauppauge card, sound comes back on that specific channel. 

I do not have any trouble with the Medion card, there all channels tune and give correct audio. 

It feels like the Hauppauge card has trouble tuning certain frequencies correctly.

Has anybody experienced this behaviour as well ?

Would welcome any suggestion to get to the bottom of this.

Thanks,

Jawadde.

---

### Post by axelsvag on 2008-05-24
It is a long shot but can there be a problem with hauppage and 8.04. If you look at my problem with pvr500 it looks a little bit the same 

[http://ubuntuforums.org/showthread.php?t=803217]("http://ubuntuforums.org/showthread.php?t=803217") 

I tried maybe 15 times that afternoon to get things to work. But as I said it is a long shot.

---

### Post by jawadde on 2008-05-24
Hi,

Thank you for this hint. Unfortunately, changing the frequencies to channels doesn't make any difference for me. Problem remains. 

I did however make some progress...

In my opinion, the problem is caused by the order in which drivers are loaded. 

I unloaded the tuner, SAA7134 and CX88 related modules and manully loaded them in the right order. Now the problem is gone.

So, what I think is happening is that the tuner module is loaded inbetween the SAA7134 and CX88 modules. This seems to cause a problem for the CX88 modules which are loaded last. 

Anybody any idea how I can force the tuner module to be loaded after all the card drivers have been loaded ?

Thanks,

Jawadde.

---

### Post by jtsop on 2008-08-18
which is the right order?

---

### Post by nicola76b on 2008-11-11
Hi. I have the same card and no signal. The only error in dmesg seems:
```
[ 1254.277816] cx22702_readreg: readreg error (ret == -121)
[ 1254.279483] cx22702_writereg: writereg error (reg == 0x0d, val == 0x00, ret == -121)
```
should it be the right order the one reported here?
[http://www.i-owns-u.net/~ryan/Hauppauge_WinTV-HVR-3000.html](http://www.i-owns-u.net/~ryan/Hauppauge_WinTV-HVR-3000.html)

Any tips for my problem?
Best regards, 
  -nicola

---

