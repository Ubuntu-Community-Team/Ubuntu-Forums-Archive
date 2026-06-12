---
title: "dvbhdhomerun problem, please help!!!"
date: 2015-09-15
forum: Mythbuntu
---

### Post by shadowyangweb on 2015-09-15
Spent one week on this, tried everything I can find online and still no working, please please please help!!!


First I am trying to use tvheadend on my ubuntu 14.04 server. I followed  [Complete Setup Guide for TVHeadEnd, Ubuntu, HDHomeRun Tuner, XBMC, and North American Program Guides]("https://tvheadend.org/boards/4/topics/10322/") and it doesn't work. The guide is for ubuntu 10.04 - 12.04, so I compiled the [dvbhdhomerun]("https://github.com/h0tw1r3/dvbhdhomerun/") by myself. No services found. I tried everything I can and I realized the problem is dvbhdhomerun.  Below is all the info. Please help.


Server:
```

~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


~$ uname -a
Linux homeserver 4.0.0-040000-generic #201504121935 SMP Sun Apr 12 23:36:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```


hdhomerun info:
```

~$ hdhomerun_config discover
hdhomerun device xxxxxxxx found at xxx.xxx.xxx.xxx


~$ hdhomerun_config xxxxxxxx get /sys/hwmodel
HDHR3-US


~$ hdhomerun_config xxxxxxxx get /sys/model
hdhomerun3_atsc


~$ hdhomerun_config xxxxxxxx get /sys/features
channelmap: us-bcast us-cable us-hrc us-irc kr-bcast kr-cable
modulation: 8vsb qam256 qam64
auto-modulation: auto auto6t auto6c qam


~$ hdhomerun_config xxxxxxxx get /sys/version
20150604


~$ hdhomerun_config xxxxxxxx get /tuner0/lockkey
none

```


By using hdhomerun_config scan, I got all channels I suppose to get.
```

~$ hdhomerun_config xxxxxxxx scan 0
SCANNING: 803000000 (us-bcast:69)
.....
SCANNING: 683000000 (us-bcast:49)
LOCK: 8vsb (ss=79 snq=71 seq=100)
TSID: 0x0033
PROGRAM 1: 62.1 CJNT-DT
........
SCANNING: 647000000 (us-bcast:43)
LOCK: 8vsb (ss=66 snq=57 seq=100)
TSID: 0x0C13
PROGRAM 3: 44.1 WFFF-HD
........
SCANNING: 599000000 (us-bcast:35)
LOCK: 8vsb (ss=88 snq=69 seq=100)
TSID: 0x4471
PROGRAM 1: 35.1 CFJP-DT
........
SCANNING: 581000000 (us-bcast:32)
LOCK: 8vsb (ss=92 snq=87 seq=100)
TSID: 0x0C11
PROGRAM 3: 33.1 VPBS
PROGRAM 4: 33.2 VPBS+
PROGRAM 5: 33.3 CREATE
PROGRAM 6: 33.4 WORLD
.........
SCANNING: 563000000 (us-bcast:29)
LOCK: 8vsb (ss=79 snq=72 seq=100)
TSID: 0x446F
PROGRAM 3: 29.1 CFTU-DT
..........
SCANNING: 545000000 (us-bcast:26)
LOCK: 8vsb (ss=100 snq=73 seq=100)
TSID: 0x446D
PROGRAM 3: 17.1 CIVM-HD
..........
SCANNING: 533000000 (us-bcast:24)
LOCK: 8vsb (ss=60 snq=43 seq=100)
TSID: 0x5F4C
PROGRAM 3: 24.1 CIVS-HD
SCANNING: 527000000 (us-bcast:23)
LOCK: none (ss=41 snq=0 seq=0)
SCANNING: 521000000 (us-bcast:22)
LOCK: 8vsb (ss=100 snq=89 seq=100)
TSID: 0x0C0D
PROGRAM 1: 3.1 WCAX-HD
PROGRAM 2: 3.2 Movies
SCANNING: 515000000 (us-bcast:21)
LOCK: 8vsb (ss=100 snq=91 seq=100)
TSID: 0x4467
PROGRAM 3: 6.1 CBMT-DT
SCANNING: 509000000 (us-bcast:20)
LOCK: none (ss=57 snq=0 seq=0)
SCANNING: 503000000 (us-bcast:19)
LOCK: 8vsb (ss=100 snq=84 seq=100)
TSID: 0x4465
PROGRAM 3: 2.1 CBFT-DT
..........
SCANNING: 479000000 (us-bcast:15)
LOCK: 8vsb (ss=99 snq=86 seq=100)
TSID: 0x4495
PROGRAM 1: 15.1 CKMI-HD
PROGRAM 2: 15.2 CKMI-SD
SCANNING: 473000000 (us-bcast:14)
LOCK: 8vsb (ss=91 snq=78 seq=100)
TSID: 0x087B
PROGRAM 3: 5.1 WPTZ-HD
PROGRAM 6: 5.2 The CW
PROGRAM 7: 5.3 Me TV
SCANNING: 213000000 (us-bcast:13)
LOCK: none (ss=59 snq=0 seq=0)
SCANNING: 207000000 (us-bcast:12)
LOCK: 8vsb (ss=100 snq=92 seq=100)
TSID: 0x446B
PROGRAM 1: 12.1 CFCF
SCANNING: 201000000 (us-bcast:11)
LOCK: none (ss=55 snq=0 seq=0)
SCANNING: 195000000 (us-bcast:10)
LOCK: 8vsb (ss=100 snq=91 seq=100)
TSID: 0x4469
PROGRAM 1: 10.1 CFTM-HD
.......

```


