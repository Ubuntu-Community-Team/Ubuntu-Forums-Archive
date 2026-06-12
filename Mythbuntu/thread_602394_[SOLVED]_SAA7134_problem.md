---
title: "[SOLVED] SAA7134 problem"
date: 2007-11-04
forum: Mythbuntu
---

### Post by thusgaard on 2007-11-04
Hi 

I have an ASUS TV-FM7134 card in my windows media center. I desided to run Mythbuntu 7.10 on the mediacenter, reading that the SAA7134 was supported under windows. 

Maybe I'm just stupid, but I can't get it working. 

The card is recocniced by mythbuntu (as far as I can tell) but when I try to tune channels I get an error saying some thing like "could not connect to device". 

Please help. 

As this is a stand alone system that I can easily reinstall we can experiment. 

J;-)

---

### Post by steefjeqv on 2007-11-04
Hello,

Try this in terminal :

sudo modprobe saa7134 

If this doesn't do the trick, you can try :

sudo modprobe saa7134 card=16

Greetings,
Steven

---

### Post by thusgaard on 2007-11-04
Am I to expect any answers from the modprobe?

---

### Post by steefjeqv on 2007-11-04
Hi,

No.

If it doesn't give an error after you've executed this command in terminal, this most likely means that the saa7134 drivers are now loaded.
Do not reboot, because this will unload the drivers !

Greetings,
Steven

---

### Post by thusgaard on 2007-11-04
It still says can not open card. I have tried maunaly setting up a channel. Testing that in a second.

---

### Post by thusgaard on 2007-11-04
No luck all my interfaces is already in use. I think this card may be not very compatible.

---

### Post by reclusivemonkey on 2007-11-04
TVTime can be very helpful in setting up your TV card just to test the card itself without worrying about any MythTV problems. I have a card supported by the saa7134 driver, and I didn't have any channel tuning issues, but MythTV couldn't unmute the card so I use v4lctl to do that.

Just install TVTime, and see how you go on with that.

---

### Post by steefjeqv on 2007-11-04
Hi,

Are you using MythTV to test your card ?

If so, you may try to use Kaffeine (for testing).
It handles DVB cards quite good.

To install it, just type the following in terminal :

sudo apt-get install kaffeine

When you use kaffeine the first time, it will let you know if the TV card is recognized.

Greetings,
Steven

---

### Post by thusgaard on 2007-11-04
> **steefjeqv said:**
> 
If so, you may try to use Kaffeine (for testing).
It handles DVB cards quite good.


The card is not a DVB card

---

### Post by thusgaard on 2007-11-04
did some further research: 

The bttv, saa7134, and cx88 drivers each support a wide variety of cards which all use the same chip. In particular, these cards differ in what tuner they use, how many inputs they have, and how it is configured.

Often, these drivers cannot autodetect the card type, or detect the incorrect card. To debug this, you must watch your kernels logs by running the "dmesg" command, potentially loading and unloading the driver with different options until the driver is successfully loaded.

[   29.982944] tuner 0-0043: chip found @ 0x86 (saa7134[0])
[   29.982975] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   29.998408] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   29.998413] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   29.998446] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   29.998450] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   30.005636] saa7134[0]: registered device video0 [v4l2]
[   30.005674] saa7134[0]: registered device vbi0
[   30.005707] saa7134[0]: registered device radio0
[   30.024063] saa7134 ALSA driver for DMA sound loaded
[   30.024093] saa7134[0]/alsa: saa7134[0] at 0xcffff000 irq 16 registered as card -2

---

### Post by thusgaard on 2007-11-04
The card works with TVtime. But no sound. 

So now I have to find a way to get it working with Myth. 
And then I need to get sound.

---

### Post by thusgaard on 2007-11-04
I now have sound, Thanks to Alsamixer (run from terminal) and I have video. 

All of the above in TVtime. 

So now I need to figure out how to get the same features in Mythtv. Any help will be awarded with lots of thanks and high thoughts. 

;-)

---

### Post by thusgaard on 2007-11-12
I have every thing working now. It's not that hard installing MythBuntu. 

I have some problems that I will ans in other questions. 

J;-)

---

