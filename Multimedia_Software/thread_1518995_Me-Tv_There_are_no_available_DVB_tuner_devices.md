---
title: "Me-Tv There are no available DVB tuner devices"
date: 2010-06-27
forum: Multimedia Software
---

### Post by capo1949 on 2010-06-27
Hi All

I am trying to get me-tv to work on my laptop, dell studio 16. When I initially downloaded it it ask for transmitter station which I entered and it found the relevant channels, which I loaded and I was able to get a good picture, but no sound.

Whilst googling this problem I tried to open me-tv again and got the alarm
"There are no available DVB tuner devices".  I then removed the application with apt get and then reinstalled, resulting in the same alarm.
I cold booted and then me-tv shows a blank screen with the various tv program schedules detailed and red button channel selected?

graham@graham-laptop:~$ dmesg | grep dvb
[   15.165361] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   15.165366] usb 2-1.1: firmware: requesting dvb-usb-dib0700-1.20.fw
[   15.346753] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   16.066422] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   16.066473] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.510356] dvb-usb: schedule remote query interval to 50 msecs.
[   16.510359] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   16.510673] usbcore: registered new interface driver dvb_usb_dib0700
[ 1372.830062] dvb-usb: Hauppauge Nova-T Stick successfully deinitialized and disconnected.
[ 2283.364004] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[ 2283.364015] usb 2-1.1: firmware: requesting dvb-usb-dib0700-1.20.fw
[ 2283.374685] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[ 2284.083188] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[ 2284.083255] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 2284.514098] dvb-usb: schedule remote query interval to 50 msecs.
[ 2284.514104] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.

some assistance would be appreciated

---

