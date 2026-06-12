---
title: "ATI HDTV Wonder lock, no channels"
date: 2009-12-01
forum: Mythbuntu
---

### Post by C_Oblender on 2009-12-01
This has me scratching my head. I have An ATI tuner card and have already downloaed the updated firmware for it. Scanned for channels and only had one lock with 2 channels. Other channels had a lock but no channels.  From what I could see this shouldn't have happened.  Because of the observed siginal strength.

Ch. 15     Siginal strength 64%    S/N 36%    Lock, No Channels
Ch. 17     Signal strength 55%    S/N 35%    Lock, No Channels
Ch. 42     Signal strength 52%    S/N 35%    Lock, 2 Possible Channels

The worse part about the channel that I am getting is that it is the Baptist rant station.  The real anti-thought, anti-evolution Baptist rant station.

---

### Post by blackoper on 2009-12-01
I ran a channel scan with an ati hdtv wonder this weekend and it found all the channels. I followed an old thread I posted in about it but had no issues once I loaded the right firmware.


All you need to do is get the firmware:

sudo aptitude install linux-source
cd /usr/src
sudo tar xvjf linux-source-[INSERT YOUR KERNEL HERE- just do an ls].tar.bz2
cd linux-source-[INSERT YOUR KERNEL VERSION]/Documentation/dvb
sudo perl get_dvb_firmware nxt2004
sudo cp dvb-fe-nxt2004.fw /lib/firmware/


then add 
cx88-dvb
 to the /etc/modules file as it's own line and that worked for me after reboot or a depmod -a

---

### Post by C_Oblender on 2009-12-01
Thanks for the reply.  Unfortunately I had already ran into that problem and updated the firmware.

---

### Post by blackoper on 2009-12-01
which of the two coax inputs do you have the cable in? It should be the one closest to the middle of the card (away from the edge) for qam tuning

---

### Post by C_Oblender on 2009-12-01
Sorry I should have specified that this was ATSC tuning.  Plus Time Warner over here seems to think that you should pay extra for digital basic cable.

---

### Post by Senkoboy on 2009-12-01
You need a better antenna, Google DIY 4 bay antenna. I am picking up stations 65+ miles with mine.

My ATI card shows a higher signal strength than my Gov. Tuner Box or my TV, with the same antenna.  They all pick up the same channels, just show different signal strengths.

---

