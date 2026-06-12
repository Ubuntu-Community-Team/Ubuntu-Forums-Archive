---
title: "ASUS U3000 Hybrid USB Tuner"
date: 2011-08-06
forum: Multimedia Software
---

### Post by juhaszjozsef on 2011-08-06
Hi all!

I've recently purchased an ASUS U3000 Hybrid USB Tuner stick.
According to linuxTV, the device shoul work "out of the box" under Ubuntu 11.04.
I suppose it does:
It identifies itself as (lsusb):
```
Bus 001 Device 017: ID 0b05:1736 ASUSTek Computer, Inc. 
```

Then the (dmesg) firmware is loaded as well:
```
[23245.690079] usb 1-5: new high speed USB device using ehci_hcd and address 12
[23246.173283] IR NEC protocol handler initialized
[23246.191064] IR RC5(x) protocol handler initialized
[23246.201057] IR RC6 protocol handler initialized
[23246.203899] dib0700: loaded with support for 15 different device-types
[23246.205043] dvb-usb: found a 'Asus My Cinema-U3000Hybrid' in cold state, will try to load a firmware
[23246.215900] IR JVC protocol handler initialized
[23246.278683] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[23246.284216] IR Sony protocol handler initialized
[23246.294391] lirc_dev: IR Remote Control driver registered, major 250 
[23246.307134] IR LIRC bridge handler initialized
[23246.491096] dib0700: firmware started successfully.
[23247.000271] dvb-usb: found a 'Asus My Cinema-U3000Hybrid' in warm state.
[23247.000381] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[23247.000509] DVB: registering new adapter (Asus My Cinema-U3000Hybrid)
[23247.276762] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[23247.321938] xc2028 8-0061: creating new instance
[23247.321942] xc2028 8-0061: type set to XCeive xc2028/xc3028 tuner
[23247.370095] Registered IR keymap rc-dib0700-rc5
[23247.372832] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/rc/rc0/input10
[23247.373027] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/rc/rc0
[23247.373266] dvb-usb: schedule remote query interval to 50 msecs.
[23247.373273] dvb-usb: Asus My Cinema-U3000Hybrid successfully initialized and connected.
[23247.374042] usbcore: registered new interface driver dvb_usb_dib0700

```

My problems are:
What to do next, to get the device working?
If I start xawtv, it complains:
```
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.38-10-generic)
xinerama 0: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such device or address
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Permission denied
v4l2: open /dev/video0: Permission denied
v4l: open /dev/video0: Permission denied
no video grabber device available
```
and also as root:
```
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (2.6.38-10-generic)
xinerama 0: 1680x1050+0+0
WARNING: No DGA direct video mode for this display.
can't open /dev/video0: No such device or address
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such device or address
v4l2: open /dev/video0: No such device or address
v4l: open /dev/video0: No such device or address
no video grabber device available
```

Although, I **do not have /dev/video0**, but the /dev/dvb/adapter0 devices come up upon insertion:
```
drwxr-xr-x  2 root root     120 2011-08-06 12:13 .
drwxr-xr-x  3 root root      60 2011-08-06 12:13 ..
crw-rw----+ 1 root video 212, 0 2011-08-06 12:13 demux0
crw-rw----+ 1 root video 212, 1 2011-08-06 12:13 dvr0
crw-rw----+ 1 root video 212, 3 2011-08-06 12:13 frontend0
crw-rw----+ 1 root video 212, 2 2011-08-06 12:13 net0
```

I would like to use my tuner stick under ubuntu to receive analog / digital TV and stream it over the network (eg. with VLC) but for now I can't even watch any TV or listen to FM radios...

Any help would be appreciated.
Thanks

---

### Post by realzippy on 2011-08-06
Where does it say that firmware is loaded?
Would expect something like:


```
[  816.402150] dvb-usb: found a 'Asus My Cinema-U3000Hybrid' in cold state,
will try to load a firmware
[  816.402160] usb 2-5: firmware: requesting dvb-usb-dib0700-1.20.fw
[  816.459465] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[  816.672410] dib0700: firmware started successfully.
```

edit:
Ok just saw:
```
[14851.939822] dvb-usb: Asus My Cinema-U3000Hybrid successfully initialized and connected.
```

---

### Post by juhaszjozsef on 2011-08-06
Thanks for looking into my problem.
I've made some mistakes in my first post... Sorry for that!
Just pasted the dmesg | tail output. Double checked /dev and no /dev/video0... :( 
 -> Assumed it is a driver problem
 -> Recompiled v4l from mercurial
 -> No change in the situation...
Now I've updated the first post with the correct (and complete) dmesg output.

---

### Post by stepper on 2011-08-06
Since it says adapter0 registered, I will guess you can use VLC or Kaffeine to watch TV.

---

### Post by juhaszjozsef on 2011-08-07
Already tried it.
No channels found :( (on WIN it finds 44 channels)

---

### Post by realzippy on 2011-08-07
You mean kaffeine finds the adapter and just struggles when scanning?

---

### Post by MartyBuntu on 2011-08-07
What do you have connected to the tuner right now? (antenna...cable...etc...)

---

### Post by juhaszjozsef on 2011-08-08
Hi all!

Yes, kaffeine just tries to find channels with no luck :(
It does scan but cannot find anything...
I'm conected to UPC cable and find more than 40 channels on Win7 x64

---

### Post by realzippy on 2011-08-08
..you have a correct channels.conf ?

---

### Post by juhaszjozsef on 2011-08-09
I don't think so.
How can I check it?

---

### Post by realzippy on 2011-08-22
Kaffeine should ask for it and offer default channel.conf....

---

### Post by mzcl-mn on 2012-07-17
Hello!

I also am a happy owner of an Asus U3000 Hybrid USB Tuner...

But I cannot view DVB-T in linux as "perfectly" as I do in Windows, (I always get pixelizations and image and sound degradation on my Ubuntu 12.04 x86_64).

Is there any workaround to accomplish this?

Thanks.

---

### Post by wildmanne39 on 2012-07-17
Hi, old thread closed, please start a new thread.
Thanks

---

