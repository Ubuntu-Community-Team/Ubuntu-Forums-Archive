---
title: "Wireless Connection Stopped Working"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by Readyt on 2010-04-08
I have ubuntu 9.10 and my wireless connection has been working perfectly until a few weeks ago when I updated my laptop. I can connect to the internet using my wired cable but not by wireless. There is nothing listed under my wireless list. I am new to this and have been unsuccessful in getting my wireless connection going again. I don't even know were to begin. I have a 2wire modem also. Any help will be greatly appreciated.
 
Thank you in advance

---

### Post by Tilex on 2010-04-08
Can you tell us what your Wireless card is ?  You can copy/paste the output of the command: lsmod ?

---

### Post by Readyt on 2010-04-08
Thanks for the reply The output is:

tammy@tammy-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
arc4                    1660  0 
ecb                     2524  0 
lib80211_crypt_wep      3708  0 
joydev                 10240  0 
pcmcia                 36808  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
iptable_filter          3100  0 
ppdev                   6688  0 
ipw2100                70672  0 
libipw                 43148  1 ipw2100
lib80211                6432  2 lib80211_crypt_wep,libipw
yenta_socket           24296  4 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables

---

