---
title: "Hammerfall DSP 9632 Sound Card"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by John E on 2007-02-07
Yesterday, I posted this question in the "hardware & laptops" forum - but today I realised that this is the right forum for sound card questions. Maybe someone can tell me how to delete my other thread? Anyway, here's my question....

I just bought an RME manufactured sound card, called the "Hammerfall DSP 9632". Ubuntu's Device Manager seems to have found the card but I don't know where to get the driver or how to install it. The install CD (as usual) comes with only Windows drivers. I tried RME's web site but it only seems to offer drivers for Windows & OSX.

However, quite a few people assured me that Linux drivers are readily available for my new card. Is this something I can download with apt-get install? If so, how would I find out what command to type?

---

### Post by John E on 2007-02-07
Incidentally, I've already tried [these instructions]("http://www.ubuntuforums.org/showthread.php?t=205449") but they didn't work for me.

---

### Post by John E on 2007-02-07
According to someone who supposedly knows about these things, I need to install an application called 'hdspmixer' instead of the standard 'alsamixer'. I tried typing **sudo apt-get-install hdspmixer** but I got a message saying that the package couldn't be found.

Anyone know what I need to do to obtain **hdspmixer**?

---

### Post by John E on 2007-02-08
It seems like there aren't many sound card experts on this forum... :( Anyway, I managed to find and install the hdspmixer - in fact, it's the very same application that came with my Windows driver. Now when I play a sound, I can see it on playback channels 1&2 but I still can't hear anything.

On the Windows version, the sound appears on those playback channels - but also on output channels 1&2 and finally, on the main master output. This isn't happening under Ubuntu. It's as if the mixer isn't routing the sound anywhere. I've tried playing with mutes & solos but nothing produces any sound.

I was assured that this card is simplicity to set up - but it isn't. It seems to be just as troublesome as my old sound card which I eventually gave up on. Could anyone hazard a guess at what the next stage might be?

---

### Post by John E on 2007-02-09
AAARGHH...!

Would you believe it... this has turned out to be a known problem with the latest firmware for this card!!!

For anyone else who encounters this problem, you need to _downgrade_ your firmware to the [previous version]("http://www.rme-audio.de/download/treiber_archiv/fut_win_dsp.zip"). You then need to re-install the Windows driver (if you're dual booting into Windows) making sure that you use the driver supplied on your CD ROM. Card will then work correctly under both Windows & Linux.

---

### Post by neomad on 2007-05-21
Ok amazing, thank you. I will not downgrade my drivers because I will not discard all optmisations and improvements made in RME in last 2 years to run Ubuntu Studio.

If you know somebody running Ubuntu Studio or 7.04 with last RME Firmware just let me know ;)

Regards !

---

