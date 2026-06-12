---
title: "Hvr1600 Mythbuntu 8.1 no chan's on dvb scan"
date: 2008-10-07
forum: Mythbuntu
---

### Post by geowtx on 2008-10-07
Hvr1600 came up and running on new install of Mythbuntu 8.1. Analog tuner has no problems recording, playback, or sound. When I attempt to scan dvb no channels are found on my Cableone cable. I have scanned all US-center-frequency modulation schemes. No channels were returned.

geo@geo-desktop:~$ ls -l /dev/dvb/adapter0
total 0
crw-rw----+ 1 root video 212, 4 2008-10-07 18:47 demux0
crw-rw----+ 1 root video 212, 5 2008-10-07 18:47 dvr0
crw-rw----+ 1 root video 212, 3 2008-10-07 18:47 frontend0
crw-rw----+ 1 root video 212, 7 2008-10-07 18:47 net0


My understanding is that if I have the above response that the drivers are installed and communicating with the card properly.

I am sure I am overlooking something simple. Anyone with working channel.conf for Cableone I would appreciate your help, and any help with what I am missing is welcome.

Mythbuntu 8.1
athalon xp 2000+
.7 gb ram
ati 8500 running vesa driver for now

---

### Post by dibuntux on 2008-10-09
I - I can scan preset freqs for channels, but I'm not getting all the networks I used to get on 8.04 - Got problems since 8.04.1
The network I need it is found and all channels found using the scan command in dvb-t utils, but cannot import the channels.conf!
Even in VLC. I can select the network I need, but only some channels works, other do not.

My config:
Mythbuntu 8.10beta1
Athlon XP 1700+ 512 MB
Nvidia 5200
Hauppauge HVR1100
Technisat SkyStar 2.6 (btw, dvb-s is OK!)

Thank you for reading this...

---

