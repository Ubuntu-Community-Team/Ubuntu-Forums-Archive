---
title: "Increasing network throughput"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by auren on 2010-04-02
Hi, guys. I've a bit of a problem with the networking at home. I have 2 computers and 1 NAS. I've enabled FTP on my NAS. Both PCs used to be windows based but after one got infected by a virus, I thought of trying out ubuntu. Before, both PCs can do 40MB/s when transferring large files using filezilla. Now, the ubuntu pc only does 1.5MB/s using filezilla too. I think I just need to tweak the settings for ubuntu or maybe not. Can anyone help? or point me to the right direction? Posts, links, etc.

---

### Post by iponeverything on 2010-04-02
> **auren said:**
> Hi, guys. I've a bit of a problem with the networking at home. I have 2 computers and 1 NAS. I've enabled FTP on my NAS. Both PCs used to be windows based but after one got infected by a virus, I thought of trying out ubuntu. Before, both PCs can do 40MB/s when transferring large files using filezilla. Now, the ubuntu pc only does 1.5MB/s using filezilla too. I think I just need to tweak the settings for ubuntu or maybe not. Can anyone help? or point me to the right direction? Posts, links, etc.

Need more details on your setup.

---

### Post by auren on 2010-04-02
> **iponeverything said:**
> Need more details on your setup.

AMD LE-1300
motherboard MSI K9AGM3-F (690G chipset)
1Gbps ethernet port (built in)
1.5GB RAM DDR2-667
400GB IDE WD

Software:
Ubuntu 9.10
2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux - when I type "uname -a" in terminal


2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         txqueuelen:1000 
          Interrupt:30 Base address:0xe000 


running filezilla 3.2.7.2


That's as much as I can gather on my own.

Is it really possible to reach 70-80 MB/s? hehe.

It isn't necessary to do FTP. If anyone else has a solution for reliable and fast file transfer via network, I'd appreciate the help.

NAS: using Thecus N5200 Pro. RAID5.

---

### Post by iponeverything on 2010-04-03
> **auren said:**
> AMD LE-1300
motherboard MSI K9AGM3-F (690G chipset)
1Gbps ethernet port (built in)
1.5GB RAM DDR2-667
400GB IDE WD

Software:
Ubuntu 9.10
2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux - when I type "uname -a" in terminal


2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

         UP BROADCAST MULTICAST  MTU:1500  Metric:1
         txqueuelen:1000 
          Interrupt:30 Base address:0xe000 


running filezilla 3.2.7.2


That's as much as I can gather on my own.

Is it really possible to reach 70-80 MB/s? hehe.

It isn't necessary to do FTP. If anyone else has a solution for reliable and fast file transfer via network, I'd appreciate the help.

NAS: using Thecus N5200 Pro. RAID5.

Something is messed up. I have reached 80 MB/s with going through catalyst with Gigabit fiber to the server and copper to client. The client was linux box using intel ethernet hardware. 

Run some tests going host to host via a x-over.

---

### Post by auren on 2010-04-03
> **iponeverything said:**
> Something is messed up. I have reached 80 MB/s with going through catalyst with Gigabit fiber to the server and copper to client. The client was linux box using intel ethernet hardware. 

Run some tests going host to host via a x-over.

You lost me after saying something is messed up hehehe. what's catalyst? x-over ... did you mean a crossover cable?

---

### Post by iponeverything on 2010-04-03
> **auren said:**
> You lost me after saying something is messed up hehehe. what's catalyst? x-over ... did you mean a crossover cable?

oh.. catalyst is just a line of cisco switches..

And and yes x-over is crossover. Just a regular cable with the send and receive pairs crossed. (1-3, 2-6) 

 Are you running directly into the NAS or are going through another piece of hardware? Run "ifconfig" and see if you seeing errors. Also run "sudo ethtool eth0" to see the negotiated speed.

---

### Post by auren on 2010-04-07
> **iponeverything said:**
> oh.. catalyst is just a line of cisco switches..

And and yes x-over is crossover. Just a regular cable with the send and receive pairs crossed. (1-3, 2-6) 

 Are you running directly into the NAS or are going through another piece of hardware? Run "ifconfig" and see if you seeing errors. Also run "sudo ethtool eth0" to see the negotiated speed.

Sorry I forgot to mention, I'm using a dlink 655 as my router and then a dgs-1008 under it. Both PCs and NAS are connected to the dlink switch (dgs-1008 )

---

