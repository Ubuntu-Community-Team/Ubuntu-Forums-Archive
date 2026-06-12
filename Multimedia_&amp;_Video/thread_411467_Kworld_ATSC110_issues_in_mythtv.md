---
title: "Kworld ATSC110 issues in mythtv"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by c3rb3rus on 2007-04-16
Hello,

I just recently put together my first mythtv box and i am having problems in a few areas.  First, here is my system:

cpu: athlon x2 3600+
motherboard: asus m2npv-vm
tuner: kworld atsc-110
ram: 1 gig
hd: 320 gig

I installed ubuntu and mythtv according to the directions located in the guide on this site.  The biggest problem that I am having is that the tuner card does not seem to be working right.  I can tune to some analog stations (2-13) but i get no sound.  I try scanning through qam stations but i cannot get a lock on any, even though the scanning dialog shows ~90+ % signal and 60+% signal to noise.  I've tried looking through other threads, and i thought that i had the card installed correctly, but i guess i was wrong... Can anyone help?

Thanks in advance.

---

### Post by c3rb3rus on 2007-04-17
bump

anyone have any ideas?

---

### Post by biker19 on 2007-04-24
Do you know for sure you have clear QAM chs in your area? The card can find plenty of QAM chs but if they're encrypted it can't display them. Read through the Kworld thread for this card for any other ideas. [http://ubuntuforums.org/showthread.php?t=372635&page=5&highlight=kworld](http://ubuntuforums.org/showthread.php?t=372635&page=5&highlight=kworld)

Do you get sound in Ubuntu itself? The lack of sound may be driver related - nothing to do with this card.

---

### Post by c3rb3rus on 2007-05-01
I'm pretty sure that there are clear QAM channels in the area (i have digital cable from Cablevision in northern NJ).  After my latest scan I finally picked some up some digital channels.  Strangely although many channels were picked up in the scan, only a few picked up names and will actually tune.

As far as the analog channel sound problem, I am trying to get sound without a loopback cable.  I followed the directions at the lnmk here: [http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110](http://www.mythtv.org/wiki/index.php/Kworld_ATSC_110) but they do not seem to work.  I think that i might have the wrong device configured in the mythtv backend or frontend because sound works in gnome.  Here are my current configurations:

Frontend audio config:

Audio output device: ALSA:default
Passthrough device: Default
Mixer Device: default
Mixer Controls: PCM

Backend v4l card config:

video device: /dev/video0
probed info: Kworld ATSC110 [saa7134]
VBI device: /dev/vbi0
Audio device: /dev/dsp
Audio Sampling rate: 32000
Default input: Television


Also, had anyone managed to get lirc working for the ir input on this card?  If so, how?

---

### Post by biker19 on 2007-05-03
The chs that display the station info are the clear QAM chs - all the rest are encrypted.

I think there was a Lirc setup wiki somewhere for the remote that comes with this card. I haven't tried it yet.

---

