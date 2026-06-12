---
title: "pchdtv 5500 no analog"
date: 2008-11-26
forum: Mythbuntu
---

### Post by tresero on 2008-11-26
I have read the jumble of suggestions on the internet and can not get analog (i.e. cable) working. 

Most posts suggest using the new drivers from linuxtv.
I did that.

The card works flawlessly for digital, I can test with the unencrypted channels.


They also suggest using dvb and adding the analog portion. This does not work. There is no analog component to dvb.
If I use the analog drivers I get all my channels, but the sound repeats the first second or two getting louder and louder.

I don't have digital cable, nor do I want to upgrade. I only have cable tv since I pay for cable internet. I hope there is a solution for analog and the 5500. This card is supposed to just work, but I have spent 2 weeks trying things. 

I have worked daily as a developer and sysadmin with linux since pre 1.0, yes really, so I am not a newbie, you can discuss options however needed.

---

### Post by klc5555 on 2008-11-26
> **tresero said:**
> I have read the jumble of suggestions on the internet and can not get analog (i.e. cable) working. 

Most posts suggest using the new drivers from linuxtv.
I did that.

The card works flawlessly for digital, I can test with the unencrypted channels.


They also suggest using dvb and adding the analog portion. This does not work. There is no analog component to dvb.
If I use the analog drivers I get all my channels, but the sound repeats the first second or two getting louder and louder.

I don't have digital cable, nor do I want to upgrade. I only have cable tv since I pay for cable internet. I hope there is a solution for analog and the 5500. This card is supposed to just work, but I have spent 2 weeks trying things. 

I have worked daily as a developer and sysadmin with linux since pre 1.0, yes really, so I am not a newbie, you can discuss options however needed.

First of all, I have to offer the opinion, as a long-time pchdtv-5500 user, that the analog half of the 5500 pretty well just sucks.

But anyway, the docs that specify "adding the analog portion" to the DVB refer to how the cards were set up under Mythtv 0.20.2, and do not seem to have been updated for Mythtv 0.21. 

The analog half of the 5500 is set up in Mythtv 0.21 as though it were a separate card (analog, using v4l and outputting to /dev/video0 and audio to /dev/dsp, or /dev/dsp1 or whichever option offered in the dropdown menu works --it may not be the one you'd logically expect. You can't physically type one in yourself, it won't save when you leave the card's setup.) After the analog side of the 5500 is set up as a separate card, it should be placed into the same Recording Group in the backend setup as is the DVB half of the card --this is how Mythtv 0.21 does it so that the Mythtv scheduler doesn't try to record from both sides of the card at the same time.

The audio sampling bitrate in the card's backend setup has to be changed from the default 32k to 48k, to avoid the dreaded "Razzy/Tinny sound" problem. The sampling rate will also have to be changed to 48k in the frontend  setup, under Recording Profiles -- Software Encoders (v4l-based), for Default, LiveTV, High Quality and Low Quality.

And you should be basically ready to go. I suspect your card's problem is that it's dumping audio to the wrong /dev/dsp choice. 

If the analog part of the card starts, LiveTV races for a couple of seconds, stalls for a couple of seconds, races for a couple, etc., with bad color and horrible sound, then you have to restart the card by clicking out of LiveTV and back in. And then, generally, the analog part of the card will settle down and work properly. This race condition of the card makes scheduled recordings with the analog part of the card something of a gamble: if it misfires, your recording will have all the race portions and none of the stalls, so that it runs at about 1.5x normal speed and is unusuable because of sound quality. In LiveTV, you change from the analog part of the card to digital and back by using the "change source input" in the menu ("m" key shortcut).

After the better part of a year screwing around with a couple of these cards, I finally gave up on using them for analog recording at all, and added a couple of Hauppauges to various backends on my system for analog recording use. I do love the 5500s for clear QAM, though.

All the best! :)

---

### Post by tresero on 2008-11-26
Thanks, I thought I was going crazy. I am a command line guy so being stuck in the gui is a little trying. 
I can't afford another card right now, but what exact model are you using? I saw win500 or some such, but I thought that anything win, pretty much didn't work with linux.

Thanks again for the prompt reply.

---

### Post by klc5555 on 2008-11-27
> **tresero said:**
> Thanks, I thought I was going crazy. I am a command line guy so being stuck in the gui is a little trying. 
I can't afford another card right now, but what exact model are you using? I saw win500 or some such, but I thought that anything win, pretty much didn't work with linux.

Thanks again for the prompt reply.

One backend has an old Hauppauge PVR-150 on it, which is flawlessly reliable and takes almost no hardware resources.

When I needed another analog input for recording, I tried to get another 150 or its equivalent (250, 350, 500). Unfortunately, by that time (a couple of months ago) the Analog Police had the pipeline of new analog-only devices pretty well shut down. So I've got a 1600. It has its own driver quirks --the cx18 driver is a cranky beta that has some I2C bus issues and doesn't play completely nicely with NVidia proprietary drivers, but once I finally got the 1600 configured, or at least the analog side of it, it has  worked fine for me as an analog tuner on a remote backend. The 1600 is PCI; its PCI-e equivalent is the 1250.

If you have particular cards you're wondering about, their more-or-less current state of driver support in Mythtv and Linux can be checked via the wiki page: 
[http://mythtv.org/wiki/index.php/Category:Video_capture_cards](http://mythtv.org/wiki/index.php/Category:Video_capture_cards)
which resource is gradually becoming more complete and is generally being kept up-to-date.

All the best!

---

