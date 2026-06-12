---
title: "MythTv backend setup problem"
date: 2008-12-19
forum: Multimedia Software
---

### Post by jacopsd on 2008-12-19
Hi,

I have an Hauppauge PVR-350 card and installed MythTV on my ubuntu 8.10 using Synaptic. 

When I run the mythtv backend setup my screen immediately corrupts (full screen). I have to restart gdm to get out of this situation.

My user name is in the mythtv group already.

More info:
davy@PIV-linux:~$ grep -i auppauge /var/log/messages
Dec 19 08:18:34 PIV-linux kernel: [   19.215699] ivtv0: Autodetected Hauppauge card (cx23415 based)
Dec 19 08:18:34 PIV-linux kernel: [   19.269396] tveeprom 0-0050: Hauppauge model 48134, rev J342, serial# 7067233
Dec 19 08:18:34 PIV-linux kernel: [   19.269435] ivtv0: Autodetected Hauppauge WinTV PVR-350
Dec 19 08:18:34 PIV-linux kernel: [   20.369156] ivtv0: Initialized card #0: Hauppauge WinTV PVR-350

I was looking on several places for help, but could not find a similar post.

Any idea hot to resolve this?

Thx a lot for your help!
Davy
:guitar:

---

