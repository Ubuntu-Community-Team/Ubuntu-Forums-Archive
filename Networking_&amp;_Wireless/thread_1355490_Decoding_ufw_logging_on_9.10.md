---
title: "Decoding ufw logging on 9.10"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by avdiscolo on 2009-12-15
I am a brand new ubuntu user.  Can someone tell me how to determine what service is being blocked and how to fix it?  I have a home network of Windows, Mac, and now one Ubuntu machine.

```
Dec 14 21:50:18 ubuntu0 kernel: [90944.989219] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:26:c2:93:08:00 SRC=192.168.0.12 DST=255.255.255.255 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=26842 PROTO=UDP SPT=63380 DPT=15582 LEN=20 
Dec 14 21:50:18 ubuntu0 kernel: [90944.989314] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:26:c2:93:08:00 SRC=192.168.0.12 DST=255.255.255.255 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=26843 PROTO=UDP SPT=63385 DPT=15582 LEN=20 
Dec 14 21:53:17 ubuntu0 kernel: [91123.956405] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:26:c2:93:08:00 SRC=192.168.0.12 DST=192.168.0.255 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=26981 PROTO=UDP SPT=59302 DPT=15582 LEN=20 
Dec 14 21:53:17 ubuntu0 kernel: [91123.992948] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:26:c2:93:08:00 SRC=192.168.0.12 DST=192.168.0.255 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=26982 PROTO=UDP SPT=59303 DPT=15582 LEN=20 
Dec 14 21:53:17 ubuntu0 kernel: [91123.992986] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:26:c2:93:08:00 SRC=192.168.0.12 DST=192.168.0.255 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=26983 PROTO=UDP SPT=59304 DPT=15582 LEN=20 
Dec 14 21:53:18 ubuntu0 kernel: [91124.951518] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:26:c2:93:08:00 SRC=192.168.0.12 DST=255.255.255.255 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=26984 PROTO=UDP SPT=59305 DPT=15582 LEN=20 
Dec 14 21:53:18 ubuntu0 kernel: [91124.991637] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:26:c2:93:08:00 SRC=192.168.0.12 DST=255.255.255.255 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=26985 PROTO=UDP SPT=59306 DPT=15582 LEN=20 
Dec 14 21:53:18 ubuntu0 kernel: [91124.991675] [UFW BLOCK] IN=eth0 OUT= MAC=ff:ff:ff:ff:ff:ff:00:18:8b:26:c2:93:08:00 SRC=192.168.0.12 DST=255.255.255.255 LEN=40 TOS=0x00 PREC=0x00 TTL=128 ID=26986 PROTO=UDP SPT=59307 DPT=15582 LEN=20 

```Thanks,
Anthony

---

### Post by MaindotC on 2009-12-15
Try:
```

man ufw

```

---

### Post by avdiscolo on 2009-12-15
I suppose I should have been more precise in constructing my previous post.

I've already successfully installed ufw exceptions for vnc and the group of netbios services.  I've read the man pages for ufw(8), ufw-framework(8), and iptables(8).  I've also done searches on this forum on configuring ufw and on the ubuntu documentation web site.  I know there are many very helpful and knowledgeable people here.

Specifically, I can see that there are 1 broadcast and 1 multicast addresses in question, both using port 15582.  But I haven't been able to figure out what service that port is related to.

Thanks.

---

### Post by avdiscolo on 2009-12-16
I ran wireshark and figured out what where those packets were coming from.  The ones sent to 255.255.255.255 were a DHCP Inform message and the ones to 192.168.0.255 were a NBS name query.

---

### Post by MaindotC on 2009-12-16
Well those shouldn't be blocked.  How did you resolve the issue?

---

### Post by avdiscolo on 2009-12-16
I didn't resolve it.  I couldn't find any services running on my system that were related to these message types.  I'm not running a DHCP or WINS server.
 
How do you recommend that I solve this?
 
Thanks.

---

### Post by peepingtom on 2009-12-16
If you don't want to learn about the fine points of UFW, there's a GUI called gufw. It's in the main repositories now, you can install it with with [apt:gufw](apt:gufw)

---

