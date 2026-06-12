---
title: "DVB-T USB Card Yuan High-Tech Found by OS but not applications"
date: 2017-02-27
forum: Multimedia Software
---

### Post by Walter_ZAMBOTTI on 2017-02-27
$ dmesg | grep dvb
[   18.001933] dvb-usb: found a 'YUAN High-Tech MC770' in cold state, will try to load a firmware
[   18.087584] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   18.792609] dvb-usb: found a 'YUAN High-Tech MC770' in warm state.
[   18.792710] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   19.696780] dvb-usb: schedule remote query interval to 50 msecs.
[   19.696783] dvb-usb: YUAN High-Tech MC770 successfully initialized and connected.
[   19.697080] usbcore: registered new interface driver dvb_usb_dib0700
$ ls -lR /dev/dvb
/dev/dvb:
total 0
drwxr-xr-x 2 root root 120 Feb 27 15:24 adapter0


/dev/dvb/adapter0:
total 0
crw-rw----+ 1 root video 212, 0 Feb 27 15:24 demux0
crw-rw----+ 1 root video 212, 1 Feb 27 15:24 dvr0
crw-rw----+ 1 root video 212, 3 Feb 27 15:24 frontend0
crw-rw----+ 1 root video 212, 2 Feb 27 15:24 net0
$ groups
wallyz adm cdrom sudo dip video plugdev lpadmin sambashare
$ dvbscan /usr/share/dvb/dvb-t/au-Perth >~/.tzap/channelsnew.conf
Failed to open frontend
$

Ubuntu 16.04. (Was working under 14.04)

me-tv and dvbscan fail to find any DVB device?

What should I look at/check next?

---

