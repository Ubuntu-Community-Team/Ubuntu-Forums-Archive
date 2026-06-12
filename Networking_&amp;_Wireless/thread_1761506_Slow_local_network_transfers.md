---
title: "Slow local network transfers"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by packer_fan on 2011-05-18
Good morning,

I am new to ubuntu but not Linux in general.  Although I am not a networking guru by any means.  I just finished installing and patching ubuntu 10.04 (32 bit) on a dual core Intel MB that I bought  5 years ago but have not really used much.  The Intel MB supports Gigabit Ethernet.

I have the ubuntu server plugged into D-Link 1224T 10/100/1000 switch and am getting a green 1000Mbps link light.  

I also have a Mac Mini and a MacBook Pro plugged into the switch,  they also are getting a green 1000Mbps link lights.

When I scp (initiated from ubuntu) a 1GB file from the Mac Mini to the ubuntu box the initial transfer rate is like 55MB/sec and the steadily drops to around 8MB/sec during the transfer, with the transfer taking about 2 minutes.

If I scp (initited from the MacBook Pro) a 1GB file from the Mac Mini to the MacBook Pro box the initial transfer rate  is like 55MB/sec and stays right around the 48MB/Sec-50MB/sec range,  with the transfer taking about 10-15 seconds.

I have IPV6 turned off on the ubuntu box.  What else should I be looking at in order to get better transfer speeds on the ubuntu box?

Thanks
Peter

---

### Post by packer_fan on 2011-05-18
Additional info.

I downloaded and boot Fedora Core 15 beta Live CD and I was able to get 40MB/sec transfer rate.
The 1GB file was downloaded in less than 15 seconds.  

So may question is what is Fedora Core 15 beta doing different with my built in NIC card than
Ubuntu 10.04 and 11.04?

Thoughts?

Thanks

Peter

---

