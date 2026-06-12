---
title: "Asus U3000 mini tuning problems"
date: 2008-07-03
forum: Multimedia Software
---

### Post by dewgenenny on 2008-07-03
Hi,

Hoping someone can shed some light on this!

I have an Asus U3000 mini usb dvb-t tuner and I'm struggling to get it working properly in Hardy Heron. I have tested the card in windows xp with the same antenna and it works flawlessly, receiving all channels.

I am using the 2.6.24-19-generic kernel which (should) work out of the box. Device is recognised and the correct dvb_usb_dib0700 module is loaded, with the correct devices created etc etc. Correct firmware is in /lib/firmware/2.6.24-19-generic.

Scanning using kaffeine gets me some channels (I'm based in Perth, Western Australia) - I get SBS & SBS HD but no other channels. 

It appears to me that there is an issue with the tuner changing frequency (check the output of scan...), I'm a little stuck, any help would be massively appreciated!!!

Here's some technical output:

root@jaws:/home/tom# cat /var/log/dmesg | grep dvb
[   57.721601] dvb-usb: found a 'ASUS My Cinema U3000 Mini DVBT Tuner' in cold state, will try to load a firmware
[   57.773379] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   58.465269] dvb-usb: found a 'ASUS My Cinema U3000 Mini DVBT Tuner' in warm state.
[   58.465328] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   58.871555] dvb-usb: ASUS My Cinema U3000 Mini DVBT Tuner successfully initialized and connected.
[   58.871833] usbcore: registered new interface driver dvb_usb_dib0700

root@jaws:/home/tom#  lsmod | grep dvb
dvb_usb_dib0700        26376  0
dib7000p               17672  2 dvb_usb_dib0700
dib7000m               16516  1 dvb_usb_dib0700
dvb_usb                19852  1 dvb_usb_dib0700
dvb_core               81404  1 dvb_usb
dib3000mc              13960  1 dvb_usb_dib0700
dib0070                 9092  1 dvb_usb_dib0700
i2c_core               24832  8 mt2266,dib7000p,dib7000m,dvb_usb,nvidia,dib3000mc,dibx000_common,dib0070
usbcore               146028  9 dvb_usb_dib0700,dvb_usb,hci_usb,usb_storage,usbhid,libusual,ohci_hcd,ehci_hcd


root@jaws:/home/tom# ls -la /dev/dvb/adapter1
total 0
drwxr-xr-x  2 root root      120 2008-07-04 08:01 .
drwxr-xr-x  3 root root       60 2008-07-04 08:01 ..
crw-rw----+ 1 root video 212, 68 2008-07-04 08:01 demux0
crw-rw----+ 1 root video 212, 69 2008-07-04 08:01 dvr0
crw-rw----+ 1 root video 212, 67 2008-07-04 08:01 frontend0
crw-rw----+ 1 root video 212, 71 2008-07-04 08:01 net0

root@jaws:/home/tom# scan -a 1 /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Perth
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Perth
using '/dev/dvb/adapter1/frontend0' and '/dev/dvb/adapter1/demux0'
initial transponder 226500000 1 3 9 3 1 1 0
initial transponder 177500000 1 2 9 3 1 1 0
initial transponder 191625000 1 3 9 3 1 1 0
initial transponder 219500000 1 3 9 3 1 1 0
initial transponder 536500000 1 2 9 3 1 2 0
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
__tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: 226500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
__tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
__tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: 177500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
__tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
__tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: 191625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
__tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
__tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: 219500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_3_4:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_16:HIERARCHY_NONE
__tune_to_transponder:1483: ERROR: Setting frontend parameters failed: 22 Invalid argument
>>> tune to: 536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
0x0000 0x0320: pmt_pid 0x0400 SBS -- SBS HD (running)
0x0000 0x0321: pmt_pid 0x0401 SBS -- SBS (running)
0x0000 0x0322: pmt_pid 0x0402 SBS -- SBS NEWS (running)
0x0000 0x0323: pmt_pid 0x0408 SBS -- SBS 2 (running)
0x0000 0x032e: pmt_pid 0x0403 SBS -- SBS RADIO 1 (running)
0x0000 0x032f: pmt_pid 0x0404 SBS -- SBS RADIO 2 (running)
Network Name 'SBS NETWORK'
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 571500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
0x0320 0x0320: pmt_pid 0x0400 SBS -- SBS HD (running)
0x0320 0x0321: pmt_pid 0x0401 SBS -- SBS (running)
0x0320 0x0322: pmt_pid 0x0402 SBS -- SBS NEWS (running)
0x0320 0x0323: pmt_pid 0x0408 SBS -- SBS 2 (running)
0x0320 0x032e: pmt_pid 0x0403 SBS -- SBS RADIO 1 (running)
0x0320 0x032f: pmt_pid 0x0404 SBS -- SBS RADIO 2 (running)
Network Name 'SBS NETWORK'
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 585625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 564500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 543500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (12 services)
SBS HD:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:800
SBS:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:801
SBS NEWS:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:802
SBS 2:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:803
SBS RADIO 1:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:814
SBS RADIO 2:536500000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:815
SBS HD:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:102:103:800
SBS:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:801
SBS NEWS:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:162:83:802
SBS 2:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:161:81:803
SBS RADIO 1:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:201:814
SBS RADIO 2:536625000:INVERSION_AUTO:BANDWIDTH_7_MHZ:FEC_2_3:FEC_2_3:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE:0:202:815
Done.

Anyone got an idea what is going on here???????

CHeers,

Tom

---

### Post by xc3RnbFO8P on 2008-07-04
When you scan channels,
turn off wireless and mobile phones (cell phones).

---

### Post by dewgenenny on 2008-07-09
So have managed to get it fixed - turns out the ubuntu 2.6.24-19-generic version of the dvb driver for the u3000 mini is no good.

Once I'd get the latest version from linuxtv via mercurial, it was all good - some instructions here:

[http://www.linuxtv.org/wiki/index.php/Asus_My-Cinema-U3000_Mini](http://www.linuxtv.org/wiki/index.php/Asus_My-Cinema-U3000_Mini)

Cheers,

Tom

---

### Post by Offramp on 2008-10-21
Hi all,

I am also trying to get my U3000 tuner working.  I bought mine in Europe last year and I have a different VID and PID as to that listed at linuxtv.  I would appreciate it if anyone could let me know if they are having the same problem or how I could get the correct driver to load (system logs are telling me that it thinks it is a keyboard).  The device works on WinXP.

Cheers

---

