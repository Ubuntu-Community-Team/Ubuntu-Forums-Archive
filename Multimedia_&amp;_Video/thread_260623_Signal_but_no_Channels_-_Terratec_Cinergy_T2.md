---
title: "Signal but no Channels - Terratec Cinergy T2"
date: 2006-09-19
forum: Multimedia &amp; Video
---

### Post by adrian_ on 2006-09-19
I'm unable to get a channel list using w_scan or scan. I know the antenna strength is ok because I've use the T2 on a windows machine with no problems.

Setup:

The module seems to be ok:
ryan@number2:~$ lsusb
Bus 001 Device 002: ID 0ccd:0038 TerraTec Electronic GmbH Cinergy T^2 DVB-T Receiver
Bus 001 Device 001: ID 0000:0000

From dmesg:

[17179599.976000] DVB: registering new adapter (TerraTec/qanu USB2.0 Highspeed DVB-T Receiver).
[17179599.976000] input: TerraTec/qanu USB2.0 Highspeed DVB-T Receiver remote control as /class/input/input3
[17179599.976000] usbcore: registered new driver cinergyT2

The devices seem to be ok as well (ryan is a member of the video group):

ryan@number2:~$ ls /dev/dvb/adapter0/
demux0  dvr0  frontend0  net0
ryan@number2:~$ ls -l /dev/dvb/adapter0/ total 0
crw-rw---- 1 root video 212, 4 2006-09-18 19:12 demux0
crw-rw---- 1 root video 212, 5 2006-09-18 19:12 dvr0
crw-rw---- 1 root video 212, 3 2006-09-18 19:12 frontend0
crw-rw---- 1 root video 212, 7 2006-09-18 19:12 net0

Using Kaffeine, the Cinergy T2 also shows up in the dvb menu, again indicating that all's well in terms of the T2 being recognized.

I scan using the dvb-util package scan application and first used the provided example (Mendip) for my area (south-west england):

ryan@number2:~$ scan -u /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Mendip > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Mendip
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754167000 0 2 0 1 0 0 0
>>> tune to: 754167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.

Then tried modified the example using a frequency with which the windows machine successfully got a channel list, but still nothing:

ryan@number2:~$ scan -u /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Bristol > channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-Bristol
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 778000000 0 2 0 1 0 0 0
>>> tune to: 778000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
dumping lists (0 services)
Done.

I then built w_scan, this app walks frequencies looking for a decent signal then tries to grab channels (unlike dvb-util's scan where a frequency must be preset). 

w_scan result:

ryan@number2:~$ w_scan -t3 -F channels.conf
w_scan version 20060705
Info: using DVB adapter auto detection.
   Found DVB-T frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_
frontend TerraTec/qanu USB2.0 Highspeed DVB-T Receiver supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_
177500:
184500:
191500:
198500:
205500:
212500:
<sic> i'm cutting out some of the printout here, no signal until below <\sic>
746000: signal ok (I999B8C999D999M999T999G999Y999)
754000: signal ok (I999B8C999D999M999T999G999Y999)
762000:
770000:
778000: signal ok (I999B8C999D999M999T999G999Y999)
786000:
794000:
802000: signal ok (I999B8C999D999M999T999G999Y999)
810000:
818000:
826000: signal ok (I999B8C999D999M999T999G999Y999)
834000:
842000: signal ok (I999B8C999D999M999T999G999Y999)
850000:
858000:
tune to: :746000:I999B8C999D999M999T999G999Y999:T:27500:
Info: filter timeout pid 0x0011
Info: filter timeout pid 0x0000
Info: filter timeout pid 0x0010
tune to: :754000:I999B8C999D999M999T999G999Y999:T:27500:
Info: filter timeout pid 0x0011
Info: filter timeout pid 0x0000
Info: filter timeout pid 0x0010
tune to: :778000:I999B8C999D999M999T999G999Y999:T:27500:
Info: filter timeout pid 0x0011
Info: filter timeout pid 0x0000
Info: filter timeout pid 0x0010
tune to: :802000:I999B8C999D999M999T999G999Y999:T:27500:
Info: filter timeout pid 0x0011
Info: filter timeout pid 0x0000
Info: filter timeout pid 0x0010
tune to: :826000:I999B8C999D999M999T999G999Y999:T:27500:
Info: filter timeout pid 0x0011
Info: filter timeout pid 0x0000
Info: filter timeout pid 0x0010
tune to: :842000:I999B8C999D999M999T999G999Y999:T:27500:
----------no signal----------
tune to: :842000:I999B8C999D999M999T999G999Y999:T:27500: (no signal)
----------no signal----------
dumping lists (0 services)
Done.

Signal strength ok but no channels gleaned. Like I mention before it works with the same antenna cable, in the same physical position with a windows machine.

Configuration incorrect perhap? What's wrong here?
Thanks 

Adrian

---

### Post by weezel on 2007-08-15
I'm getting same kind of problems by myself :/

---

### Post by mhakali on 2007-11-12
Same problems here. A Hauppauge WinTV-HVR3000. Did you get any resolution to the problems?

Using vanilla kernel 2.6.23.1 and have tried to compile the CVS modules.

---

### Post by fdimmling on 2007-11-12
I am using the Cinergy T2 here in Berlin, Germany, on a Gutsy system and Kaffeine. Selecting the area (Berlin,germany) and starting Scan I got all stations available here and good qualitiy TV. Everything worked out of the box. Same result before with Feisty - and also with Dapper. 
Your problem must have its root in the data for the scan or something area specific - not related to the system.

Friedrich

---

### Post by motin on 2008-01-10
I just got the same problem. 

After moving my laptop closer to the window, I got different errors though - and also some channels went through. Still none of the channels I am looking for are found...

Any solution yet?

---

### Post by kurt-beule on 2008-01-25
yip yip, same problem here, aggravated by the fact that i have to run *sudo kaffeine* to get the device detected at all. the configure dialog pops up and shows the correct device specifications. but then, channel scan, signal and the green "lock" light (what does it mean?) goes on and off every now and then, but not all the way through the scan. it takes a minute or two but yields no channels.

when plugging the device into the usb, the blue light goes on for a short moment, and off again. it stays off even through the scan. when booting the laptop (p4) with the device already plugged, then the light is on for a slightly longer time during the initial boot stages but then goes off. the relevant output from "lsusb", "dmesg", and "ls -al /dev/dvb/adapter0/"  is astonishingly similar to the one described in the first post above.

i had the device running well with suse on the same machine, plugged to the same antenna, in the same room and on the same table. but after some update it stopped working. that was one of the reasons why i installed ubuntu 7.10 instead, which is running now. imagine my disappointment that the problem looks very much the same here too. :confused:

---

### Post by Hemonator on 2008-06-25
Yeh... "bump" I think... Terratec Cinergy DT and absolutely identical problem.

---

