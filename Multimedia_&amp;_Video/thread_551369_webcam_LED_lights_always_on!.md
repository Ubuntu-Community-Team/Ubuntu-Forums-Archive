---
title: "webcam LED lights always on?!"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by daimoh on 2007-09-15
I recently plugged my webcam in (a cheap, "Keystone" brand one) and it all works perfectly with the awesome "motion" program (see [http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)).

Unfortunately, my webcam has a ring of white LEDs around the lens, and I can't for the life of me figure out how to turn them off. There's no configuration option in motion, but as that box isn't running xwindows or anything, I need a command-line utility that will turn the LEDs off.

Can anyone recommend something that may do this for me?

Output from dmesg as follows:
[258224.722309] usb 1-1: new full speed USB device using ohci_hcd and address 2
[258224.942850] usb 1-1: configuration #1 chosen from 1 choice
[258225.086795] Linux video capture interface: v2.00
[258225.125448] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX)
[258225.635115] usbcore: registered new interface driver gspca
[258225.635123] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[258225.646639] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.05
[258225.646688] usbcore: registered new interface driver zc0301

---

### Post by Chrissss on 2007-09-20
I know this "problem". One solution would be. Install camstream

sudo apt-get install camstream

and add the line
```
caminfo > /dev/null
```
to the /etc/rc.local (before exit 0).

CU
Christoph

---

### Post by daimoh on 2007-09-20
Thanks Christoph - unfortunately I didn't want to install x11 etc on that box (no room etc.), and camstream seems to require it; apt-get returns:

The following extra packages will be installed:
  defoma fontconfig fontconfig-config libaudio2 libfontconfig1 libfreetype6
  libice6 liblcms1 libmng1 libpng12-0 libqt3-mt libsm6 libx11-6 libx11-data
  libxau6 libxcursor1 libxdmcp6 libxext6 libxfixes3 libxft2 libxi6
  libxinerama1 libxrandr2 libxrender1 libxt6 ttf-dejavu x11-common
Suggested packages:
  defoma-doc psfontmgr x-ttcidfont-conf dfontmgr nas libfreetype6-dev
  liblcms-utils libqt3-mt-psql libqt3-mt-mysql libqt3-mt-odbc
Recommended packages:
  camstream-doc libft-perl libgl1-mesa-glx libgl1 libglu1-mesa libglu1 libxmu6
The following NEW packages will be installed:
  camstream defoma fontconfig fontconfig-config libaudio2 libfontconfig1
  libfreetype6 libice6 liblcms1 libmng1 libpng12-0 libqt3-mt libsm6 libx11-6
  libx11-data libxau6 libxcursor1 libxdmcp6 libxext6 libxfixes3 libxft2 libxi6
  libxinerama1 libxrandr2 libxrender1 libxt6 ttf-dejavu x11-common
0 upgraded, 28 newly installed, 0 to remove and 35 not upgraded.

Is there another similar program that just runs via the command-line? (like motion does)

---

