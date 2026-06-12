---
title: "Networking concernson a Poweredge"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by reev3r on 2008-12-30
I installed Ubuntu 8.04 last night on a Dell Poweredge 1600sc with an Intel gigabit Ethernet controller. I am not exactly certain how to explain the issue, but I will do my best. It seems that the network only transmits/receives once a second, In the network monitor I get a spike up to gigabit speeds about once a second, up/down/up/down/up/down and so on and so on, so it averages speeds of about 11MBytes/sec. I have run benchmarks on my disks and they seem to be reading and writing just fine, I have four 36Gb SCSI drives in a RAID5 array, and one 500GB drive on a 3ware 8506 RAID controller not part of an array. Again, when testing both logical disks, they get expected speeds. I have another Ubuntu 8.04 server that is getting gigabit speeds over my network. Any help would be appreciated.

**Update**

When using iperf on the two 8.04 machines I get speeds of around 300 Mbits/sec with the server having the issue as client, however, when reversing the roles, and the server in question is set as server, I am getting around 420 Mbits/sec average.

Thank you,

~Jacob

---

### Post by tech9 on 2008-12-30
> **reev3r said:**
> I installed Ubuntu 8.04 last night on a Dell Poweredge 1600sc with an Intel gigabit Ethernet controller. I am not exactly certain how to explain the issue, but I will do my best. It seems that the network only transmits/receives once a second, In the network monitor I get a spike up to gigabit speeds about once a second, up/down/up/down/up/down and so on and so on, so it averages speeds of about 11MBytes/sec. I have run benchmarks on my disks and they seem to be reading and writing just fine, I have four 36Gb SCSI drives in a RAID5 array, and one 500GB drive on a 3ware 8506 RAID controller not part of an array. Again, when testing both logical disks, they get expected speeds. I have another Ubuntu 8.04 server that is getting gigabit speeds over my network. Any help would be appreciated.

Thank you,

~Jacob

sounds like something is chattering between your devices. what kind of servers did you implement?

---

### Post by reev3r on 2008-12-30
For the sake of easy identification the names are as follows:

Survage is the 8.04 that functions properly
Serpent is the 8.04 that is having the network issues.

Survage currently has a VNC server, Gnump3d server, samba, ftp, and ssh, I think that is all on that one.

Serpent currently only has samba installed and functional.

---

### Post by reev3r on 2008-12-30
I just made a ramdisk to test and further see if it is the Ultra320 SCSI RAID array or the sata raid controller for the 500GB and I get the same results. I am going to try to procure another NIC and see if the issue persists. I will keep updating as new ideas/results come along.

**Update**

Attached a photo. This is a transfer of a 700MB file to the ramdisk, as you can see, the transfer is consistently intermittent. There is a burst of roughly 70+/- MBytes/sec and then drops down to 0.

~reev3r

---

### Post by tech9 on 2008-12-30
> **reev3r said:**
> I just made a ramdisk to test and further see if it is the Ultra320 SCSI RAID array or the sata raid controller for the 500GB and I get the same results. I am going to try to procure another NIC and see if the issue persists. I will keep updating as new ideas/results come along.

**Update**

Attached a photo. This is a transfer of a 700MB file to the ramdisk, as you can see, the transfer is consistently intermittent. There is a burst of roughly 70+/- MBytes/sec and then drops down to 0.

~reev3r

wow, that is very bizarre. Its almost like the bandwidth should stay constant, but is dropping packets in a continuous pattern.

Well the only thing I can think of is to run a sniffing program on that server. I am not too sure about sniffing apps in linux. I usually use a program called "wireshark" at work - but this is an MS app. maybe it will run in wine - not sure.

Anyway, thats all I can think of now, to try to pinpoint packets/packet loss - which that is what it looks like from your screenshot.

You may be on to something with trying another NIC, could also be a faulty NIC.

good luck,

T9

---