dvbhdhomerun info:


/etc/dvbhdhomerun
```

~$ more /etc/dvbhdhomerun
[xxxxxxxx-0]
tuner_type=ATSC
use_full_name=true


[xxxxxxxx-1]
tuner_type=ATSC
use_full_name=true


# Enable additional logging  from libhdhomerun itself
[libhdhomerun]
enable=true
logfile=/var/log/dvbhdhomerun.log

```


dmesg:
userhdhomerun up and running!
```

~$ dmesg
[79922.269841] HDHomeRun: Begin init, version 0.0.16
[79922.269952] HDHomeRun: Waiting for userspace to connect
[79922.269953] HDHomeRun: End init
[79922.734264] hdhomerun: userhdhomerun connected
[79922.734301] hdhomerun: userhdhomerun connected
[79922.734314] hdhomerun: creating dvb device for xxxxxxxx-0
[79922.734508] DVB: registering new adapter (HDHomeRun)
[79922.739503] HDHomeRun HDHomeRun.0: DVB: registering adapter 0 frontend 0 (HDHomeRun ATSC xxxxxxxx-0)...
[79922.739663] HDHomeRun0: DVB Frontend registered
[79922.739668] HDHomeRun0: Registered DVB adapter0
[79922.739816] hdhomerun: device /dev/hdhomerun_data0 created
[79922.739918] hdhomerun: userhdhomerun connected
[79922.739927] hdhomerun: creating dvb device for xxxxxxxx-1
[79922.740049] DVB: registering new adapter (HDHomeRun)
[79922.740697] HDHomeRun HDHomeRun.1: DVB: registering adapter 1 frontend 0 (HDHomeRun ATSC xxxxxxxx-1)...
[79922.740798] HDHomeRun1: DVB Frontend registered
[79922.740801] HDHomeRun1: Registered DVB adapter1
[79922.744755] hdhomerun: device /dev/hdhomerun_data1 created
[79922.745711] hdhomerun: userhdhomerun connected

```




And here comes the problem, either w_scan or scan founds nothing!!!


w_scan:
I ran it with different parameters and they made differents. 
w_scan -c CA
w_scan -c US
w_scan -f a -A 1 -c CA -v -F -t 3


```

~$ w_scan -c CA
w_scan version 20130331 (compiled for DVB API 5.10)
using settings for CANADA
ATSC
VSB US/CA, DVB-T TW
scan type TERRCABLE_ATSC, channellist 1
output format vdr-2.0
WARNING: could not guess your codepage. Falling back to 'UTF-8'
output charset 'UTF-8', use -C <charset> to override
Info: using DVB adapter auto detection.
    /dev/dvb/adapter0/frontend0 -> TERRCABLE_ATSC "HDHomeRun ATSC xxxxxxxx-0": good :-)
    /dev/dvb/adapter1/frontend0 -> TERRCABLE_ATSC "HDHomeRun ATSC xxxxxxxx-1": good :-)
Using TERRCABLE_ATSC frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.a
frontend 'HDHomeRun ATSC xxxxxxxx-0' supports
INVERSION_AUTO
8VSB
16VSB
QAM_64
QAM_256
FREQ (54.00MHz ... 858.00MHz)
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
57000: 8VSB(time: 00:00) 
............. 
803000: 8VSB(time: 02:48) 


ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

```


