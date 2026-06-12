---
title: "Unable to Scan for Channels"
date: 2011-04-15
forum: Mythbuntu
---

### Post by jmcvay on 2011-04-15
Mythbuntu 10.10 64bit installed.

All updates applied as of this posting.

Tuner Cards Installed.
(3)Hauppauge WinTV-HVR-1250 PCI
(1)Hauppauge WinTV-HVR-2250 PCI

Source: OTA HDTV via Antenna. (Looks great hooked directly to TV)

When I got to scan for channels, the setup application simply locks up. Screenshot provided.

[[IMG]http://img24.imageshack.us/img24/9319/unledi.jpg[/IMG]](http://img24.imageshack.us/i/unledi.jpg/)

Here is a link to my logs.

[http://mythbuntu.pastebin.com/fjtZUNzN](http://mythbuntu.pastebin.com/fjtZUNzN)

---

### Post by jmcvay on 2011-04-16
I have removed all but one Hauppauge WinTV-HVR-1250 PCI from my system.

I have cleared all my settings within MythTV Setup (Tuners, Source, etc)

I have been attempting to create a channels.conf file which I believed might be a work around for my inability to scan. It is hanging as well. I'm going to let it sit overnight and see if it isn't just my impatience.


```
josh@mythback:~$ scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
scanning /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB
service is running. Channel number: 5:1. Name: 'WTVF NewsChannel 5'
service is running. Channel number: 5:2. Name: 'NewsChannel5 Plus'
service is running. Channel number: 5:3. Name: 'THIStv Nashville'
>>> tune to: 85028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
```

---

### Post by jmcvay on 2011-04-16
I let **scan /usr/share/dvb/atsc/us-ATSC-center-frequencies-8VSB** run overnight it never gets past the filter timeout.

This is the output from yet another attempt. Similar results.


```
josh@mythback:~$ w_scan -fa -A1 -c US -x -o 7
w_scan version 20100316 (compiled for DVB API 5.1)
using settings for UNITED STATES
ATSC
VSB US/CA, DVB-T TW
frontend_type ATSC, channellist 1
output format initial tuning data
Info: using DVB adapter auto detection.
	/dev/dvb/adapter0/frontend0 -> ATSC "Samsung S5H1411 QAM/8VSB Frontend": good :-)
Using ATSC frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.1
frontend Samsung S5H1411 QAM/8VSB Frontend supports
INVERSION_AUTO
8VSB
QAM_64
QAM_256
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
57000: 8VSB(time: 00:02) 
63000: 8VSB(time: 00:04) 
69000: 8VSB(time: 00:07) 
79000: 8VSB(time: 00:09) 
85000: 8VSB(time: 00:12) 
177000: 8VSB(time: 00:15) 
183000: 8VSB(time: 00:17) 
189000: 8VSB(time: 00:20) 
195000: 8VSB(time: 00:22) (time: 00:25) 
201000: 8VSB(time: 00:26) 
207000: 8VSB(time: 00:28) 
213000: 8VSB(time: 00:31) 
473000: 8VSB(time: 00:33) 
479000: 8VSB(time: 00:36) (time: 00:38) signal ok:
	8VSB     f=479000 kHz
485000: 8VSB(time: 00:39) 
491000: 8VSB(time: 00:41) 
497000: 8VSB(time: 00:44) 
503000: 8VSB(time: 00:46) 
509000: 8VSB(time: 00:49) 
515000: 8VSB(time: 00:51) (time: 00:54) signal ok:
	8VSB     f=515000 kHz
521000: 8VSB(time: 00:54) 
527000: 8VSB(time: 00:57) (time: 00:59) 
533000: 8VSB(time: 01:00) 
539000: 8VSB(time: 01:03) 
545000: 8VSB(time: 01:05) 
551000: 8VSB(time: 01:08) (time: 01:10) signal ok:
	8VSB     f=551000 kHz
557000: 8VSB(time: 01:11) 
563000: 8VSB(time: 01:13) 
569000: 8VSB(time: 01:16) 
575000: 8VSB(time: 01:18) 
581000: 8VSB(time: 01:21) 
587000: 8VSB(time: 01:23) (time: 01:26) signal ok:
	8VSB     f=587000 kHz
593000: 8VSB(time: 01:26) 
599000: 8VSB(time: 01:28) 
605000: 8VSB(time: 01:31) (time: 01:34) signal ok:
	8VSB     f=605000 kHz
611000: 8VSB(time: 01:34) 
617000: 8VSB(time: 01:36) 
623000: 8VSB(time: 01:39) 
629000: 8VSB(time: 01:41) 
635000: 8VSB(time: 01:44) 
641000: 8VSB(time: 01:46) 
647000: 8VSB(time: 01:49) 
653000: 8VSB(time: 01:52) 
659000: 8VSB(time: 01:54) 
665000: 8VSB(time: 01:57) 
671000: 8VSB(time: 01:59) 
677000: 8VSB(time: 02:02) 
683000: 8VSB(time: 02:04) 
689000: 8VSB(time: 02:07) (time: 02:09) signal ok:
	8VSB     f=689000 kHz
695000: 8VSB(time: 02:10) 
701000: 8VSB(time: 02:12) 
707000: 8VSB(time: 02:15) 
713000: 8VSB(time: 02:17) 
719000: 8VSB(time: 02:20) 
725000: 8VSB(time: 02:22) 
731000: 8VSB(time: 02:25) 
737000: 8VSB(time: 02:27) 
743000: 8VSB(time: 02:30) 
749000: 8VSB(time: 02:32) 
755000: 8VSB(time: 02:35) 
761000: 8VSB(time: 02:37) 
767000: 8VSB(time: 02:40) 
773000: 8VSB(time: 02:42) 
779000: 8VSB(time: 02:45) 
785000: 8VSB(time: 02:47) 
791000: 8VSB(time: 02:50) 
797000: 8VSB(time: 02:52) 
803000: 8VSB(time: 02:55) 
tune to: 8VSB     f=479000 kHz 
(time: 02:57) ----------no signal----------
tune to: 8VSB     f=479000 kHz  (no signal)
(time: 02:58) service is running. Channel number: 17:1. Name: 'WZTV-FO'
tune to: 8VSB     f=515000 kHz 
(time: 02:59) Info: PAT filter timeout
Info: VCT(terrestrial) filter timeout
```

---

### Post by ilcapo09 on 2011-04-16
I was having the same problem trying to scan channels with my HVR-1250 running Mythbuntu 10.10 64bit.

After hours of trying different solutions and breaking up my installation I decided to do a clean install of Mythbuntu 10.10 but the 32bit version this time.

On my first scan it detected all the Clear Qam channels and it's been working like a charm since.

I'm no expert but I'm willing to say that the HVR-1250 works out of the box with 32bit Mythbuntu.

BTW, isnt the HVR-1250 PCI-e?

---

### Post by jmcvay on 2011-04-16
Good eye. It is indeed PCI-e. I'm a victim of copy and paste from Hauppauge's site.

I'll give 32bit a whirl, I've been fooling with this for months.

---

### Post by jmcvay on 2011-04-17
The channel scanning issue was resolved by switching to the 32bit version of Mythbuntu 10.10.

---

### Post by ilcapo09 on 2011-04-17
Yeah, there's something on the 64bit version that just doesn't mesh with the HVR-1250.

---

### Post by David Grigor on 2011-04-18
This has been an issue since day 1 of 10.10.  

To get to work with 64b, You can follow the workaround by applying a higher kernel from this thread:

[http://ubuntuforums.org/showthread.php?t=1593695](http://ubuntuforums.org/showthread.php?t=1593695)

However, so close to 11.04 release, I'd just wait and see if it's resolved.

---

### Post by jjinco33 on 2011-04-26
I tried as suggested and the X-Server kept segfaulting. :(

Had to remove the newer kernel through apt-get. The only options I have when adding the kernel PPA are 2.6.35 kernels. 

Card still hanging and I need to be able to record shows for my wife soon. Any help on adding the PPA correctly to upgrade my Kernel to a version that works?

---

### Post by jmcvay on 2011-05-03
This issue also seems to be resolved in 11.04 64bit.

---

### Post by Maheriano on 2011-05-15
Can someone please tell me how to get the 1250 to work in 11.04 64 bit? I scan for channels but none of them have any signal. Nothing locks up, I just don't get any channels. Which settings do I need for Canada? I'm trying to get a ATSC feed for over the air digital cable.

---

