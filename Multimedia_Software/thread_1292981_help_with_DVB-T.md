---
title: "help with DVB-T"
date: 2009-10-16
forum: Multimedia Software
---

### Post by c-m on 2009-10-16
I recently bought a TERRATEC CINERGY DVD-T usb adapter due to its compatibility with linux.

The device plugs straight in and is detected in all applications. 

The problem is that both scans in kaffiene and Me-tv have resulted in 0 channels being found. I have a signal strength of 92% and the same card can find channels in windows.

I am scanning the tacolneston transmitter in Norfolk.

Can anyone shed any light on this?

---

### Post by HappyFeet on 2009-10-16
Have you tried tvtime? Also, see [this]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers").

---

### Post by steefjeqv on 2009-10-17
Hi,

Give w_scan a try.

[https://launchpad.net/ubuntu/jaunty/+package/w-scan]("https://launchpad.net/ubuntu/jaunty/+package/w-scan")

Greetings,
Steven

---

### Post by c-m on 2009-10-17
> **steefjeqv said:**
> Hi,

Give w_scan a try.

[https://launchpad.net/ubuntu/jaunty/+package/w-scan]("https://launchpad.net/ubuntu/jaunty/+package/w-scan")

Greetings,
Steven

When I run w-scan it does something for a while and then says:

Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

What do i do next?

```
w_scan -ft -c GB >> channels.conf
w_scan version 20090808 (compiled for DVB API 5.0)
using settings for UNITED KINGDOM
DVB aerial
DVB-T GB
frontend_type DVB-T, channellist 6
output format vdr-1.6
Info: using DVB adapter auto detection.
	/dev/dvb/adapter0/frontend0 -> DVB-T "TerraTec/qanu USB2.0 Highspeed DVB-T Receiver": good :-)
	/dev/dvb/adapter1/frontend0 -> DVB-S "ST STV0299 DVB-S": specified was DVB-T -> SEARCH NEXT ONE.
Using DVB-T frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.0
frontend TerraTec/qanu USB2.0 Highspeed DVB-T Receiver supports
INVERSION_AUTO
QAM_AUTO
TRANSMISSION_MODE_AUTO
GUARD_INTERVAL_AUTO
HIERARCHY_AUTO
FEC_AUTO
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
Scanning 7MHz frequencies...
177500: (time: 00:00) 
184500: (time: 00:03) 
191500: (time: 00:05) 
198500: (time: 00:08) 
205500: (time: 00:10) 
212500: (time: 00:13) 
219500: (time: 00:15) 
226500: (time: 00:18) 
Scanning 8MHz frequencies...
474000: (time: 00:20) 
474167: (time: 00:23) 
473833: (time: 00:25) 
482000: (time: 00:28) 
482167: (time: 00:30) 
481833: (time: 00:33) 
490000: (time: 00:35) 
490167: (time: 00:38) 
489833: (time: 00:40) 
498000: (time: 00:43) 
498167: (time: 00:46) 
497833: (time: 00:48) 
506000: (time: 00:51) 
506167: (time: 00:53) 
505833: (time: 00:56) 
514000: (time: 00:58) 
514167: (time: 01:01) 
513833: (time: 01:03) 
522000: (time: 01:06) 
522167: (time: 01:08) 
521833: (time: 01:11) 
530000: (time: 01:13) 
530167: (time: 01:16) 
529833: (time: 01:18) 
538000: (time: 01:21) 
538167: (time: 01:23) 
537833: (time: 01:26) 
546000: (time: 01:28) 
546167: (time: 01:31) 
545833: (time: 01:33) 
554000: (time: 01:36) 
554167: (time: 01:39) 
553833: (time: 01:41) 
562000: (time: 01:44) 
562167: (time: 01:46) 
561833: (time: 01:49) 
570000: (time: 01:51) 
570167: (time: 01:54) 
569833: (time: 01:56) 
578000: (time: 01:59) 
578167: (time: 02:01) 
577833: (time: 02:04) 
586000: (time: 02:06) 
586167: (time: 02:09) 
585833: (time: 02:11) 
594000: (time: 02:14) 
594167: (time: 02:16) 
593833: (time: 02:19) 
602000: (time: 02:21) 
602167: (time: 02:24) 
601833: (time: 02:26) 
610000: (time: 02:29) 
610167: (time: 02:32) 
609833: (time: 02:34) 
618000: (time: 02:37) 
618167: (time: 02:39) 
617833: (time: 02:42) 
626000: (time: 02:44) 
626167: (time: 02:47) 
625833: (time: 02:49) 
634000: (time: 02:52) 
634167: (time: 02:54) 
633833: (time: 02:57) 
642000: (time: 02:59) 
642167: (time: 03:02) 
641833: (time: 03:04) 
650000: (time: 03:07) 
650167: (time: 03:09) 
649833: (time: 03:12) 
658000: (time: 03:14) 
658167: (time: 03:17) 
657833: (time: 03:19) 
666000: (time: 03:22) 
666167: (time: 03:25) 
665833: (time: 03:27) 
674000: (time: 03:30) 
674167: (time: 03:32) 
673833: (time: 03:35) 
682000: (time: 03:37) 
682167: (time: 03:40) 
681833: (time: 03:42) 
690000: (time: 03:45) 
690167: (time: 03:47) 
689833: (time: 03:50) 
698000: (time: 03:52) 
698167: (time: 03:55) 
697833: (time: 03:57) 
706000: (time: 04:00) 
706167: (time: 04:02) 
705833: (time: 04:05) 
714000: (time: 04:07) 
714167: (time: 04:10) 
713833: (time: 04:12) 
722000: (time: 04:15) 
722167: (time: 04:18) 
721833: (time: 04:20) 
730000: (time: 04:23) 
730167: (time: 04:25) 
729833: (time: 04:28) 
738000: (time: 04:30) 
738167: (time: 04:33) 
737833: (time: 04:35) 
746000: (time: 04:38) 
746167: (time: 04:40) 
745833: (time: 04:43) 
754000: (time: 04:45) 
754167: (time: 04:48) 
753833: (time: 04:50) 
762000: (time: 04:53) 
762167: (time: 04:55) 
761833: (time: 04:58) 
770000: (time: 05:00) 
770167: (time: 05:03) 
769833: (time: 05:05) 
778000: (time: 05:08) 
778167: (time: 05:11) 
777833: (time: 05:13) 
786000: (time: 05:16) 
786167: (time: 05:18) 
785833: (time: 05:21) 
794000: (time: 05:23) 
794167: (time: 05:26) 
793833: (time: 05:28) 
802000: (time: 05:31) 
802167: (time: 05:33) 
801833: (time: 05:36) 
810000: (time: 05:38) 
810167: (time: 05:41) 
809833: (time: 05:43) 
818000: (time: 05:46) 
818167: (time: 05:48) 
817833: (time: 05:51) 
826000: (time: 05:53) 
826167: (time: 05:56) 
825833: (time: 05:58) 
834000: (time: 06:01) 
834167: (time: 06:04) 
833833: (time: 06:06) 
842000: (time: 06:09) 
842167: (time: 06:11) 
841833: (time: 06:14) 
850000: (time: 06:16) 
850167: (time: 06:19) 
849833: (time: 06:21) 
858000: (time: 06:24) 
858167: (time: 06:26) 
857833: (time: 06:29) 

ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!


```

---

### Post by howefield on 2009-10-17
> **c-m said:**
> Can anyone shed any light on this?

Are you really running Gutsy ?

Newer kernels seem to be kinder to dvb-t devices.

To find the nearest transmitter to you, visit

[http://www.digitaluk.co.uk/postcodechecker/](http://www.digitaluk.co.uk/postcodechecker/)

---

### Post by c-m on 2009-10-17
I'm running Karmic

I know my nearest transmitter its Tacolneston in Norfolk, UK

I have tried running Scan but that doesn't work either:

scan uk-Tacolneston > channels.conf
scanning uk-Tacolneston
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: cannot open 'uk-Tacolneston': 2 No such file or directory
ERROR: initial tuning failed
dumping lists (0 services)
Done.

---

### Post by steefjeqv on 2009-10-17
Hi,

w_scan detects your dvb device.

Some possible options :

- your signal may be too strong. Are you using some kind of signal amplifier ?

- your dvb device may need firmware. If you haven't checked dmesg yet, you may find some usefull info there.

Greetings,
Steven

---

### Post by c-m on 2009-10-21
> **steefjeqv said:**
> Hi,

w_scan detects your dvb device.

Some possible options :

- your signal may be too strong. Are you using some kind of signal amplifier ?

- your dvb device may need firmware. If you haven't checked dmesg yet, you may find some usefull info there.

Greetings,
Steven


No amplification used at all. 

The device sohuldn't need additional firmware as it is well known to work with linux out of the box.

[http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T2]("http://www.linuxtv.org/wiki/index.php/TerraTec_Cinergy_T2")



it works fine in Windows.

What else can I try in linux to get this working?

---

### Post by steefjeqv on 2009-10-24
Hi,

The device needs firmware, which normally is loaded by default.
However, these things go wrong once in while.
I remember having to move my firmware to another dir when Gutsy came out. It was my Terratec Cinergy DVB-T which suddenly stopped working. Great signal no lock.
If this is the case, your dmesg or syslog should mention this.

Greetings,
Steven

---

### Post by c-m on 2009-10-24
I have just plugged the device in and here is the relevent dmesg output:

```
[  190.784889] usb 1-2: configuration #1 chosen from 1 choice
[  190.813079] dvb-usb: found a 'TerraTec/qanu USB2.0 Highspeed DVB-T Receiver' in warm state.
[  190.816683] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  190.816812] DVB: registering new adapter (TerraTec/qanu USB2.0 Highspeed DVB-T Receiver)
[  190.817808] DVB: registering adapter 1 frontend 0 (TerraTec/qanu USB2.0 Highspeed DVB-T Receiver)...
[  190.818117] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/input/input7
[  190.818150] dvb-usb: schedule remote query interval to 50 msecs.
[  190.818935] dvb-usb: TerraTec/qanu USB2.0 Highspeed DVB-T Receiver successfully initialized and connected.
[  190.818964] usbcore: registered new interface driver cinergyT2

```

---

### Post by steefjeqv on 2009-10-24
Hi,

There seems to be a kernel problem for Karmic :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421258]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421258")

Should be fixed in the newest kernel, as mentioned in the bug report.

Greetings,
Steven

---

### Post by c-m on 2009-10-24
So its a case of downloading the absolute latest kernel?

---

### Post by steefjeqv on 2009-10-24
Hi,

As of version 2.6.31-10.33 things should work.

If you're using an older kernel, then this should be the culprit.

Greetings,
Steven

---

### Post by c-m on 2009-11-04
I now have the very latest karmic kernel, but still no luck.

```

carl@carl-desktop:~$ scan /usr/share/dvb/dvb-t/uk-Tacolneston > channels.conf
scanning /usr/share/dvb/dvb-t/uk-Tacolneston
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 810000000 0 3 9 1 0 0 0
initial transponder 786000000 0 2 9 3 0 0 0
initial transponder 730167000 0 2 9 3 0 0 0
initial transponder 769833000 0 3 9 1 0 0 0
initial transponder 794000000 0 3 9 1 0 0 0
initial transponder 818000000 0 3 9 1 0 0 0
WARNING: frontend type (QPSK) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (QPSK) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (QPSK) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (QPSK) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (QPSK) is not compatible with requested tuning type (OFDM)
WARNING: frontend type (QPSK) is not compatible with requested tuning type (OFDM)
ERROR: initial tuning failed
dumping lists (0 services)
Done.
carl@carl-desktop:~$ 




```

---

### Post by steefjeqv on 2009-11-04
Hi,

Do you have the same problem when you use w_scan ?

Perhaps using sudo when entering the scan command may give a better result.

Greetings,
Steven

---

