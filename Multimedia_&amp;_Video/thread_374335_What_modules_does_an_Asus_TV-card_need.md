---
title: "What modules does an Asus TV-card need?"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by mojoman on 2007-03-02
Hi, 

I just bought a TV-card, Asus My Cinema P7131 Dual, for my computer that's running on 64-bit Dapper.

lspci gives the following output:
```
0000:01:07.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev d1)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 4876
        Flags: bus master, medium devsel, latency 32, IRQ 106
        Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <available only to root>
```

So, I guess the card is detected and identified correctly. I have no idea if the correct modules are loaded in the kernel but this is how my etc/modules look like:
```

lp
psmouse
rtc

```

I suspect that this the problem (I've read that the module bttv should be loaded as well). Do I need to kompile a new kernel for this?

Thankful for any and all help
/Mojoman

---

### Post by david_2001 on 2007-03-02
If you're lucky, the card should have been recognised and the saa7134 kernel modules loaded automatically.  You could just try a TV viewer to see whether it's working or, if you want to be a little more scientific, try the following at a command prompt:
```
dmesg | less
```
You need to look for something like:
> saa7133[2]: subsystem: 1043:4876, board: ASUSTeK P7131 Dual [card=78,autodetected]
saa7133[0]: board init: gpio is 0
tuner 0-004b: chip found @ 0x96 (saa7133[0])
tuner 0-004b: setting tuner address to 61
tuner 0-004b: type set to tda8290+75a
in the dmesg output.

---

### Post by mojoman on 2007-03-02
> **david_2001 said:**
> If you're lucky, the card should have been recognised and the saa7134 kernel modules loaded automatically.  You could just try a TV viewer to see whether it's working or, if you want to be a little more scientific, try the following at a command prompt:
```
dmesg | less
```
You need to look for something like:

in the dmesg output.

Thanks for the help. I should have written that TvTime just gives me a black screen. However, I tried dmesg | grep saa7134 and it gave the following output.
```
[   45.402240] saa7133[0]: found at 0000:01:07.0, rev: 209, irq: 106, latency: 32, mmio: 0xfdeff000
[   45.402246] saa7133[0]: subsystem: 1043:4876, board: UNKNOWN/GENERIC [card=0,autodetected]
[   45.402255] saa7133[0]: board init: gpio is 40000
[   45.544708] saa7133[0]: i2c eeprom 00: 43 10 76 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   45.544717] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   45.544723] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d5 ff ff ff ff
[   45.544729] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.544735] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 55 50 ff ff ff ff ff ff
[   45.544741] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.544747] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.544753] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.544956] saa7133[0]: registered device video0 [v4l2]
[   45.544977] saa7133[0]: registered device vbi0
[   45.561958] saa7133[0]/alsa: saa7133[0] at 0xfdeff000 irq 106 registered as card -1

```

Does this mean that the correct modules loaded? And should I edit /etc/modules in any way?

/Mojoman

---

### Post by david_2001 on 2007-03-02
The recommended way of specifying module load options is to put them in a file under /etc/modprobe.d.  In this case, create a file in /etc/modprobe.d/ called "saa7134" containing:
```
options saa7134 card=78
```
then restart and check the dmesg output again.

---

### Post by mojoman on 2007-03-03
David_2001: Alright! Things are moving in the right direction. :) 

Before I got your tip I had tried this link:

[https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)

However, ivtv-utils have no istallation candidate (though the other packages installed just fine) and this didn't help at all.

Your tip made the difference, the card is now up and running though I get "no signal". I can scan for channals but I can't find any. However, this is just a configuration issue, it might be that it's searching for digital channels and right now I only got analog (but this is due to change in Stockholm in just a week or so as the analog net is about to be closed down). 

Anyway, thanks a bunch for the help, I'll get on with the nitty-gritty configuration now :) 

Best regards
/Mojoman

---

### Post by superm1 on 2007-03-05
> **mojoman said:**
> David_2001: Alright! Things are moving in the right direction. :) 

Before I got your tip I had tried this link:

[https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)

However, ivtv-utils have no istallation candidate (though the other packages installed just fine) and this didn't help at all.

Your tip made the difference, the card is now up and running though I get "no signal". I can scan for channals but I can't find any. However, this is just a configuration issue, it might be that it's searching for digital channels and right now I only got analog (but this is due to change in Stockholm in just a week or so as the analog net is about to be closed down). 

Anyway, thanks a bunch for the help, I'll get on with the nitty-gritty configuration now :) 

Best regards
/Mojoman
ivtv-utils *is* on that repository, I just installed it.  A bit odd you didn't see the package.

---

### Post by mojoman on 2007-03-05
> **superm1 said:**
> ivtv-utils *is* on that repository, I just installed it.  A bit odd you didn't see the package.

Really?