scan:
no matter I use ca-AB-Calgary or us-ATSC-center-frequencies-8VSB or us-NTSC-center-frequencies-8VSB or the one I created by the result of hdhomerun_config xxxxxxxx scan 0, I got same " tuning failed"
```

~$ scan /usr/share/dvb/atsc/ca-AB-Calgary 
scanning /usr/share/dvb/atsc/ca-AB-Calgary
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 515000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 515000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 563000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 563000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 635000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 635000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 683000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 683000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```


And here is the log:


```

~$ l /var/log/*home*
-rw-r--r-- 1 root    0 Sep 10 08:46 /var/log/dvbhdhomerun_stderr.log
-rw-r--r-- 1 root 152K Sep 10 10:03 /var/log/dvbhdhomerun_stdout.log
-rw-r--r-- 1 root  11K Sep 10 10:03 /var/log/dvbhdhomerun.log

```


nothing else but "hdhomerun_control_get_set: ERROR: invalid channel" in dvbhdhomerun.log
```

$ tail /var/log/dvbhdhomerun.log
20150910-10:02:40 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:02:43 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:02:45 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:02:48 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:02:50 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:02:53 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:02:55 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:02:58 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:03:00 hdhomerun_control_get_set: ERROR: invalid channel
20150910-10:03:03 hdhomerun_control_get_set: ERROR: invalid channel

```


for dvbhdhomerun_stdout.log, it keep repeating the message shows below 
```

~$ more /var/log/dvbhdhomerun_stdout.log
FE_SET_FRONTEND, freq: 1
Thu Sep 10 10:03:00 2015 sym qual: 0
Thu Sep 10 10:03:00 2015 hdhomerun_device_set_tuner_channel: 0
Thu Sep 10 10:03:01 2015 hdhomerun_tuner_status_t: 1
Thu Sep 10 10:03:01 2015 FE_READ_STATUS
Thu Sep 10 10:03:01 2015 sym qual: 0
Thu Sep 10 10:03:01 2015 FE_READ_STATUS
Thu Sep 10 10:03:01 2015 sym qual: 0
Thu Sep 10 10:03:02 2015 FE_READ_STATUS
Thu Sep 10 10:03:02 2015 sym qual: 0
Thu Sep 10 10:03:02 2015 FE_READ_STATUS
Thu Sep 10 10:03:02 2015 sym qual: 0
Thu Sep 10 10:03:02 2015 FE_READ_STATUS
Thu Sep 10 10:03:02 2015 sym qual: 0
Thu Sep 10 10:03:02 2015 FE_READ_STATUS
Thu Sep 10 10:03:02 2015 sym qual: 0
Thu Sep 10 10:03:02 2015 FE_READ_STATUS
Thu Sep 10 10:03:02 2015 sym qual: 0
Thu Sep 10 10:03:02 2015 FE_READ_STATUS
Thu Sep 10 10:03:02 2015 sym qual: 0
Thu Sep 10 10:03:03 2015 FE_READ_STATUS
Thu Sep 10 10:03:03 2015 sym qual: 0
Thu Sep 10 10:03:03 2015 FE_READ_STATUS
Thu Sep 10 10:03:03 2015 sym qual: 0
Thu Sep 10 10:03:03 2015 FE_READ_STATUS
Thu Sep 10 10:03:03 2015 sym qual: 0
FE_SET_FRONTEND, freq: 1
Thu Sep 10 1

```




Obviously tvheadend got no service is normal since w_scan and scan couldn't get any channel neither. I think the problem is causing by dvbhdhomerun driver. Is it anything else I can provide to help solving my problem? 


Thanks a lot in advance.

---

### Post by hollywoodpete on 2015-09-17
I won't be of too much help but would suggest trying to post at [https://tvheadend.org/projects/tvheadend/boards/4](https://tvheadend.org/projects/tvheadend/boards/4)
I used their forum when I was messing with TVHeadEnd. I finally switched to Myth when I got a cable card. TVHeadEnd was OK with over-the-air but a failure with cable. Or try Myth

---

### Post by blm-ubunet on 2015-09-22
And this cmd ?
```
w_scan -fa -A1 -c US -X
or
w_scan -fa -A1 -c CA -X
```
[http://linuxtv.org/wiki/index.php/W_scan#Scanning_ATSC_VSB_.28United_States.2C_Over-the-Air.29](http://linuxtv.org/wiki/index.php/W_scan#Scanning_ATSC_VSB_.28United_States.2C_Over-the-Air.29)

What's the "-F" or "-v" or the "-t" cmd options (that you used)?

---

### Post by shadowyangweb on 2015-09-23
tvheadend 4.05 works!!!!! dont need to use dvbhdhomerun anymore, thanks a lot for the help.

---

