---
title: "Yet Another tv / dvb-t problem."
date: 2008-08-12
forum: Multimedia Software
---

### Post by Ubuntaqua on 2008-08-12
Dear all,

I'm trying to get a Pinnacle PCTV Hybrid pro pci working on my Hardy desktop. (Athlon 3500+ with 1go RAM and an ATI x1950 pro graphics). from what i've gathered, the chipset is a 310i.

What works :
- The dvb-t card is recognised directly out of the box and driver is loaded (seems ok). Dmesg, lsmod & all return something very pleasant.
- Thus, the card is also recognised ok by Me-tv and Kaffeine (it is even picked up by Skype as a video grabber)

What don't work:
1 - Searching for channels on both apps (Me-tv and Kaffeine) returne nothing : the dvb-t scanner fails to tune properly to the channels. I tried to feed it about all combination of offsets available corresponding to my location (XXX MHz + n  *166KHz, n = -1, 0, 1, 2, 3) but still, no tune lock (or no luck, as you wish).


I've updated the firmware in /lib/firmware (shouldn't be necessary as the card is recognised) and then put the original one in place, and Hardy is supposed to have it working out of the box.


2 - Trying to use the "normal" TV tunner on tvtime returns the  following error :
```
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/xavier/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: http://gatos.souceforge.net/
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces
```
I suspect this is due to the ATI card i'm using (reading forums and all) so here's what I'v tried:
a - radeon driver with/without Xgl installed
b - fglrx driver with/without Xgl installed and with/without the following options :
- Run in the command line before restarting X```
sudo aticonfig --overlay-type=Xv
```
- and options in xorg.conf (should be equivalent to the above)
```
Option  "VideoOverlay" "on"
 Option  "OpenGLOverlay"  "off"

```

Am I missing anything very obvious here or is there some mysterious how-to that I overlooked ?

Many thanks for any help.

---

