---
title: "Problems with ubuntu discover"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by Optimist on 2006-06-05
HEllo all,

first I'd like to say that I'm quite enthousiastic with ubuntu, and in particular, with the supported hardware for my rather oldfashioned laptop (Acer travelmate 722TX):

- it took me less then 15 min. to install my  wlan card (MA521)
- it took me again less then 15 min. to install my Windows Network (!) printer (Lexmark) X1140.

Compared with my further linux installation (SuSE 6.4), it's almost sort of a miracle how smoothly this is running nowadays.

But I've got serious problems getting my sound card to work. I've got this infamous NM2200 from NeoMagic. I've found out that I need to switch on ISAPnP, which I've done now. After that, the card is not recognized by the 'discover' process, but at least I can load the modules manually, using a startup script to configure the ISAPnP-card (isapnp) and doing the modprobe ad1848, opl3 etc. The modules are loaded, and I can see them running in lsmod. Now the problem is, that this 'discover' startup scheme always detects the PCI chipset and loads the corresponding driver module. The correct driver module is the ad1848, which is an OSS driver only, no ALSA, i. e. the soundcore being used is 'sound', and not 'snd'. Therefore 'discover' loads the 'nm256_sound' module. 

This seems to irritate the following setup, since e. g. ac97 and the ac97_codec are using the faulty nm256_sound module only,but not the correct ad1848/opl3 drivers.

How can I keep the 'discover' process from loading the faulty nm256_sound driver and linking the correct ad1848/opl3 drivers to ac97, the sound mixer etc?

Thanks in advance for your efforts, and, P.S.: I'm using breezy badger, not dapper drake, but couldn't find the the corresponding subforum. 

Optimist

---

