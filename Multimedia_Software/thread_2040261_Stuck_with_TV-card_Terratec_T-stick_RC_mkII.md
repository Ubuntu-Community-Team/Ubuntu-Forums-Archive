---
title: "Stuck with TV-card Terratec T-stick RC mkII"
date: 2012-08-10
forum: Multimedia Software
---

### Post by Aljosja90 on 2012-08-10
Dear all,

I've recently switched from Win7 to Ubuntu 12.04 and I'm pretty happy about it so far. All my hardware works fine, with the exception of my usb tv-tuner, which is why I've come here. I searched on the subject a lot and couldn't find a solution for my situation among the many I've come across.

So I own a Terratec Cinergy T-stick RC mkII (rev. 3)> aljosja@aljosja-System-Product-Name:~$ lsusb
[...]
Bus 002 Device 003: ID 0ccd:00d3 TerraTec Electronic GmbH 
, which, as I've found out through Terratec's [_**website**_]("http://linux.terratec.de/tv_en.html"), is not supported yet by linuxtv.org. My kernel log or dmesg also showed that no driver could be loaded. After a lot of googleing and some failed attempts I found [_**this**_]("http://forum.ubuntuusers.de/topic/dvb-t-terratec-cinergytstickrc-rev-3-usb-wird-/#post-4395402") post, which apparently worked, since after the following the instructions, the suggested "dmesg| grep -i dvb" gives me the following output now:

> 
aljosja@aljosja-System-Product-Name:~$ sudo dmesg| grep -i dvb
[sudo] password for aljosja: 
[    2.335946] dvb-usb: found a 'USB DVB-T Device' in warm state.
[    2.335949] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[    2.337488] DVB: registering new adapter (USB DVB-T Device)
[    3.154714] DVB: registering adapter 0 frontend 0 (Realtek DVB-T RTL2832)...
[    3.154811] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/input/input14
[    3.154886] dvb-usb: schedule remote query interval to 287 msecs.
[    3.154888] dvb-usb: USB DVB-T Device successfully initialized and connected.
[    3.154909] usbcore: registered new interface driver dvb_usb_rtl2832u


However, the problem is that none of the software I've used can find any channels. MythTV doesn't see the device altogether, Kaffeine does, but it can't find any channels when doing the scan, and w_scan returns the following:

> 
aljosja@aljosja-System-Product-Name:~$ w_scan
w_scan version 20111203 (compiled for DVB API 5.4)
guessing country 'NL', use -c <country> to override
using settings for NETHERLANDS
DVB aerial
DVB-T Europe
frontend_type DVB-T, channellist 4
output format vdr-1.6
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
	/dev/dvb/adapter0/frontend0 -> DVB-T "Realtek DVB-T RTL2832": good :-)
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.4
frontend 'Realtek DVB-T RTL2832' supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
FREQ (50.00MHz ... 862.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:01) 
184500: (time: 00:06) 

[..] 

850000: (time: 04:46) 
858000: (time: 04:51) 

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!



Any ideas what the problem could be? Is the driver from the German website a faulty one?

Thank you very much!

---

