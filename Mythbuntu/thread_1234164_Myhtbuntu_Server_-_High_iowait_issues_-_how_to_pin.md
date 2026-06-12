---
title: "Myhtbuntu Server - High iowait issues - how to pin point and solve?"
date: 2009-08-07
forum: Mythbuntu
---

### Post by Da_Teach on 2009-08-07
First let me give some details about my mythbuntu-server. Its a Intel E8400 server with 4Gb of memory. It has an 1261ML Areca controller with 10x 500Gb in Raid 6 and 3x 1Tb in Raid 5. The controller also has 2Gb of cache memory onboard. It also has 3 DVB-C capture cards. 

On normal usage its not having a huge issue (e.g. streaming live tv to two of the mythbuntu clients, or streaming any other types of video). 

Now when the disks get a bit of an io-load (unpacking a file, copying files from another pc to the server, etc) then there will be iowait spikes. This causes live tv / streaming video to freeze up and actually at times cause the whole server to hang for up to a few seconds.

Now I say "a bit of an io-load" because, for example, file transfers dont go above 40-50mb/sec. The Areca controller can handle much more (the main array of 10x 500Gb's can handle 300mb/sec easy and the 3x 1tb array can handle at least 150mb/sec).

I already ran vmstat -a 2 10 and it gave this as output:
```
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free  inact active   si   so    bi    bo   in   cs us sy id wa
 0  0  15612  22268 3422332 278904    0    0   279   512   18   65  3  1 95  1
 1  0  15612  23112 3421568 278820    0    0   486  3693 6260 10166  5  8 80  8
 0  0  15612  22296 3422776 278728    0    0   786  4568 5586 8493  6  5 89  0
 0  0  15612  23912 3421060 278552    0    0   704  8794 5074 7569  5  5 90  0
 0  0  15612  22336 3423172 278336    0    0   576 91692 5574 8184  4  8 83  4
 1  1  15612  23932 3420864 278224    0    0   606  1282 5063 8051  4  5 87  4
 0  3  15612  30100 3421028 272672    0    0    64    38 2077 5101  8 12  1 79
 1  0  15612  25752 3425700 272672    0    0    64   163 1976 4456  3  1 10 86
 1  0  15612  24188 3427472 272536    0    0   512  3115 5202 8225  4  6 90  0
 0  0  15612  21164 3431048 271988    0    0   640  3025 6198 9581  4  7 89  0

```

As it shows in that output "wa" (iowait) went up and all other io just dropped. iostat 1 showed the same, when iowait went up, all other io stopped. No process was using a lot of cpu (smbd was, at max, using 10% cpu). 

My linux knowledge isnt sufficient to pinpoint and/or solve the issue.

So my question is, can anyone help pin point the issue and possibly solve it ?

---

### Post by movieman on 2009-08-08
There are known problems with high IO-wait in the Linux kernel, which are always on the verge of being fixed. From what I remember disk reads can end up being queued behind large disk writes for a long period under heavy load.

One thing you might try is to mount the disk with the noatime option, as that will stop the OS updating access times and reduce the number of disk writes... that makes a big difference to my Linux box at work when it's heavily loaded. There are some apps which care about access time but most don't.

---

### Post by robertock on 2009-12-22
I had this same problem today. What I did: I verified my /etc/fstab file and I found my problem: one of the directories (mount points) I've configured in the file doesn't exist. So after I create the directory, everything just back to normal. No more IOWait.

---

