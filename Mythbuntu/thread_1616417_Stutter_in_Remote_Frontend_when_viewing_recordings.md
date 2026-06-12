---
title: "Stutter in Remote Frontend when viewing recordings"
date: 2010-11-08
forum: Mythbuntu
---

### Post by sinkyboy2000 on 2010-11-08
I have an Acer Revo (single core) as a backend/frontend.  I have an old EECPC has my only remote frontend.
 
The frontend stutters when I play recordings.  I thought it was a bit strange as Mythvideo and LiveTV work perfectly.  
 
Can anyone recommend how I go about identifying the problem.
 
I was originally running a livecd frontend from a usb stick.  I've done a full install on an SD card.  Problem occurs in both.
 
I'm pretty new to linux and mythtv - so sorry if this is really simple.

---

### Post by nickrout on 2010-11-08
you need to look in the file /var/log/mythtv/mythfrontend.log and see if you can see any errors recorded at the time the glitch happens.

---

### Post by haiko2201 on 2010-11-10
I believe your  EEEPC don't have enough performance. If the TV is good you could transcode the recordings to lower format and watch video.

haiko2201

---

### Post by sinkyboy2000 on 2010-11-17
The log looks like this.

> 010-11-17 22:23:26.122 RingBuf(myth://192.168.1.68:6543/1004_20101105232000.mpg): Waited 1.0 seconds for data to become available...
2010-11-17 22:23:26.269 NVP(0): prebuffering pause
2010-11-17 22:23:27.803 NVP(0): prebuffering pause
2010-11-17 22:23:28.159 RingBuf(myth://192.168.1.68:6543/1004_20101105232000.mpg): Waited 1.0 seconds for data to become available...
2010-11-17 22:24:06.490 NVP(0): prebuffering pause
2010-11-17 22:24:08.111 NVP(0): prebuffering pause
2010-11-17 22:24:10.067 NVP(0): prebuffering pause
2010-11-17 22:24:11.588 NVP(0): prebuffering pause
2010-11-17 22:24:14.010 NVP(0): prebuffering pause
2010-11-17 22:24:15.868 NVP(0): prebuffering pause
2010-11-17 22:24:17.470 NVP(0): Prebuffer wait timed out 10 times.
2010-11-17 22:24:18.037 NVP(0): prebuffering pause
2010-11-17 22:24:19.639 NVP(0): Prebuffer wait timed out 10 times.
2010-11-17 22:24:20.420 NVP(0): prebuffering pause
2010-11-17 22:24:20.980 RingBuf(myth://192.168.1.68:6543/1004_20101105232000.mpg): Waited 1.0 seconds for data to become available...
2010-11-17 22:24:22.021 NVP(0): Prebuffer wait timed out 10 times.
2010-11-17 22:24:22.800 TV: Attempting to change from WatchingPreRecorded to None
2010-11-17 22:24:22.801 [mp2 @ 0xb659f120]incomplete frame
2010-11-17 22:24:22.801 AFD Error: Unknown audio decoding error
2010-11-17 22:24:22.877 TV: Changing from WatchingPreRecorded to None
2010-11-17 22:24:34.889 Deleting UPnP client...

I don't think it's the cpu, because I've seen reports of others on the web using the eeepc for this purpose.  Also, wouldn't it have the same problem with live tv if it was a cpu problem?

Any help would be much appreciated.

---

### Post by nickrout on 2010-11-18
[http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause)

---

### Post by LowSky on 2010-11-18
if your using Wifi it could be the problem. I had ot upgrade to Wireless N because G didn't give me enough bandwidth. Also I know for a fact that Intel Atom processors cannot process HD video very well. My own netbook is a huge failure at playing HD video.

---

### Post by nickrout on 2010-11-18
> **LowSky said:**
> if your using Wifi it could be the problem. I had ot upgrade to Wireless N because G didn't give me enough bandwidth. Also I know for a fact that Intel Atom processors cannot process HD video very well. My own netbook is a huge failure at playing HD video.

All dealt with in the link I gave.

---

### Post by sinkyboy2000 on 2010-11-19
> **nickrout said:**
> [http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause](http://www.mythtv.org/wiki/Troubleshooting:Prebuffering_pause)
 
Thanks for that.  I suspect my problem is the "Network I/O issues".  I used storage groups to make the recordings accessible.  Does that rule out this as a cause?

---

### Post by nickrout on 2010-11-20
No, if you have network problems you have network problems, doesn't matter if it is storage groups, nfs or whatever.

What is your network setup?

And if you say "wireless" I say "that's your problem right there" followed by "run a wire" followed by "no, really run a wire" followed by "try powerline"

---

### Post by sinkyboy2000 on 2010-11-20
Yeah - wireless.  But surely if my network can handle livetv it should be able to handle recordings.  Are they not the same bitrate?

---

### Post by nickrout on 2010-11-20
> **sinkyboy2000 said:**
> Yeah - wireless.  But surely if my network can handle livetv it should be able to handle recordings.  Are they not the same bitrate?

yes I see your point. To eliminate it run a wire and see, it only has to drape across your floor for an hour or two to test it.

Otherwise work your way through the list.

---

