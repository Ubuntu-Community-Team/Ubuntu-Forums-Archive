---
title: "Dvico TV card"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by bh56 on 2006-10-10
Hi all,
I have a dvico dvb-t plus card TV card. TVtime and xawtv only have composite1 and svideo as input options. Scantv reports that television is an invalid option. From lsmod all the driver modules appear to be in place; the correct /dev entries (/dev/video0 and /dev/vid0) are also there.
The only error I can find is when I run v4l-conf, it reports
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  13
  Current serial number in output stream:  13
I'm using a an Asrock 775VM800 (celeron2.6GHz) board with an nvidia mx440 video card, kernel is 2.6.15-27-686. TV works fine under XP.
Thanks for any suggestions
Brendan

---

