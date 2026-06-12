---
title: "DVB card &quot;Phillips Semiconductors SAA7146&quot; not detected"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by andybalaam on 2006-09-28
Hi All,

I'm trying to use a Hauppauge Nova-T digital TV card here in the UK, under Ubuntu Edgy Eft.

The /dev/video0 device is not present, and there is no info about this card in the output of dmesg.

Any help anyone can give me would be greatly appreciated.

Info:

andy@systemax:~$ lspci | grep Multimedia\ controller
00:07.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)

andy@systemax:~$ dmesg | grep DVB

andy@systemax:~$ uname -r
2.6.17-7-generic

andy@systemax:~$ ls /dev/vid*
ls: /dev/vid*: No such file or directory

Thanks very much,

Andy

---

