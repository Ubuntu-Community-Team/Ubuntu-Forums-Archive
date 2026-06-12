---
title: "Dead NIC?"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by ubun2ibun3 on 2010-02-28
I transfered my music library to an older computer of mine, which is running Hardy 8.04.1, before I upgraded my better computer.  Now I wanted to move it back using a crossover cable, so I linked them up, setup XP as the host (192.168.0.1) and Hardy as 192.168.0.2.  They were pinging fine and everything, but when I started the transfer of my music folder in the form of a tarball over FTP, it started just fine and just stopped.  I tried pinging one another, and it wasn't working.  I reboot both and it still wouldn't work, and on the Ubuntu machine, there isn't even any ethX network devices listed!  The network card was older, and I suppose it is possible it just crapped out, but would that really happen just like that?

---

### Post by Iowan on 2010-02-28
Sounds like it could have happened. You can check **sudo lshw -C network** - but it sounds like you've already confirmed problem...

---

