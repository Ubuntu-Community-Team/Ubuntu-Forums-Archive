---
title: "nautilus vs scp"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by iponeverything on 2010-07-12
Not a question, just an observation and potential project. 

Moving a 13 Gig uncompressed archive over a wireless N connection, I see almost twice the throughput from ssh2 using scp from command line than when using the nautilus ssh implementation though the "Places->Connect to server" drag and drop ssh connect method.  

scp:

```
2002-windows.tar                     8% 1202MB  10.8MB/s   19:14 ETA

```

nautilus ssh file copy image attached:

Gist -- 5.2 MB/sec for same file from same location.

Tested multiple times under the same conditions. The switch ports on the wireless router are 100 Mbps, so with the scp and 10.8 MB/s throughput, I am running up against the 100 Mbps switch port -- 10.8 MB/s = 86.4 Mbps. 

I first noticed it when I switched to Ubuntu 8.10 from strait Debian. It just looks like nautilus could use a better ssh2 implementation - just a hypothesis based on limited observation.  

If someone is looking for a good project to spruce up their resume and collect some good FOSS Karma -- I am sure it would provide hours of enjoyment. 

The wireless router:
Linksys WRT160Nv3 running DD-WRT v24-sp2 (11/25/09) std-nokaid-nohotspot - build 13309M

Client:
Lenovo x200 P8600 c2d and Intel 5100 wireless running 10.04 64 bit.

---

