---
title: "Problem with channel - DVB-S tuner Skystar USB HD"
date: 2013-02-22
forum: Multimedia Software
---

### Post by siekier on 2013-02-22
Hello,
Recently I was made my DVB-S Technisat _[Skystar USB HD]("https://www.technisat.com/en_XX/SkyStar-USB-HD/352-2675-1648/")_ tuner working on Linux. I am using Ubuntu 12.10 and Arch Linux, both 64 bit. My antenna is set for European Astra 23,5E satellite.
Recive on most channels is pretty the same like on Windows 7 in DVBViewer. 
 
The problem is with one channel - _[Planeta HD]("http://www.lyngsat.com/tvchannels/bg/Planeta-HD.html")_ is not working on Linux, but works good on Windows.
I have check it on Ubuntu and Arch on VLC, Me-TV, MPlayer with same results.
I have tried to set MythTV but I have some problems with that tuner in MythTV.

Running simple testing tool I got this:
```
[jacek@arch ~]$ femon -H
FE: Technisat SkyStar USB HD (DVB-S/S2) (DVBS)
Problem retrieving frontend information: Inappropriate ioctl for device
status SCVYL | signal  72% | snr  76% | ber 0 | unc 1 | FE_HAS_LOCK
```
Here are some screenshots:
[U][Planeta HD (Ubuntu VLC)]("http://i.imm.io/WY5S.png")
[Planeta HD (Windows DVBViewer)]("http://i.imm.io/WY7H.png")
[Some HD channel (Ubuntu VLC)]("http://i.imm.io/WVE9.png")[/U]

---

