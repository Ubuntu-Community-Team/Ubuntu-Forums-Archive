---
title: "NovaT and HVR1300 timed out, no signal"
date: 2010-03-06
forum: Mythbuntu
---

### Post by paul-cyt on 2010-03-06
I have two cards which neither produces a successful channel scan.  Both result in 'timed out, no signal' messages:

Hauppague NovaT PCI
Hauppague HVR1300 PCI

$grep -i DVB: /var/log/dmesg
[   10.521765] DVB: registering new adapter (TT-Budget/WinTV-NOVA-T     PCI)
[   10.589391] DVB: registering adapter 0 frontend 0 (Philips TDA10045H DVB-T)...
[   10.908665] DVB: registering new adapter (cx88[0])
[   10.908668] DVB: registering adapter 1 frontend 0 (Conexant CX22702 DVB-T)...

$lspci | grep Multimedia
05:00.0 Multimedia controller: Philips Semiconductors SAA7146 (rev 01)
05:02.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:02.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
05:02.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

$tail -f /var/log/messages
tda1004x: found firmware revision 0 -- invalid
tda1004x: waiting for firmware upload (dvb-fe-tda10045.fw)...
budget_ci dvb 0000:05:00.0: firmware: requesting dvb-fe-tda10045.fw
tda1004x: firmware upload failed
tda1004x: found firmware revision 0 -- invalid
tda1004x: waiting for firmware upload (dvb-fe-tda10045.fw)...
budget_ci dvb 0000:05:00.0: firmware: requesting dvb-fe-tda10045.fw
tda1004x: firmware upload failed

So it looks to me that one of the cards (novaT?) is missing firmware, but why no channels found on the HVR1300?

I've install 9.04 64bit, 9.10 64bit and now 10.04 64 bit (5/3/2010 build) with autobuilds updates (and updated)

I've tried to use the log grabber, but can't work out how to get them to pastebin.... Duh!

I've tried to make mythbuntu work for me for 2 days... I'm pretty downhearted about this right now, I had told the wife that windows7 had to go and mythbuntu would be the way forward ..... please help me before the windows 7 disc goes back in the drive!  Eak!

---

### Post by paul-cyt on 2010-03-06
further investigations:

$ cd /etc/init.d
$ stop mythtv-backend
$scan -f /dev/dvb/adapter0/frontend0 -d /dev/dvb/adapter0/demux0 /home/tv/Desktop/freqs/uk-SandyHeath -o zap | tee /home/tv/Desktop/freqs/scanned-channels.conf

scanning /home/tv/Desktop/freqs/uk-SandyHeath
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
WARNING: >>> tuning failed!!!
>>> tune to: 842000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 626167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 626167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 674167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 674167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)



$scan -f /dev/dvb/adapter1/frontend0 -d /dev/dvb/adapter1/demux0 /home/tv/Desktop/freqs/uk-SandyHeath -o zap | tee /home/tv/Desktop/freqs/scanned-channels.conf

scanning /home/tv/Desktop/freqs/uk-SandyHeath
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
WARNING: >>> tuning failed!!!
>>> tune to: 842000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 626167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 626167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 674167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 674167000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)

---

### Post by paul-cyt on 2010-03-06
attempts to get firmware, but still no dvb-fe-tda10045.fw 

$apt-get install linux-firmware-nonfree

