---
title: "LITE-ON USB2.0 DVB-T Tuner - works sometimes... but why not always??"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Mr_Arne on 2008-01-03
Hello all of you,
For quite a while I've been wrestling with a TV-tuner as described in the subject line. It has been working flawlessly in both Xubuntu 7.04, and later Ubuntu 7.10 with only minor configuring. This is on IBM laptops, mod T23, quite old hardware. I have done channel.conf-files with scan-utils and I am able to watch TV with Xine, very nice yes. BUT: when I try to repeat my success story on an ordinary IBM desktop machine, a ThinkCentre S50, somewhat more modern hardware, it just refuse to work...! On this hardware I've been trying with both Ubuntu 7.04 and 7.10. In this case I also keep my /home in a separate partition which I keep untouched when upgrading from one release to another (which I always do from scratch).

Some info from the working laptop (Ubuntu 7.10):
```
ola@gutsy01:~$ lsmod | grep usb
dvb_usb_dibusb_mc       6528  0 
dvb_usb_dibusb_common    10884  1 dvb_usb_dibusb_mc
dib3000mc              13444  2 dvb_usb_dibusb_common
dvb_usb                21644  2 dvb_usb_dibusb_mc,dvb_usb_dibusb_common
dvb_core               82216  1 dvb_usb
dvb_pll                15492  2 dvb_usb_dibusb_common,dvb_usb
i2c_core               26112  5 mt2060,dib3000mc,dibx000_common,dvb_usb,dvb_pll
usbcore               138632  4 dvb_usb_dibusb_mc,dvb_usb,uhci_hcd
```

```
ola@gutsy01:~$ dmesg | grep dvb
[   25.956000] dvb-usb: found a 'LITE-ON USB2.0 DVB-T Tuner' in cold state, will try to load a firmware
[   26.076000] dvb-usb: downloading firmware from file 'dvb-usb-dibusb-6.0.0.8.fw'
[   26.804000] usbcore: registered new interface driver dvb_usb_dibusb_mc
[   26.928000] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[   28.732000] dvb-usb: found a 'LITE-ON USB2.0 DVB-T Tuner' in warm state.
[   28.732000] dvb-usb: will use the device's hardware PID filter (table count: 32).
[   29.392000] dvb-usb: schedule remote query interval to 150 msecs.
[   29.392000] dvb-usb: LITE-ON USB2.0 DVB-T Tuner successfully initialized and connected.
```

Some info from the non-working desktop (Ubuntu 7.10):
```
ola@workplace01:~$ lsmod | grep usb
dvb_usb_dibusb_mc       6528  0 
dvb_usb_dibusb_common    10884  1 dvb_usb_dibusb_mc
dib3000mc              13444  1 dvb_usb_dibusb_common
dvb_usb                21644  2 dvb_usb_dibusb_mc,dvb_usb_dibusb_common
dvb_core               82216  1 dvb_usb
dvb_pll                15492  2 dvb_usb_dibusb_common,dvb_usb
i2c_core               26112  4 dib3000mc,dibx000_common,dvb_usb,dvb_pll
usbcore               138632  5 dvb_usb_dibusb_mc,dvb_usb,ehci_hcd,uhci_hcd
```

```
ola@workplace01:~$ dmesg | grep dvb
[   26.934984] dvb-usb: found a 'LITE-ON USB2.0 DVB-T Tuner' in cold state, will try to load a firmware
[   27.009406] dvb-usb: downloading firmware from file 'dvb-usb-dibusb-6.0.0.8.fw'
[   27.063250] usbcore: registered new interface driver dvb_usb_dibusb_mc
[   27.066390] dvb-usb: generic DVB-USB module successfully deinitialized and disconnected.
[   28.956096] dvb-usb: found a 'LITE-ON USB2.0 DVB-T Tuner' in warm state.
[   28.956311] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   28.961411] dvb-usb: no frontend was attached by 'LITE-ON USB2.0 DVB-T Tuner'
[   28.962224] dvb-usb: schedule remote query interval to 150 msecs.
[   28.962229] dvb-usb: LITE-ON USB2.0 DVB-T Tuner successfully initialized and connected.
```

Some advice anyone? I've googled myself to strange face colors about this ](*,), found suggestions from early 2006 on patches for v4l-drivers (which now is included in kernel, therefore the issue seems obsolete), found issues about usb-identification problems etc, but I think that the software should behave somehow similar though hardware differs significantly. Related experiences (and solutions??) are highly appreciated. :-P

Regards
Ola

---

