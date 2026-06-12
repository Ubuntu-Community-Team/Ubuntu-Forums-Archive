---
title: "pptpd looses connection"
date: 2006-03-06
forum: Networking &amp; Wireless
---

### Post by ttallos on 2006-03-06
Is there any way to get pptpd to quit loosing a connection after 20 min or so. When I first set the box up it would work for 2-3 hours allowing a 400MB file to be sent to a neighbor home down the street we both have Cable. lately it just shuts itself off I am trying to send files across town now though and have no idea if this is part of the issue. here is a bit of the log file before I lost the conection....localhost pptpd[31807] GRE: Discarding out of order packet 
localhost last message repeated 9 times 
localhost last message repeated 7 times 
localhost pptpd[31807] CTRL: Received PPTP Control Message (type: 5) 
localhost pptpd[31807] CTRL: Made a ECHO RPLY packet 
localhost pptpd[31807] CTRL: I wrote 20 bytes to the client. 
localhost pptpd[31807] CTRL: Sent packet to client 
localhost pptpd[31807] GRE: Discarding out of order packet 
localhost last message repeated 10 times 
localhost last message repeated 6 times 
localhost pptpd[31807] CTRL: Received PPTP Control Message (type: 5) 
localhost pptpd[31807] CTRL: Made a ECHO RPLY packet 
localhost pptpd[31807] CTRL: I wrote 20 bytes to the client. 
localhost pptpd[31807] CTRL: Sent packet to client 
localhost pptpd[31807] GRE: Discarding out of order packet 
localhost last message repeated 7 times 
localhost pptpd[31807] GRE: read(fd=4,buffer=507c60,len=8196) from PTY failed: 
status = -1 error = Input/output error, usually caused by unexpected termination 
of pppd, check option syntax and pppd logs 
localhost pptpd[31807] CTRL: PTY read or GRE write failed (pty,gre)=(4,5) 
localhost pptpd[31807] CTRL: Reaping child PPP[31808] 
localhost pptpd[31807] CTRL: Client 24.98.88.73 control connection finished 
localhost pptpd[31807] CTRL: Exiting now

---

