---
title: "Tunning issues on new install"
date: 2009-05-17
forum: Mythbuntu
---

### Post by kgross on 2009-05-17
I have had a working fedora system for years.  Until today that is.  Had a problem upgrading, so I decided to move the main backend to a mythbuntu setup.  

System has worked fine under fedora 8 for a long time.  Asus motherboard, don't have model handy, with built in nvidia 7150 video, pvr 500 and avermedia A180 digital card.  After I got the system up and running the tuner cards will not work correctly.  A180 can not find any channels when doing a scan, even though many channels worked fine yesterday under fedora.  PVR 500, low numbered channels come in, but very poorly, after you get past about channel 12 or so you can't get anything.


Install was very simple, setup system as master backend/frontend (ended up having to reformate and lost old database :(.  All three tuners are seen in mythtv-setup, just can't tune properly for standard analog US cable and QAM digital cable.

Any suggestions or questions.  

Thanks

Kim

---

### Post by klc5555 on 2009-05-17
> **kgross said:**
> I have had a working fedora system for years.  Until today that is.  Had a problem upgrading, so I decided to move the main backend to a mythbuntu setup.  

System has worked fine under fedora 8 for a long time.  Asus motherboard, don't have model handy, with built in nvidia 7150 video, pvr 500 and avermedia A180 digital card.  After I got the system up and running the tuner cards will not work correctly.  A180 can not find any channels when doing a scan, even though many channels worked fine yesterday under fedora.  PVR 500, low numbered channels come in, but very poorly, after you get past about channel 12 or so you can't get anything.


Install was very simple, setup system as master backend/frontend (ended up having to reformate and lost old database :(.  All three tuners are seen in mythtv-setup, just can't tune properly for standard analog US cable and QAM digital cable.

Any suggestions or questions.  

Thanks

Kim

Re. the A180: there is a wiki guide at: [http://www.mythtv.org/wiki/AVerTV_HD_A180](http://www.mythtv.org/wiki/AVerTV_HD_A180)

Check whether the firmware for the card has loaded by: dmesg | grep nxt

If no nxt2004 firmware is loading, you will likely need to install it as the wiki guide specifies.

Check whether the saa7134 module for the A180 has been loading somehow-or-other by dmesg | grep saa    

If the dmesg output indicates that the module has set up a /dev/video0 (or 1 or 2) for the card, then the module is certainly loading incorrectly, and thinks your A180 is analog rather than digital. In practice, the Phillips tuner cards are almost never properly detected nor is their saa713x module properly loaded by a default "modprobe". Try unloading and reloading the driver as follows:

sudo rmmod saa7134-dvb
sudo rmmod saa7134

The dvb has to be unloaded first, then the plain saa7134. And now:

sudo modprobe saa7134 card=75 tuner=68 disable_ir=1

If the module loads, try scanning with the card. If you're successful scanning, locking, tuning, etc.; the way to ensure the module loads the needed way at bootup is not through an /etc/modprobe.d/options.conf file, which seems to be cheerfully ignored by the module, but rather by blacklisting the module, and then putting the modprobe command you used to manually load the module into the /etc/rc.local file.

Re. the 500: the card may function as a v4l analog card, but make sure you have it/them set up in the backend as a mpeg2 decoder. Also, if the A180 has been mis-loading its saa7134 driver as an analog /dev/videoX, this plays hob with _real_ analog device you may have, including the 500.

Good luck.

---

