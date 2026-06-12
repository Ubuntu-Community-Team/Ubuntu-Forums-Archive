---
title: "xorg.conf for DELL U3011/hdmi and hires --- how?"
date: 2013-01-10
forum: Multimedia Software
---

### Post by iaw4 on 2013-01-10
I am trying to connect a new DELL U3011 monitor to a low-end HDMI card.  I have an ultra-speed HDMI cable, so the hardware should be all there.  get-edid produces non-sense output, and asks me to report it to the maintainer.

so, all I am getting now is 1920x1080 on that monitor.  I need to get it to native 2560x1600.  something like

[     5.511] (II) RADEON(0): Modeline "2560x1600"x59.9  268.00  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync (98.5 kHz eP)
[     5.511] (II) RADEON(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz e)

which is what it was for my HP LP3065.  easy, me thinks.  I just need to override what my /var/log/X log tells me,

[     6.141] (II) RADEON(0): EDID vendor "DEL", prod id 16484
[     6.141] (II) RADEON(0): Using EDID range info for horizontal sync
[     6.141] (II) RADEON(0): Using EDID range info for vertical refresh
[     6.141] (II) RADEON(0): Printing DDC gathered Modelines:
[     6.141] (II) RADEON(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz eP)


...except that I do not have an Xorg.conf file in ubuntu 12.10.  how do I tell X to try 2560x1600?

help appreciated.

/iaw

---

### Post by dannyboy79 on 2013-01-10
create the xorg.conf file and add your modeline to it. Are you certain your "low-end HDMI card" can even push that resolution? I understand the monitor can handle it BUT it's up to the card and driver if it can produce that res

---

### Post by iaw4 on 2013-01-10
I did not get far, but I thought I would share for the next sufferer how far I got.  DELL's HDMI EDID seems all screwed up, if only because their name has lost its final L.  grrr....

second, the tool to use under ubuntu is xrandr.  I tried

xrandr --newmode "2560x1600" 268.50  2560 2608 2640 2720  1600 1603 1609 1646 +hsync -vsync
xrandr --addmode HDMI-0 2560x1600

(strangely, I could never get the --device (-d) option work.  has anyone figured out how to use it?)  the above seems to have worked.  and then..

xrandr -s 2560x1600

however, I get corrupted video at this point.  so, it's not working.  maybe DELL is correct in that it does not advertise 2560x1600 via edid over HDMI to clients.  so, new video card for me...

/iaw

---

### Post by dannyboy79 on 2013-01-11
i picked up a Nvidia 8400 GS for only $29.99 from Newegg and am very happy with it. Has HDMI out

---

