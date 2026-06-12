---
title: "How to Astrometa DVB-T2 usb tuner in ubuntu ?"
date: 2016-08-27
forum: Mythbuntu
---

### Post by echosmart on 2016-08-27
Hi !
i'm want to use astrometa usb dvb-t2 usb stick on ubuntu but not working.

I'm trying this:
```
git clone git://linuxtv.org/media_build.git
cd media_build
./build
make stagingconfig
make -C ./v4l/
make install
copied firmware
dmesg | grep dvb
```

after reboot install w_scan on ubuntu, and scanning DVB-T2 channels. 
W_scan fiind all dvb-t2 channels, make channelist file, but this file not played with VLC or Me TV.
Also try to scan with tvheadend, but tvheadend not scanning anything..

from this webpage: [http://blog.palosaari.fi/2014/09/naked-hardware-18-astrometa-amdvb-t2-v2.html](http://blog.palosaari.fi/2014/09/naked-hardware-18-astrometa-amdvb-t2-v2.html)

it's possible to solve this ?

If trying to open channels with VLC this is the error:
[http://imgur.com/a/pBeDe](http://imgur.com/a/pBeDe)

If i want to open channelist with VIDEOS (TOTEM) :

[http://imgur.com/a/X31yC](http://imgur.com/a/X31yC)

missing multimedia DVB-T2 protocpol source.

For scanning DVB-T2 i'm using 

```
w_scan -ft -c RO -L >channels.xspf
```

this is scaned xml file:

```
]<?xml version="1.0" encoding="UTF-8"?>
 	DVB Playlist
	w_scan-20141122
	[http://wirbel.htpc-forum.de](http://wirbel.htpc-forum.de)
 			0001. TVR1
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				2
				program=1
 			0002. TVR2
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				3
				program=2
 			0003. TVR3
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				4
				program=3
 			0004. TVR Cluj
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				5
				program=4
 			0005. TVR Craiova
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				6
				program=5
 			0006. TVR Iasi
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				7
				program=6
 			0007. TVR Timisoara
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				8
				program=7
 			0008. TVR Tg Mures
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				9
				program=8
 			0009. TVR HD
			dvb-t2://frequency=474000000
 				dvb-bandwidth=8
				dvb-ts-id=600
				10
				program=9
```

---

### Post by echosmart on 2016-08-31
This device is not supported on Ubuntu ??

---

### Post by howefield on 2016-09-01
Thread moved to the "*Mythbuntu*" forum, not because you are running Mythbuntu but the experts who post here might be able to help you out.

I'd try renaming the channels.xspf to channels.conf and try again in VLC.

---

### Post by echosmart on 2016-09-02
I lost a few days with this, but whithout results...
I abandon this project.

DVB-T2 not running in Ubuntu :(

In Windows with Dvbviewer Pro Demo running very fast and very good !
Ubuntu has disappointed me again.

I do not know how many days I try to make something work that does not work...
...that was...

---

### Post by echosmart on 2016-09-06
Solved by user @Kimarite from hungarian Ubuntu forum.

[http://ubuntu.hu/node/42292](http://ubuntu.hu/node/42292)

Thanks @Kimarite !

---