mojoman@home:~$ sudo apt-get install ivtv-utils
Password:
Reading package lists... Done
Building dependency tree... Done
Package ivtv-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ivtv-utils has no installation candidate

I'm running 64-bit, could that be it?

/Mojoman

---

### Post by superm1 on 2007-03-05
> **mojoman said:**
> Really?

mojoman@home:~$ sudo apt-get install ivtv-utils
Password:
Reading package lists... Done
Building dependency tree... Done
Package ivtv-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ivtv-utils has no installation candidate

I'm running 64-bit, could that be it?

/Mojoman
Oh you know what, it is quite possible that I forgot to build the 64 bit ivtv-utils :)
I'll build it at home later tonite and get it added. Thanks for the catch!

---

### Post by superm1 on 2007-03-06
Okay - i've updated the ivtv repository.  Hopefully the 64 bit builds should now be available.

---

### Post by mojoman on 2007-03-07
> **superm1 said:**
> Okay - i've updated the ivtv repository.  Hopefully the 64 bit builds should now be available.

It installed just fine! :biggrin:

Thanks!
/Mojoman

---

### Post by david_2001 on 2007-03-07
Why install utilities (ivtv-utils) for a TV card that isn't supported by the ivtv driver (any Asus TV card)?  Is this some sort of coded conversation and I'm not in on the secret :confused:

---

### Post by mojoman on 2007-03-10
> **david_2001 said:**
> Why install utilities (ivtv-utils) for a TV card that isn't supported by the ivtv driver (any Asus TV card)?  Is this some sort of coded conversation and I'm not in on the secret :confused:

To thell you the truth, I wansn't sure wether or not it supported asus (when I googled I encountered some conflicting information on this) and I wanted to give it a try. However, the card is now up and running, though I can't find any channels :( 

/mojoman

---

### Post by mojoman on 2007-03-11
David_2001:  tvtime detects the card but it can't find any channels at all. Also, it doesn't seem to find the tuner (e.g. FM-Radio Tuner doesn't find any channels at all, and it doesn't show up on dmesg). 

Do you have any tips on how to go forward with this?

Best regards
/Mojoman

---

### Post by david_2001 on 2007-03-12
> **mojoman said:**
> David_2001:  tvtime detects the card but it can't find any channels at all. Also, it doesn't seem to find the tuner (e.g. FM-Radio Tuner doesn't find any channels at all, and it doesn't show up on dmesg). 

Do you have any tips on how to go forward with this?

Best regards
/Mojoman

I've done a little research - Google returned much information about this card.  Radio may not work unless you upgrade to a more recent version of the LinuxTV drivers.  (Upgrade to the latest development version of the drivers is normally not particularly difficult to achieve - famous last words, of course, but I have them installed here.)  However, analogue TV should function, given a good signal.  How close is your dmesg output to:
> saa7133[0]: subsystem: 1043:4876, board: ASUSTeK P7131 Dual [card=78,insmod option]
saa7133[0]: board init: gpio is 0
saa7133[0]: i2c eeprom 00: 43 10 76 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d5 ff ff ff ff
saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 55 50 ff ff ff ff ff ff
saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
tuner 0-004b: chip found @ 0x96 (saa7133[0])
tuner 0-004b: setting tuner address to 61
tuner 0-004b: tuner: type set to tda8290+75a
saa7133[0]: registered device video0 [v4l2]
saa7133[0]: registered device vbi0
saa7133[0]: registered device radio0
and what TV standard do you have where you are - there could be a problem with signal offsets.

---

### Post by mojoman on 2007-03-13
Well, dmesg gives this:
```

[   44.928071] saa7133[0]: found at 0000:01:07.0, rev: 209, irq: 106, latency: 32, mmio: 0xfdeff000
[   44.928077] saa7133[0]: subsystem: 1043:4876, board: ASUSTeK P7131 Dual [card=78,insmod option]
[   44.928088] saa7133[0]: board init: gpio is 40000
[   45.064889] saa7133[0]: i2c eeprom 00: 43 10 76 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   45.064898] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   45.064905] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d5 ff ff ff ff
[   45.064911] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.064918] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 55 50 ff ff ff ff ff ff
[   45.064925] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.064931] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.064938] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   45.101965] saa7133[0]: registered device video0 [v4l2]
[   45.102047] saa7133[0]: registered device vbi0
[   45.102141] saa7133[0]: registered device radio0
[   45.119357] saa7133[0]/alsa: saa7133[0] at 0xfdeff000 irq 106 registered as card -1
```

Nothing on the tuner.

I'm in Sweden. TV-standard should be PAL (right?). Stockholm has just the other day switched to digital transmission but it didn't work earlier with analog and it doesn't work now as digital. Anyway, I live in aa apartmet building and as I receive a central signal it is already converted and the change of standard doesn't effect me.

I thankful for any tips you can have on this.

Best regards
/Mojoman

---

