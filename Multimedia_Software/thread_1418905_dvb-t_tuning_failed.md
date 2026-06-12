---
title: "dvb-t tuning failed"
date: 2010-03-01
forum: Multimedia Software
---

### Post by eternnit on 2010-03-01
Hello,
 
I am trying to get my usb dvb-t ( ec168 ) working under ubuntu 9.10. But when I try to scan for channels I get "tuning failed".
 
**lsusb **
bus 002 device 005: id 18b4:1001 
 
**dmesg**
[ 110.616247] usb 2-1: new high speed usb device using ehci_hcd and address 4
[ 110.749146] usb 2-1: configuration #1 chosen from 1 choice
[ 110.750753] input: hid 18b4:1001 as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1:1.0/input/input12
[ 110.750897] generic-usb 0003:18b4:1001.0002: input,hidraw1: usb hid v1.11 keyboard [hid 18b4:1001] on usb-0000:00:1d.7-1/input0
[ 110.785211] dvb-usb: found a 'e3c ec168 dvb-t usb2.0 reference design' in cold state, will try to load a firmware
[ 110.785218] usb 2-1: firmware: requesting dvb-usb-ec168.fw
[ 110.789292] dvb-usb: downloading firmware from file 'dvb-usb-ec168.fw'
[ 110.892747] dvb-usb: found a 'e3c ec168 dvb-t usb2.0 reference design' in warm state.
[ 110.892836] dvb-usb: will pass the complete mpeg2 transport stream to the software demuxer.
[ 110.893366] dvb: registering new adapter (e3c ec168 dvb-t usb2.0 reference design)
[ 110.917566] dvb: registering adapter 0 frontend 0 (e3c ec100 dvb-t)...
[ 110.928401] mxl5005s: attached at address 0xc6
[ 110.928406] dvb-usb: e3c ec168 dvb-t usb2.0 reference design successfully initialized and connected.
[ 110.928437] usbcore: registered new interface driver dvb_usb_ec168
 
**scan /usr/share/dvb/dvb-t/es-madrid > $home/.channels.conf**
scanning /usr/share/dvb/dvb-t/es-madrid
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 618000000 0 2 9 3 1 3 0
initial transponder 706000000 0 2 9 3 1 3 0
initial transponder 770000000 0 2 9 3 1 3 0
initial transponder 810000000 0 2 9 3 1 3 0
initial transponder 834000000 0 2 9 3 1 3 0
initial transponder 842000000 0 2 9 3 1 3 0
initial transponder 850000000 0 2 9 3 1 3 0
initial transponder 858000000 0 2 9 3 1 3 0
>>> tune to: 618000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none
warning: >>> tuning failed!!!
>>> tune to: 618000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none (tuning failed)
warning: >>> tuning failed!!!
>>> tune to: 706000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none
warning: >>> tuning failed!!!
>>> tune to: 706000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none (tuning failed)
warning: >>> tuning failed!!!
>>> tune to: 770000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none
warning: >>> tuning failed!!!
>>> tune to: 770000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none (tuning failed)
warning: >>> tuning failed!!!
>>> tune to: 810000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none
warning: >>> tuning failed!!!
>>> tune to: 810000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none (tuning failed)
warning: filter timeout pid 0x0011
warning: filter timeout pid 0x0000
warning: filter timeout pid 0x0010
>>> tune to: 834000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none
warning: >>> tuning failed!!!
>>> tune to: 834000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none (tuning failed)
warning: >>> tuning failed!!!
>>> tune to: 842000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none
warning: filter timeout pid 0x0011
warning: filter timeout pid 0x0000
warning: filter timeout pid 0x0010
>>> tune to: 850000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none
warning: >>> tuning failed!!!
>>> tune to: 850000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none (tuning failed)
warning: >>> tuning failed!!!
>>> tune to: 858000000:inversion_auto:bandwidth_8_mhz:fec_2_3:fec_auto:qam_64:transmission_mode_8k:guard_interval_1_4:hierarchy_none
warning: filter timeout pid 0x0011
warning: filter timeout pid 0x0000
warning: filter timeout pid 0x0010
dumping lists (0 services)
done.
 
thanks in advance

---

### Post by Dr_Frost on 2011-09-03
same problem here, have 3x of the ec168 and same results for all 3...

Anybody have any idea's. would be nice to use these DVB-T's

---

### Post by BicyclerBoy on 2011-09-03
These device are a bit of a mess..bit of a lottery it seems. 

[http://linuxtv.org/wiki/index.php/E3C_EC168](http://linuxtv.org/wiki/index.php/E3C_EC168)

---

