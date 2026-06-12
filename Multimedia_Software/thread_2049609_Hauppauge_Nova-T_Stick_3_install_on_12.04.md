---
title: "Hauppauge Nova-T Stick 3 install on 12.04"
date: 2012-08-28
forum: Multimedia Software
---

### Post by august008 on 2012-08-28
Hi All,

I'm trying to get a Hauppauge Nova-T Stick 3 to work on 12.04 (Linux ubuntu 3.2.0-23-generic).

I inserted the card and all seemed well:

august@ubuntu:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 2040:7070 Hauppauge Nova-T Stick 3
Bus 002 Device 003: ID 04f2:b27c Chicony Electronics Co., Ltd 

august@ubuntu:~$ dmesg | grep dvb
[   11.253423] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[   11.343136] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
[   12.046819] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   12.046883] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   12.542876] dvb-usb: schedule remote query interval to 50 msecs.
[   12.542880] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
[   12.543032] usbcore: registered new interface driver dvb_usb_dib0700

but when i run w_scan:

august@ubuntu:~$ w_scan -c AU -C UTF-8 -G > august.out
w_scan version 20120605 (compiled for DVB API 5.4)
using settings for AUSTRALIA
DVB aerial
DVB-T AU
scan type TERRESTRIAL, channellist 3
output format gstreamer
output charset 'UTF-8'
Info: using DVB adapter auto detection.
main:3220: FATAL: ***** NO USEABLE TERRESTRIAL CARD FOUND. *****
Please check wether dvb driver is loaded and
verify that no dvb application (i.e. vdr) is running.

So i followed: [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

But it didn't change anything.

Any thoughts on what i might have wrong?

Thanks in advance,

August

---

### Post by august008 on 2012-08-28
Ha. I got it. Permissions. Running scan:

august@ubuntu:~/w_scan-20120605$ scan /usr/share/dvb/dvb-t/au-Wollongong 
scanning /usr/share/dvb/dvb-t/au-Wollongong
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:2284: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 13 Permission denied

when run as root all is well. for both scan and w_scan.

---

### Post by Bucky Ball on 2012-08-28
Hi,

Don't know if you're interested, but MeTV (latest version in 12.04) is fast, simple, and has an autoscan. No need to manually use w_scan.

Xine is great, too. Even faster but no bells and whistles (Gxine has more). That does need a channel.conf file, which can be generated using w_scan, copied into the .xine folder. Then launch xine and it should find all channels. 

Have fun and good luck! Was pretty thrilling when I got my Ezycap DVB dongle working for the Olympics (which meant I could lie in bed watching til all hours as was middle of the night in Australia). Now all I need to do is get DAB+ working and all's sweet, but that looks a long way off in Linux. ;(

---

