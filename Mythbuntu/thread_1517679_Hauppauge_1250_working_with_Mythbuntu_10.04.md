---
title: "Hauppauge 1250 working with Mythbuntu 10.04"
date: 2010-06-25
forum: Mythbuntu
---

### Post by rchille on 2010-06-25
Hello all.

I picked up a PCIe x1 Hauppauge 1250 model 1196 (rev 04) yesterday and have spent the morning getting it up and running. If you get very lucky, you'll not need to do anything, for some it works directly out of the box. 

The degree that you have to play with it seems to be based on what version of the card that you get and how lucky you are with the kernel drives you have. 

There are a coupla good threads already out there:
[http://ubuntuforums.org/showthread.php?t=1308180]("http://ubuntuforums.org/showthread.php?t=1308180")
[http://ubuntuforums.org/showthread.php?t=974366]("http://ubuntuforums.org/showthread.php?t=974366")

The short answer for me was to load the newest v4l-dvb drivers from:
[http://linuxtv.org/hg/v4l-dvb]("http://linuxtv.org/hg/v4l-dvb")
(Download from the bz2/zip/gz links along the left hand side)

And to create the file "/etc/modeprobe.d/cx23885.conf" with the following:
```

options cx23885 card=20 
options CORE_cx23885[0]_dvb adapter_nr=0

```

These should set your card up as a Hauppuage 1255 and configure the digital capture. There seems to be some debate as to wither you should include the 1st line (excluding will allow autodetect which didn't work for me) or what to set it to (3 should be the correct card, but some people get it working with 18 or 20).

There also was not agreement with what steps need to be taken and is which order. I update my drivers first then added the cx23885.conf file so I'm not sure if the updated drivers were required.

Please note: If you do compile your own drivers, there is known bug:
[http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09364.html]("http://www.mail-archive.com/ubuntu-devel-discuss@lists.ubuntu.com/msg09364.html")

I hope this helps someone out there! :p

---