-rw-r--r--  1 root root   32522 2010-02-24 15:36 dvb-fe-cx24116.fw
-rw-r--r--  1 root root   12772 2010-02-24 15:36 dvb-fe-or51132-qam.fw
-rw-r--r--  1 root root   17532 2010-02-24 15:36 dvb-fe-or51132-vsb.fw
-rw-r--r--  1 root root    8518 2010-02-24 15:36 dvb-fe-or51211.fw
-rw-r--r--  1 root root   24478 2010-02-24 15:36 dvb-fe-tda10046.fw
-rw-r--r--  1 root root   24878 2010-02-24 15:36 dvb-fe-tda10048-1.0.fw
-rw-r--r--  1 root root   12401 2010-03-04 17:27 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root  239956 2010-02-24 15:36 dvb-ttpci-01.fw
-rw-r--r--  1 root root   12700 2010-02-24 15:36 dvb-usb-af9015.fw
-rw-r--r--  1 root root   10757 2010-02-24 15:36 dvb-usb-avertv-a800-02.fw
-rw-r--r--  1 root root    9025 2010-02-24 15:36 dvb-usb-bluebird-01.fw
-rw-r--r--  1 root root   34306 2010-02-24 15:36 dvb-usb-dib0700-1.10.fw
-rw-r--r--  1 root root   33768 2010-03-04 17:27 dvb-usb-dib0700-1.20.fw
-rw-r--r--  1 root root    9180 2010-02-24 15:36 dvb-usb-dibusb-5.0.0.11.fw
-rw-r--r--  1 root root    7558 2010-02-24 15:36 dvb-usb-dibusb-6.0.0.8.fw
-rw-r--r--  1 root root    7431 2010-02-24 15:36 dvb-usb-dtt200u-01.fw
-rw-r--r--  1 root root    3360 2010-02-24 15:36 dvb-usb-tvwalkert.fw
-rw-r--r--  1 root root    4286 2010-02-24 15:36 dvb-usb-umt-010-02.fw
-rw-r--r--  1 root root   10752 2010-02-24 15:36 dvb-usb-vp702x-01.fw
-rw-r--r--  1 root root   10752 2010-02-24 15:36 dvb-usb-vp7045-01.fw
-rw-r--r--  1 root root    8480 2010-02-24 15:36 dvb-usb-wt220u-02.fw
-rw-r--r--  1 root root   12902 2010-02-24 15:36 dvb-usb-wt220u-fc03.fw
-rw-r--r--  1 root root    8518 2010-02-24 15:36 dvb-usb-wt220u-zl0353-01.fw

---

### Post by paul-cyt on 2010-03-06
trying to get th tda10045 firmware:

$ apt-get install unzip   (you need this later)
$ apt-get install linux-doc
$ cd /usr/share/doc/linux-doc/dvb/
$ gunzip get_dvb_firmware.gz
$ chmod +x get_dvb_firmware

$ ./get_dvb_firmware tda10045

--2010-03-06 11:59:58--  [http://www.technotrend.de/new/217g/tt_budget_217g.zip](http://www.technotrend.de/new/217g/tt_budget_217g.zip)
Resolving [www.technotrend.de](www.technotrend.de)... 212.185.20.148
Connecting to [www.technotrend.de|212.185.20.148|:80](www.technotrend.de|212.185.20.148|:80)... connected.
HTTP request sent, awaiting response... 403 Forbidden
2010-03-06 11:59:58 ERROR 403: Forbidden.

wget failed - unable to download firmware at ./get_dvb_firmware line 577.

---

### Post by paul-cyt on 2010-03-06
I've now been able to get the tda10045 firmware.  See this thread for how I did it.

[http://ubuntuforums.org/showthread.php?t=1423062](http://ubuntuforums.org/showthread.php?t=1423062)

I'm not sure how old this version is.

using the 'scan' program, i've now got channels being listed!  woooohoooo!

/snip/
CBBC Channel:641833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:620:621:4671
BBC Red Button:641833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:4479
BBC NEWS:641833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:640:641:4415
BBC THREE:641833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:4351
BBC TWO:641833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:610:611:4237
BBC ONE:641833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_3_4:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:600:601:4173
ITV1:665833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:520:521:8258
ITV2:665833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:530:531:8325
Teletext:665833330:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_1_2:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:0:8575
/snip/

Now to try mythtv again....

---

### Post by paul-cyt on 2010-03-06
This is now very sad.  I can now watch TV using VLC (opening the channels.conf file generated from the 'scan')

But still myth will not produce a successful channel listing.

I'm at the end of my knowlegde now - any helpers?

---

### Post by paul-cyt on 2010-03-07
I have now imported the channels.conf file and I can finally watch some telly!  but no guide data and audio is also missing.....

---

### Post by mikeh on 2010-05-12
I was having these problems with Nova-T and ubuntu 9.10 in Australia.
Myth scan got 3 of 5 local channels. Importing channels.conf got others.
But no program guide. (I never had audio trouble.)

Now, with Ubuntu 10.04 lucid, I get the  "tda1004x: firmware upload failed".
No problems with the newer Dvico card.

---

### Post by dibuntux on 2010-05-13
OK, so this is the same problem I have and the MAJOR one with Myth.

Please read my thread:

[http://ubuntuforums.org/showthread.php?t=1332357](http://ubuntuforums.org/showthread.php?t=1332357)

and possibly add there so others can continue giving input on it.

TIA

---

