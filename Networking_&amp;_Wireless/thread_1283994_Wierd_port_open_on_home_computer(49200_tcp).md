---
title: "Wierd port open on home computer(49200 tcp)"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Promille on 2009-10-06
Hey.

I recently did a scan of localhost (my comp) to check for any security issues, and I have a wierd port open, 49200 on the TCP protocol.
And I cant assiocate this with anything, neither have I never installed any server/daemon running on this high port number. I did an nmap scan too, but nmap had no other info besides it was open.

I decided to do i wireshark, filtering only on that port. After about an hour i got two responses right after eachother: 
1)
810058	2439.183864	192.168.xx.xxx (the internal adress to the home computer this is regarding)	81.167.xxx.xx (the external adress, which is shared for the whole home net, not more than 2 pc's tho)	TCP	41482 > 64200 [SYN] Seq=0 Win=2048 Len=0 MSS=1460
2)810589	2439.311406	81.167.xxx.xx	192.168.xx.xxx	TCP	64200 > 41482 [RST, ACK] Seq=1 Ack=1 Win=0 Len=0
(same ip adress, just reversed)

I can't find port 41482 open though.

Thanks for any help.

/Promille

---

### Post by cj.surrusco on 2010-09-05
I know I'm a year late, but for anybody that might view this thread, 49200 is the default for UPnP, or atleast with uShare, it is.

---

