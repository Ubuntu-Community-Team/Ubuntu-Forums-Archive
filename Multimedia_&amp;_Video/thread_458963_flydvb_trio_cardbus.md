---
title: "flydvb trio cardbus"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by segalion on 2007-05-30
I'm in trouble with a flydvb trio cardbus card (DVB-T DVB-S and analog in one) and fresh Feisty (i386 generic) on an HP Pavilion DV8000z

Finally I´ve configured the card for dvb-t and dvb-s (Very well  with Kaffeine)

Instructions for people with this card and Feisty...
_______________________
 I had to append 
"option saa7134 card=84 tuner=54"
and 
"option saa7134-dvb use_frontend=1" (i.o. to use sat frontend instead of the terrestial default)
 to /etc/modprobe.d/options file
and usually I have to force to load the dvb module (sudo modprobe saa7134-dvb)
_______________________

and now my problem is the tunning/scanning of the low frequencies (LNB universal and Astra19,2 ). LOF2 works perfect, but I cant scan transponders above 11600 (switch signal). Thats those of LOF1.

"scan" manually (from dvb-utils) gives the same results... (not able to tuning low transponders).

Same config work fine in windows (progdvb and skyview).

Any can help? Someone of video4linux team?

Thanks in advance...

Segalion

---

### Post by segalion on 2007-11-06
My dvd-t.sh / dvb-s.sh config file to set the frontend manually:

```

#bin/sh
sudo rmmod saa7134_alsa
sudo rmmod saa7134_dvb
sudo rmmod saa7134
sudo pccardctl eject
sudo pccardctl insert
sleep 2
#frontend=0->dvb-t       frontend=1-> dvb-s
sudo modprobe saa7134-dvb use_frontend=0

```

---

### Post by AikBay on 2007-12-17
Hello Segalion.
I found your aportacion very interesting and I was very helpful.
But now I have the same problem as you, it is not tune in the low transponder, has succeeded in resolving it?
Thanks and greetings.

AikBay

P.D: Si quieres lo tratamos en el idioma de Cervantes...

---

### Post by segalion on 2008-01-09
I´ve solved the problem changing sat from astra to hispasat so I dont need this frequencies. This is not a good solution, so maybe I will try with kernel from gutsy release (recently upgraded).

Certainly I have sat-tv forgotten due to recent black sky in our country ;) you know...

---

### Post by segalion on 2008-01-12
Seems that the tuner problem is NOT solved with Gutsy default kernel:

Scanned in Astra 19,2 with Kaffeine and this dvb transponder file:

# Astra 1E,1F,1G,1H,1KR,2C
# Last check and/or update 16 Apr 2007
#
# freq pol sr fec
#
S 10772000 H 22000000 5/6
S 10788000 V 22000000 5/6
S 10818000 V 22000000 5/6
S 10832000 H 22000000 5/6
S 10847000 V 22000000 5/6
S 10862000 H 22000000 5/6
S 10876000 V 22000000 5/6
S 10921000 H 22000000 5/6
S 10979000 V 22000000 5/6
S 11038000 V 22000000 5/6
S 11097000 V 22000000 5/6
S 11156000 V 22000000 5/6
S 11318000 V 22000000 5/6
S 11436000 V 22000000 
S 11479000 V 22000000 5/6
S 11509000 V 22000000 5/6
S 11538000 V 22000000 5/6
S 11568000 V 22000000 5/6
S 11597000 V 22000000 5/6
S 11671000 H 22000000 5/6
S 11686000 V 22000000 5/6
S 11720000 H 27500000 5/6
S 11739000 V 27500000 5/6
S 11758000 H 27500000 1/2
S 11778000 V 27500000 3/4
S 11798000 H 27500000 3/4
S 11817000 V 27500000 3/4
S 11836000 H 27500000 3/4
S 11856000 V 27500000 3/4
S 11876000 H 27500000 3/4
S 11895000 V 27500000 3/4
S 11914000 H 27500000 
S 11934000 V 27500000 3/4
S 11954000 H 27500000 3/4
S 11973000 V 27500000 3/4
S 11992000 H 27500000 3/4
S 12012000 V 27500000 3/4
S 12032000 H 27500000 3/4
S 12051000 V 27500000 3/4
S 12070000 H 27500000 3/4
S 12090000 V 27500000 
S 12110000 H 27500000 3/4
S 12129000 V 27500000 3/4
S 12148000 H 27500000 3/4
S 12168000 V 27500000 3/4
S 12188000 H 27500000 3/4
S 12207000 V 27500000 3/4
S 12226000 H 27500000 3/4
S 12246000 V 27500000 3/4
S 12266000 H 27500000 3/4
S 12285000 V 27500000 3/4
S 12304000 H 27500000 3/4
S 12324000 V 27500000 3/4
S 12344000 H 27500000 3/4
S 12363000 V 27500000 3/4
S 12382000 H 27500000 3/4
S 12402000 V 27500000 3/4
S 12422000 H 27500000 3/4
S 12441000 V 27500000 
S 12460000 H 27500000 3/4
S 12480000 V 27500000 3/4
S 12515000 H 22000000 5/6
S 12522000 V 22000000 2/3
S 12545000 H 22000000 
S 12552000 V 22000000 5/6
S 12574000 H 22000000 5/6
S 12581000 V 22000000 5/6
S 12604000 H 22000000 5/6
S 12610000 V 22000000 5/6
S 12633000 H 22000000 5/6
S 12640000 V 22000000 5/6
S 12663000 H 22000000 5/6
S 12670000 V 22000000 5/6
S 12692000 H 22000000 5/6
S 12722000 H 22000000 2/3
S 12728000 V 19890000 3/4
S 12729000 V 19895000 3/4


D+ Channels like Taquillas dont apear (supposed in first transponders)...
 

Now, only need test diSEqC (two or more antennas, and rotor).
Remote infrared seems not to work yet (I have read something in v2l forums and kernel info)

---

### Post by segalion on 2008-06-24
Tuner problem SOLVED with Hardy kernel.

Thanks a lot.

---

