---
title: "Gigabit Networking"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by theamazingbeat on 2011-04-30
Okay so I need some help here please.

I have 2 Cat6 Ethernet cables, a gigabit router, two gigabit NIC's. But I am not getting gigabit speed. One machine is running windows and the other is running ubuntu 11.04 (beta 2) (but this has been happening since 10.10 but had no time to fix the issue).


 So I check on my windows machine and it says that my link speed is: 1.0Gbps/Full Duplex.
I check on my ubuntu machine and it says my link speed is: 1000 Mbp/s.

So I am trying to sftp something over and I am getting 9 megabytes per second. This is how it has been forever and I am taking time out to fix it but I don't know whats wrong. Or what I am doing wrong. Please help...

-Aaron

---

### Post by ajayahmed on 2011-05-06
Hello Aaron

I'm pretty sure you've been told by those who have no knowledge of networking that it's probably the server you're connected to. Don't pay attention to them.

The default TCP window sizes are so low it makes you want to slap the development team. For some reason they assume the TCP Window Scaling will optimise your connection but it will never improve throughput. Maybe that's why major companies never consider using Ubuntu on their servers.

I've successfully optimised my servers and the laptop I connect on occasion by following this guide: _[http://datatag.web.cern.ch/datatag/howto/tcp.html](http://datatag.web.cern.ch/datatag/howto/tcp.html)_[]("http://datatag.web.cern.ch/datatag/howto/tcp.html"). - This can also be used for users of the 30-50-100mbps service provided by the British Virgin Media ISP.

Please be careful as setting incorrect settings (too high or too low) can have adverse affects on your network. I would recommend you tweak a separate computer before applying changes to any of your live servers. But before all of that, do some more research on TCP throughput because some guides may only suit the author and may include/exclude modifications you might not/might want to make.

Also on a final note, there are no 'default settings' I can provide you that can guarantee maximum efficiency, it really depends on your network. If you are connected directly to an Internet Exchange than you have much more flexibility on customisation but if you are connected through collocation/data centre than you may find asking your providers network administrators as the best course of action.

Hope this helps.

Regards

---

### Post by jonsmirl on 2011-05-06
Check the lights around the network connectors of both machines. Make sure they are in the pattern that indicates GbE. I've had lightning destroy the GbE electronics in adapters and motherboards multiple times. If the GbE electronics are dead the 100Mb or 10Mb electronics silently take over.

---

### Post by theamazingbeat on 2011-05-06
I can guarantee that there is no interference. Yes the cat6 is utp. I wouldn't see why any other gigabIt network I have seen just worked properly, yet mine needs manually assigned resources. The drives are a WD 500GB 2.5 Black and a Seagate 7200 RPM 1TB 3.5, even If the drives speeds are not top notch, I should get higher than 9 Mb/s. I am positive that the drivers are up to date. I can see really think of *two issues: something wrong with my router (Dlink DIR-655) or something wrong with a windows or ubuntu setting/ config file ( most likey ubuntu). I can try transferring little files, big files, big folders, etc same thing.

---

### Post by dmizer on 2011-05-07
Have you had any success with any protocols other than FTP?

---

### Post by theamazingbeat on 2011-05-07
I have tried samba server, that didnt work either

---

### Post by bobwyajnr on 2011-05-08
Hi **theamazingbeat**

I would just like to confirm that I have seen CIFS transfers over my LAN (Gbit cat 5e) of 60 Mbytes/sec with Ubuntu 10.10 <-> Ubuntu 10.10 (OK Linux-Mint actually). That is without any jumbo frame support in my Gbit switch (an el-cheapo US Robotics one). I have only tweaked slightly tweaked my CIFS sharing settings and upgraded (the server end) to the 2.6.38 kernel. I haven't even touched the default TCP window size, etc.!

You are a little vague about which direction you transferring. To or from an sFTP server on Ubuntu 11.10 I would guess - right? Are transfers speeds symmetrically slow?

What about a connection in the reverse direction (e.g. a Windows sFTP server)? [Bitvise]("http://www.bitvise.com/") do one of the best (fastest) Windows sFTP servers on the market (with a free to use license that is not very restrictive - if you know about NTFS junction points :-) ). I would recommend trying/testing a transfer with the server-client relationship reversed.

Are you physically writing files to a disk? Is that an issue? (E.g. an NTFS partition at the Ubuntu end perhaps)? What about the full machine specs.? Amount of RAM and CPU type? Also I would presume you are using *Ext4* on the Ubuntu machine - but again you don't specify this... (:rolleyes:)

You've raised a big gap in my knowledge... Me thinks I need to research some more in depth network diagnostic/performance testing tools - since I've only really used *Wireshark* to date. :popcorn:

Bob

---

