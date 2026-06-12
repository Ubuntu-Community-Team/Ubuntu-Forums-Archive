---
title: "Will I Have a Problem using an External HDD?"
date: 2007-11-19
forum: Mythbuntu
---

### Post by tonyr1988 on 2007-11-19
I will probably buy this hard drive this weekend to use for my Mythbuntu-box:

[http://www.circuitcity.com/ssm/Seagate-500GB-FreeAgent-Desktop-Drive-305004FDA1E1/sem/rpsm/oid/172685/catOid/-12976/rpem/ccd/productDetail.do?linkid=j13774590k32998&affiliateid=k32998&mid=&=guidt&1=](http://www.circuitcity.com/ssm/Seagate-500GB-FreeAgent-Desktop-Drive-305004FDA1E1/sem/rpsm/oid/172685/catOid/-12976/rpem/ccd/productDetail.do?linkid=j13774590k32998&affiliateid=k32998&mid=&=guidt&1=)

Am I going to have a problem because it's external? Will it be too slow and cause lag during recording live TV? To be honest, I know very little about HDDs - is the bottleneck in the connection (USB, SATA, etc) or the physical drive itself?

---

### Post by foxbuntu on 2007-11-19
USB 2.0 is more than fast enough to play back video. However in the current release of MythTV (0.20.2) it does not support multiple mount points for anything. So you will have to dedicate the USB drive to whatever function you chose. This however is a less than ideal solution and would not be recommended due to the stability of USB HDD's. If the USB drive loses connectivity for any reason it could cause the backend to hang up or in rare cases cause data corruption.

---

### Post by tonyr1988 on 2007-11-19
What do you mean by "multiple mount points"? You mean one partition mounted to multiple directories? If so, that shouldn't be a problem.

I have a 160GB internal drive right now. I was planning on dedicating around 20-30GB to root and set up the remaining 130ishGB of the internal + 500GB external together (via LVM) to hold data (at one mount point). Will that cause problems?

---

### Post by foxbuntu on 2007-11-19
Yes. You seriously do not want to use a USB drive for LVM. If it disconnects, even at boot time, the LVM will be broken and data lose will ensue. 

I meant MythTV cannot use multiple directories for storage yet. (i.e. music/recordings ect have to all be stored in one mount/directory, while they can have sub directories they cannot have a different one)

---

### Post by tonyr1988 on 2007-11-19
That's the problem I'm having. I don't want to waste the 140GB extra on my internal drive, but there are few other options.

Eek! Any ideas?

---

