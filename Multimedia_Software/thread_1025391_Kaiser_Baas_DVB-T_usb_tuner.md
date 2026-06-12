---
title: "Kaiser Baas DVB-T usb tuner"
date: 2008-12-30
forum: Multimedia Software
---

### Post by dobz116 on 2008-12-30
I have a Kaiser Baas DVB-T usb tuner and I need to know how to get it working in Ubuntu Intrepid x64. I have tried Metv and Kaffeine, but they both report that I don't have any DVB-T tuner installed :confused:.  It plays tv fine in Windows Media Center.

Any Ideas?

---

### Post by xc3RnbFO8P on 2008-12-30
In Terminal:
> lsusb
show the output.

---

### Post by dobz116 on 2008-12-30
Here's what it says:

> Bus 002 Device 003: ID 045e:00b4 Microsoft Corp. 
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1164:2edc YUAN High-Tech Development Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by xc3RnbFO8P on 2008-12-30
First try **sudo modprobe dvb-usb-dib0700**
then check dmesg if **dvb-usb-dib0700 fw** is loaded.

---

### Post by dobz116 on 2008-12-30
I ran sudo modprobe dvb-usb-dib0700, then dmesg and did a search for dvb-usb-dib0700 fw but found nothing. Only thing close i found was this:
> 
[  135.464355] ppdev0: registered pardevice
[  135.512035] ppdev0: unregistered pardevice
[  137.299848] ppdev0: registered pardevice
[  137.348245] ppdev0: unregistered pardevice
[  138.554406] ppdev0: registered pardevice
[  138.604431] ppdev0: unregistered pardevice
[  140.685969] dib0700: loaded with support for 7 different device-types
[  140.687751] usbcore: registered new interface driver dvb_usb_dib0700

Metv and Kaffeine still don't detect it.

---

### Post by xc3RnbFO8P on 2008-12-30
Try this:
Start the usb TV in Windows (warm it up)
restart into Ubuntu 
dmesg 
start Kaffeine

---

### Post by dobz116 on 2008-12-30
Kaffeine is still not detecting it. :sad:

---

### Post by xc3RnbFO8P on 2008-12-30
Do this:
> sudo apt-get install build-essential
> sudo apt-get install linux-headers-$(uname -r)
> hg clone [http://linuxtv.org/hg/~pb/v4l-dvb/](http://linuxtv.org/hg/~pb/v4l-dvb/)
> cd /home/your folder/v4l-dvb/
> make
> sudo make install
restart the computer
and try Kaffeine. (show the output of TV part in dmesg)

---

### Post by dobz116 on 2008-12-31
Ran those commands with no errors (already had first two packages installed). dmesg said nothing about my tuner and Kaffiene still doesn't detect the tuner.

After re-running the Kaffiene setup it says:
> DVB-Device...
No DVB-Devices found. The DVB related functions will be hidden.

---

### Post by xc3RnbFO8P on 2008-12-31
Search:
**dvb-usb-dib0700**

---

### Post by hbc on 2009-01-11
I have this same problem.  It seems that the dvb-usb-dib0700 doesnt support product id 1e8c of vendor id 1164 (YUAN Hi-Tech).

I have a Kaiser Baas Dual TV Tuner and the driver seems not to load.  I've done some googling and for some, its as simple as adding the VID and PID in the v4l-dvb and recompile.  But this didnt work for me.  

Can anyone help?

Mark

> **Ringi said:**
> Search:
**dvb-usb-dib0700**

---

### Post by afalout on 2009-07-04
Devin Heitmueller of Kernel Labs is considering writing the driver for analog part of dib0700 devices: 

"Some discussion I have been having with Andrej Falout has prompted me
to consider finally adding analog support for dib0700 based devices?
As a result, I am interested in trying to figure out how many people
care about this.  In particular, this is a rather large project, so I
want to get an idea how many people would actually benefit from this
support (and might be willing to donate a couple of dollars toward the
effort).

I've got all the specs and information required to do the work - it's
just a matter of deciding whether it is worth spending three or four
weeks of my time that could be spent doing stuff that I would almost
certainly consider more interesting.

If you are interested in seeing this work, please reply here, or email
me privately.  Also, include what dib0700 based device you have (and
what video decoder and tuner chips it uses if you happen to know).

--
Devin J. Heitmueller - Kernel Labs
http://www.kernellabs.com"

If you are interestd in this functionality, please let Devin know by sending a message to Linux Media Mailing List :
<linux-media@vger.kernel.org>

---

### Post by jamesawebb on 2009-08-04
I can confirm that adding VID and PID to the appropriate coded v4l-dvb does indeed worked for this product (mine is a Kaiser Baas ExpressCard Dual HD Tuner).  I've submitted patches to the v4l forum but am still waiting for them to go mainstream.

Once this is installed the appropriate firmware should be loaded from /lib/firmware.

The thing that had me stumped for ages is that the numbering of the two adapters presented by the dual card differs from Windows Vista.  I have only one external antenna which seems to work well under Windows Vista.  Under Linux, I need to swap the antenna to the *other* antenna input in order to proceed with tuning.

I've *mostly* got this running under Linux.  Some channels which are available to me under windows is not available under Linux - slightly baffling but I'm certain I'll sort this out shortly.

HTH.  Glad to answer and emails for anyone.

---

