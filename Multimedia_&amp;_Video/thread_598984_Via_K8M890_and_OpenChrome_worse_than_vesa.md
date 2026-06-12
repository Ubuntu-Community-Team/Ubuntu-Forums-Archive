---
title: "Via K8M890 and OpenChrome worse than vesa"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by c't00 on 2007-10-31
I have a Shuttle xpc with a Via K8M890 (Chrome9) video chipset that I'm trying to get working under Gutsy.  I'm using the amd64 build.

lspci shows:
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890 [Chrome9] Integrated Video (rev 11)

I tried xserver-xorg-video-via and xserver-xorg-video-openchrome from the repositories, but with both xorg complained "No devices found".

Next I tried building the openchrome driver from svn using instructions at [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome).  I got a driver which loaded, but video performance was much worse than the vesa driver - everything drew very slowly, mpeg video was replaced with green lines, and switching to virtual consoles took several seconds.

Is the Chrome9 driver not ready for prime time yet, or am I just missing something (eg. xorg configuration?)

Thanks in advance for any help!

---

### Post by Yellow Pasque on 2007-10-31
When you tried the packages, did you have a Device section defined in xorg.conf with the driver defied as "via"?

---

### Post by c't00 on 2007-11-01
Yes, for the packages I used "via", the svn build I used "openchrome".

---

### Post by Matataki on 2007-11-07
I have the same problem on my K8M800, VESA is faaaar faster than the openchrome or via drivers.

I have no idea what's up with it either, just chiming in that it's really weird to have my laptop operate better with VESA drivers than drivers tailored for my card.:confused:

---

