---
title: "Me-Tv and MPEG4"
date: 2012-11-08
forum: Multimedia Software
---

### Post by eslavko on 2012-11-08
Hello...

I have AF9015 DVB-T receiver but can't get it work. Channel search in MeTv work but there are no output.
I assume that MPEG4 is problem as all transmission here are encoded in MPEG4. The card works OK under windows. So it's capable to receive MPEG4 stream.
Is there some chances to get it work under ubuntu?!? 

I have 12.04 precise pangolin.

thanks

------------------------
some debug info

lsusb
Bus 001 Device 009: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0

dmesg | grep dvb  gave me 
[   19.986801] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[   19.986840] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   20.104533] dvb-usb: schedule remote query interval to 500 msecs.
[   20.104535] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
[   20.110792] usbcore: registered new interface driver dvb_usb_af9015

---

### Post by eslavko on 2012-11-08
Hello...

Seems that MPEG4 is not the problem. 

I actually can get video but.....
Here is the steps.

My OS is UBUNTU 12.04

I start WinXp in virtual box (under ubuntu)
I start original BlazeDTV software for my receiver
I got very jerky stream (under pure windows is ok)
I virtualy disconnect DVB receiver in VirtualBox

I start Me-TV in ubuntu. 
I got the 1'st stream (no mater what stream is selected in win) in the list working. (perfect video and audio)
...When I try to change channel sometimes I got no response at all (old channel still playing) or something frezze and I can't recover video until I restart system.

So I assume it's driver problem or something. (windows leave receiver in state that ubuntu can capture data.)

Some thought?

---

### Post by BicyclerBoy on 2012-11-08
It is very likely you need firmware.
The device firmware could be in linux-firmware packages.
linux-firmware
linux-firmware-nonfree

There are some f/w & driver ideas here.. 
[http://linuxtv.org/wiki/index.php/Afatech_AF9015](http://linuxtv.org/wiki/index.php/Afatech_AF9015)

Your dmesg shows device in warm state i.e. f/w loaded by windows driver.

Try dmesg after re-plugging the device & without virtualbox running.

I assume by MPEG4 you really mean video codec mpeg4/10 AVC h264.
The container is mpeg-ts which is an mpeg2 transport stream container.
A lot of s/w labels DivX Xvid (mpeg4-asp) as MPEG4.

dvb-t commonly uses latm-aac with mpeg4/10_AVC. Programs like Xine were very slow to add support.

---

### Post by eslavko on 2012-11-09
I need to update driver. And kaffeine works now.

---

