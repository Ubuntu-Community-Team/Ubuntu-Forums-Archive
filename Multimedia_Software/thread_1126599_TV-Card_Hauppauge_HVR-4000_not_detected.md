---
title: "TV-Card Hauppauge HVR-4000 not detected?"
date: 2009-04-15
forum: Multimedia Software
---

### Post by alphanimal on 2009-04-15
Hi!

I have an HVR-4000 Video Card plugged in to my PCI, which works on Windows 7 after installing drivers.

With Ubuntu 7.10 it doesn't seem to find that device!
I read somewhere on the web that it should be fully supported by 7.10

How can I check if the device is installed properly and how could I track down the problem?

All I've noticed so far ist that Klear won't start, saying 
```
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
opening frontend failed: No such file or directory
```

and I dont seem to have /dev/dvb
```
$ cd /dev/dvb
bash: cd: /dev/dvb: No such file or directory
```

thx!
Daniel

---

### Post by alphanimal on 2009-04-16
I installed Me-TV and it says I haven't got a receiving device ...

from [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000):
> It is supported under Linux since kernel 2.6.28. 

I have Ubuntu 8.10
```
$ uname -r
2.6.27-11-generic
```

does that mean I have an older kernel version than the minimum to support my TV card?

That's strange because I installed the latest Ubuntu version 2 days ago.
And the HVR-4000 is out for a while.

Is support for that card yet to come or am I missing something else?

Daniel

---

### Post by Macintosh SE on 2009-04-16
FYI: /dev/dvb would be a file. You cannot cd (change directory) into a file. I have no knowledge of digital TV tuners but to test my analog tuner I do the following:
```
totem /dev/video0
```

This displays the video feed from Channel 3.

If /dev/dvb is the digital equivalent, you could try replacing video0 in the above command with dvb, just to see if the drivers are already installed. If not, you will likely have to find and install drivers.

---

### Post by alphanimal on 2009-04-17
HELO

Thanks for your reply!

actually I have /dev/video0, and it's a file

Since Klear tries to access /dev/dvb/adapter0/frontend0 I think /dev/dvb should be a directory!

I also have no file called /dev/dvb

totem /dev/video0 gives me an error message like "Could not determine type of data stream." (Translated from German)

I could not find a driver anywhere on the web. All I found was that the card should be supported with kernel 2.6.28.

I have ubuntu kernel 2.6.27-11
Is it the latest one? I couldnt find newer ones with apt, using

```
$ apt-cache search kernel-image
comedi-source - Comedi kernel module source
kernel-package - Programm für das Generieren von Linuxkernel-Debianpaketen
```

My question again: Is there a way to get the 2.6.28 (or later) kernel?
I think there were drivers available before that kernel was released, but they became useless because a new kernel implemented them? (Most of the links I found were leading to pages with 404 not found errors and things like that.

thxalot!
Daniel

---

### Post by xc3RnbFO8P on 2009-04-17
> My question again: Is there a way to get the 2.6.28 (or later) kernel?
You can install Jaunuty Beta or wait for the final release (12 days ?)

---

