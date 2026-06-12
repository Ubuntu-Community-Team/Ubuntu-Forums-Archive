---
title: "Problem with Mythbuntu 8.0.4.1 -no channels"
date: 2008-07-26
forum: Mythbuntu
---

### Post by tikkis on 2008-07-26
Hi

I'm having a big problem with the new Mythbuntu 8.0.4.1 and Technotrend TT DVB-T 1500 -card. I can't get any channels tuned at all. What I'm trying to do is channel scanner -> full scan -> finland. But I get nothing at all. Also it seems strange that when I look at the **Transport Editor**, there aren't any Transports there. What am I doing wrong here ? Shouldn't this work pretty much out of the box ?

I had it all working ok with feisty fawn + mythtv, but then I decided to "upgrade" to mythbuntu.. :)

Please help, I'm loosing my mind here.

---

### Post by tikkis on 2008-07-27
Some update..

```
root@htpc:~# dmesg |grep DVB
[   29.458187] DVB: registering new adapter (TT-Budget-T-CI PCI)
[   29.948087] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
```

Seems to be ok ?

But still:

```
root@htpc:~# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Jyvaskyla > ch                                                annels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/fi-Jyvaskyla
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 546000000 0 2 9 3 1 2 0
initial transponder 786000000 0 2 9 3 1 2 0
initial transponder 746000000 0 2 9 3 1 2 0
.....>>> tune to: 786000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TR                                                ANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE
PuTTYWARNING: >>> tuning failed!!!
>>> tune to: 786000000:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_2_3:FEC_AUTO:QAM_64:TRANSMISSION_MODE_8K:GUARD_INTERVAL_1_8:HIERARCHY_NONE (tuning failed)

```

And

```
root@htpc:~# scan -c5
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
dumping lists (0 services)
Done.
```

Tips ? Anyone ?

---

### Post by ian dobson on 2008-07-27
Hi,

Maybe try with w_scan I've found it more reliable than scan.

I'll need to download/compile it yourself but it works without requiring a "scan table" (fi-Jyvaskyla).

I never got scan to find anything but w_scan found all my channels.

Regards
Ian Dobson

---

### Post by rune.evjen on 2008-07-28
Hi! I had the same problem after upgrading from 8.04 to 8.04.1 (or somewhere between that).

I use a Technotrend Premium DVB-C 2300, and scanning gave no results, neither did w_scan.

I checked everything, but dmesg output seemed fine and no errors while scanning.

Searching google I came across this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209971](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209971). This bug is regarding another card, but after enabling hardy-proposed I installed the kernel that was supposed to fix that bug.

After this, scanning works fine and mythtv works fine. 

uname -a on my now working system: Linux server 2.6.24-20-generic #1 SMP Mon Jul 28 13:06:07 UTC 2008 x86_64 GNU/Linux

---

