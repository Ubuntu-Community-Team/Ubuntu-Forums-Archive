---
title: "LIRC streamzap"
date: 2007-06-08
forum: Multimedia &amp; Video
---

### Post by isaacb on 2007-06-08
I'm trying to get lirc to work with the streamzap USB reciever.  I've followed the instruction on [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) on built the modules and loaded them.  However when I try to run 'irw' I get immediately returned to the command prompt. All of the modules have loaded i.e lirc_streamzap and lirc_dev with no problems.  I can't figure out what I'm missing.
I'm getting the following message in /var/log/daemon.log

> Jun  9 20:50:48 mythos lircd-0.8.2-CVS[5783]: accepted new client on /dev/lircd
Jun  9 20:50:48 mythos lircd-0.8.2-CVS[5783]: could not open /dev/lirc
Jun  9 20:50:48 mythos lircd-0.8.2-CVS[5783]: default_init(): No such device
Jun  9 20:50:48 mythos lircd-0.8.2-CVS[5783]: caught signal


Thanks,
IB

---

