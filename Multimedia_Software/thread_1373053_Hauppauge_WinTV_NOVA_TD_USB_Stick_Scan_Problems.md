---
title: "Hauppauge WinTV NOVA TD USB Stick Scan Problems"
date: 2010-01-05
forum: Multimedia Software
---

### Post by Davlar on 2010-01-05
[SIZE=2]Hi,

I've bought one of these: WinTV-NOVA-TD USB stick
to work with my Asrock ion 330 nettop pc thing.  Looking on the LinuxTv site ([http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices](http://www.linuxtv.org/wiki/index.php/DVB-T_USB_Devices#DVB-T_USB_Devices)) this device is linux compatible.

The model no. on the back of the device is: [/SIZE]M/R: 95809/A1E4 #0307
[SIZE=2]
I tried the following with first [/SIZE][SIZE=2]Mythbuntu 9.10 and then[/SIZE][SIZE=2] Ubuntu 9.04, but I'm still unable to get scan for channels working.
[/SIZE][SIZE=2]
Anyway, this is what I've done so far:

1. Installed DVB stick on a WinXp laptop and using my TV aerial in the loft it could find lots of DVB-T channels (and even ones I didn't want, i.e. QVC shopping channel, etc.).

2. Using the instructions here ([http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)) I built and installed the V4L-DVB device drivers and dvb apps.

3. Typing [/SIZE][SIZE=2][SIZE=1]dmesg | grep dvb[/SIZE]
[SIZE=1][   12.879450] dvb-usb: found a 'Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity' in warm state.
[   12.879597] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.426640] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   13.740107] dvb-usb: schedule remote query interval to 50 msecs.
[   13.740117] dvb-usb: Hauppauge Nova-TD Stick/Elgato Eye-TV Diversity successfully initialized and connected.
[   13.740422] usbcore: registered new interface driver dvb_usb_dib0700

[SIZE=2]-which sort of looks like it has found the hardware successfully.

4. Now performing a scan I get the following:
[/SIZE][/SIZE][/SIZE]scan /home/dave/dvb-apps/util/scan/dvb-t/uk-SandyHeath 
scanning /home/dave/dvb-apps/util/scan/dvb-t/uk-SandyHeath
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 641833000 0 3 9 1 0 0 0
initial transponder 665833000 0 2 9 3 0 0 0
initial transponder 650167000 0 2 9 3 0 0 0
initial transponder 842000000 0 3 9 1 0 0 0
initial transponder 626167000 0 3 9 1 0 0 0
initial transponder 674167000 0 3 9 1 0 0 0
>>> tune to: 641833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 641833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 665833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 665833000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 650167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 650167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 842000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x0010
>>> tune to: 626167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 626167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 674167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 674167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (0 services)
Done.
[SIZE=2][SIZE=1]
[SIZE=2]And yes uk-Sandyheath is the closest TV transmitter to where I live.

5. I've also tried using the w_scan program:
[/SIZE][/SIZE][/SIZE]w_scan -f t
w_scan version 20081106
Info: using DVB adapter auto detection.
   Found DVB-T frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend DiBcom 7000PC supports
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
219500: 


w_scan version 20081106
Info: using DVB adapter auto detection.
   Found DVB-T frontend. Using adapter /dev/dvb/adapter0/frontend0
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
frontend DiBcom 7000PC supports
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
219500: 



...

794000: 
802000: 
810000: 
818000: 
826000: 
834000: 
842000: 
850000: 
858000: 
ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!
dumping lists (0 services)
Done.

[SIZE=2]And still nothing :confused:

6. I've tried turning on the low noise amplifier (LNA) on the device using:
[/SIZE][FONT=Courier New]options dvb_usb_dib0700 force_lna_activation=1
in:
[/FONT]/etc/modprobe.d/options
[SIZE=2]And then checking it is enabled by looking in:
[/SIZE]/sys/module/dvb_usb_dib0700/parameters/force_lna_activation
[SIZE=2]to see that it is set to 1, and guess what...it is.

7. I've also tried regressing the firmware by re-naming 
[/SIZE]dvb-usb-dib0700-1.10.fw to dvb-usb-dib0700-1.20.fw 
[SIZE=2]-but still no luck[/SIZE]
[SIZE=2]
So that's about as far as I've got - if anyone out there could provide any assistance then that would be quite nice :)

Thanks.
[/SIZE]

---

### Post by wirbel2 on 2010-01-05
Please use a _current_ version of w_scan, not a old version from 2k8.



Or update your dvb-apps to latest version, especially your uk-SandyHeath file, it might be outdated.

UK seems to switch over to TRANSMISSION_MODE_8K ; so this change would be at least a try.

---

### Post by Davlar on 2010-01-11
Eventually have now managed to successfully scan all channels from my local transmitter.  

Problem was the masthead amplifier I was using next to my loft TV aerial was set to the maximum gain of 25 dB.  Reducing this to the minimum gain setting of 12 dB allowed scan to work.

---

