---
title: "win vt 1300- cx8800 problem with kernel 2.6.33"
date: 2010-11-04
forum: Multimedia Software
---

### Post by webaake on 2010-11-04
On Karmic with kernel 2.6.33 from Mainline PPA installed from deb packages all modules for cx8800/Haupauge win tv 1300 DVB-T are loading according to dmesg, without errors. lspci is showing the card as well. But Kaffeine and Me-TV doesn't recognize it.

With standard Ubuntu kernel 2.6.31-22-generic #68-Ubuntu the card works really well.

I've tried to google this and someone tried the 2.6.35 kernel without success.

I'm not willing to upgrade to Maverick, but I could compile my own kernel if it is of any use.

Maybe manually install latest v4l drivers? Any suggestions are welcome.

---

### Post by webaake on 2010-11-05
Seems like I fixed it by installing latest v4l-dvb drivers. and hacking the code for HVR 1300. Got it from here;
[https://bugs.launchpad.net/mythtv/+bug/439163](https://bugs.launchpad.net/mythtv/+bug/439163)

---

