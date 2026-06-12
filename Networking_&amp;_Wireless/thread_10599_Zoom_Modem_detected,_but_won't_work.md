---
title: "Zoom Modem detected, but won't work"
date: 2005-01-09
forum: Networking &amp; Wireless
---

### Post by appleworkitbaby on 2005-01-09
Hello,

I installed Ubuntu on my iMac G3 a few days, and I have to say...Its not half bad...nothing like OS X..but for linux...I was really impressed.

Now, my internal modem blew up a few years ago during a really bad lightning storm. So I now have a Zoom technologies external USB 56K modem. When I went to go set up my dial-up connection on Ubuntu, it for some reason would keep reading my internal modem, and not the external one.
I'm not sure why its doing this considering the Device Manger Reads it (it = the zoom modem).

Is there a file I need to edit, in order to get it to use my external modem, instead of the internal one?

Thanks in advance!
 :D

---

### Post by ynef on 2005-01-10
External modems are not complicated things and they follow a very strict standard (well, most of them do) so you don't need any module for it, except one that enables the COM port. You'll just want to get a dialer program (lots to choose from) and dial your ISP. COM1 under Windows is called /dev/ttyS0 in Linux.

---

