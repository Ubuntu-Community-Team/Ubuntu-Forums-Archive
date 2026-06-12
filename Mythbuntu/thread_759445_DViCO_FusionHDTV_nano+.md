---
title: "DViCO FusionHDTV nano+"
date: 2008-04-19
forum: Mythbuntu
---

### Post by omega-00 on 2008-04-19
Hello All,

Attempting to install a DViCO FusionHDTV Nano+ (USB Device)
Following instructions from [https://help.ubuntu.com/community/DViCO_Dual_Digital_4](https://help.ubuntu.com/community/DViCO_Dual_Digital_4)

I've followed all the way through and 'lsusb' shows up the DVICO usb device, but when I check dmesg there are no references to the dvb device, and if I try to do 

scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Brisbane

I get the following error:
"FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory"

I've checked and there's no actuall /dev/dvb directory at all :confused:

So next up I read over "http://ubuntuforums.org/showthread.php?t=524303"

and tried adding the line cx88_dvb to my /etc/modules file, which just results in dmesg giving a number of dvb errors (I'm guessing this is the wrong module for the usb device.

Any suggestions?

At the moment it doesn't appear to be loading any dvb modules at all on startup.

Regards,
omega-00

---

### Post by wombo on 2008-04-19
I think I saw support added for the nano in the latest kernel (.25) which was released yesterday

---

### Post by omega-00 on 2008-04-20
[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)

Chris had added support for nano a little while ago and I've tried his tree as well, also tried loading different modules to see if it made any difference but with no such luck.

Also just tried on the 8.04rc - finger crossed that it may be in the proper release in 4 days :-/

---

### Post by sunset_studies on 2008-04-25
Any luck with this? I've just upgraded to Hardy and it's not working out of the box as I'd naively hoped.

Edit: from the 2.6.25 Kernel changelog: Add support for MT352-based DViCO FusionHDTV DVB-T NANO devices

Sounds promising. Any Idea when 2.6.25 will be apt-getable in Hardy?

---

### Post by sunset_studies on 2008-04-25
Update: I've got it working. Steps followed:

sudo apt-get install mercurial linux-headers-$(uname -r) build-essential

hg clone [http://linuxtv.org/hg/~pascoe/xc-test/](http://linuxtv.org/hg/~pascoe/xc-test/)
cd xc-test
make
sudo make install
cd /lib/firmware
sudo wget [http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw](http://www.linuxtv.org/downloads/firmware/dvb-usb-bluebird-01.fw)
sudo wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/xc3028-dvico-au-01.fw)
sudo wget [http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/dvb-usb-bluebird-02.fw)
reboot


Mine is a USB 'FusionHDTV DVB-T nano'. Good luck.

---

### Post by omega-00 on 2008-05-01
did you have to add any modules after this at all? 
I've just followed exactly that but it still doesn't show the device being loaded when I do a "dmesg | grep dvb"

It does show up when I "lsusb" thou as DVICO

Running mythbuntu 8.04

---

### Post by tc7 on 2008-05-02
My DVICO / Mythtv config broke when upgrading from Gutsy to Hardy (Ubuntu 8.04).

I got it going for DVICO fusion DVB-T Dual digital 4
Had same problem as Ben ([http://marc.info/?l=linux-video&m=120921103106246&w=2](http://marc.info/?l=linux-video&m=120921103106246&w=2)) with Mythtv recognizing the dual tuners perfectly but doesn't let me scan channels.

I probably need to do an initial scan with "scan", but can't find the tuner file yet.

Works fine with me-tv however.

Found scan file at: /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne
So ran: scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne

Will try Mythtv again later.

---

### Post by sunset_studies on 2008-05-06
I don't remember inserting any modules manually. Here is the dvb related lsmod output when my card is working though:

dvb_usb_cxusb          26756  0 
dvb_usb                22924  1 dvb_usb_cxusb
dvb_core               80124  1 dvb_usb
i2c_core               24832  3 tuner_xc2028,zl10353,dvb_usb
usbcore               146028  5 dvb_usb_cxusb,dvb_usb,ehci_hcd,uhci_hcd

One thing that might be worth a try is having the card inserted at boot up time.

---

### Post by enchesss on 2009-01-31
There is a lot of confusion in this post as to the different DVICO nano+ and normal nano usb tv tuners.


The nano+ (blue case) is not recognised with any of these instructions.

It must use different firmware from the normal nano (white case).

It shows up as DVICO when doing lsusb but

there is nothing in dmesg.


If anyone knows how to get it going then let us know.

---

### Post by Brian McG on 2009-03-28
Have been following this thread for a while now with nothing to contribute - Dvico have informed me that they'll request a linux driver for the nano+ from the chipset manufacturer.

---

### Post by carl_li on 2009-12-27
> **enchesss said:**
> There is a lot of confusion in this post as to the different DVICO nano+ and normal nano usb tv tuners.


The nano+ (blue case) is not recognised with any of these instructions.

It must use different firmware from the normal nano (white case).

It shows up as DVICO when doing lsusb but

there is nothing in dmesg.


If anyone knows how to get it going then let us know.

New here and want to share that the nano+ just will not work. People might think if nano works, then nano+ will but it's not the case. Just want to share my experience. Eventually I gave up and bought a AverMedia Volar X and works beautifully.

---

