---
title: "Rhythmbox/Clementine: no mp3 from NAS"
date: 2012-07-30
forum: Networking &amp; Wireless
---

### Post by amalgamas on 2012-07-30
Since I upgraded to 12.04 I have this strange situation:

I cannot play mp3 music from my NAS any more in Rhythmbox/Clementine and gst123.  The NAS is mounted as a remote disc (Mmedia).  Fstab:
```
//10.0.0.20/Qmultimedia                    /media/Mmedia  cifs  credentials=/root/.smbcreds,directio,iocharset=utf8,noacl,noperm,rw,nobootwait              0  0
```Flac-files play normally, and all other network functions seem normal.  I also can play mp3 files with vlc

When I substitute the .smbcreds-file with username=xxxx and password=xxxx in fstab, the mp3-files also play normally.
```
$ sudo ls -l /root/.smbcreds
-rw-r--r-- 1 root root 33 juli   8 18:43 /root/.smbcreds
```As far as I can see, everything is exactly like it was in 11.04 when everything played normally (with the .smbcreds file).

Any input on this?

---

### Post by amalgamas on 2012-07-31
I finally solved the problem.

I have set up my own fstab file a couple of years ago as well as I was  able to.  But being a linux n00b I put in the parameters in a trial and  error fashion.  Finally I was able to get a working fstab, which worked  up to ubuntu ver. 11.10.  For some reason it doesn't under 12.04.

Removing the "directio" parameter from my fstab solved the problem and gave higher network throughput.  

As I regret having used precious time for the people that helped with the issue I will mark the issue as solved.

Btw: where is the fstab manual that also explains to us normals what all those shady parameters mean and do?

---

