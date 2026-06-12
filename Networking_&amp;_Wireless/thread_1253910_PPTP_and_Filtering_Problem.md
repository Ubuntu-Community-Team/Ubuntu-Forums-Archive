---
title: "PPTP and Filtering Problem"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by knight9 on 2009-08-30
Hello everybody,

A couple of weeks ago I set up PPTP on my ubuntu VPS in order to give VPN access to my friends in Iran. Because of the filtering problem in Iran they are not able to have access to the web freely. But it seems like the government has somehow filtered PPTP and L2TP protocols, because no one could connect to the VPN server from Iran, since the server works properly for the other countries. 

Here is the log saved in syslog about a connecting attempt from Iran:
(I've modified the client's IP address)


```
Aug 28 17:30:49 root pptpd[18165]: CTRL: Client 91.18*.**.*** control connection started
Aug 28 17:30:49 root pptpd[18165]: CTRL: Starting call (launching pppd, opening GRE)
Aug 28 17:30:49 root pppd[18166]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Aug 28 17:30:49 root pppd[18166]: pppd 2.4.5 started by root, uid 0
Aug 28 17:30:49 root pppd[18166]: Using interface ppp0
Aug 28 17:30:49 root pppd[18166]: Connect: ppp0 <--> /dev/pts/0
Aug 28 17:30:49 root pptpd[18165]: GRE: Bad checksum from pppd.
Aug 28 17:30:50 root pptpd[18165]: CTRL: Ignored a SET LINK INFO packet with real ACCMs!
Aug 28 17:30:50 root pppd[18166]: MPPE 128-bit stateless compression enabled
Aug 28 17:30:52 root pppd[18166]: Cannot determine ethernet address for proxy ARP
Aug 28 17:30:52 root pppd[18166]: local  IP address 192.168.30.1
Aug 28 17:30:52 root pppd[18166]: remote IP address 192.168.30.234
Aug 28 17:38:19 root pppd[18166]: No response to 4 echo-requests
Aug 28 17:38:19 root pppd[18166]: Serial link appears to be disconnected.
Aug 28 17:38:19 root pppd[18166]: Connect time 7.5 minutes.
Aug 28 17:38:19 root pppd[18166]: Sent 16133 bytes, received 5433 bytes.
Aug 28 17:38:19 root pppd[18166]: MPPE disabled
Aug 28 17:38:22 root pppd[18166]: Connection terminated.
Aug 28 17:38:22 root pppd[18166]: Modem hangup
Aug 28 17:38:22 root pppd[18166]: Exit.
Aug 28 17:38:22 root pptpd[18165]: GRE: read(fd=6,buffer=611640,len=8196) from PTY failed: status = -1 error = Input/output error, usually caused by unexpected termination of pppd, check option syntax and pppd logs
```
Does anyone know how it's possible to solve this problem? I used CMAK to make the access easier for amateur users. Is there any other protocol that applications like CMAK support them?

Your help is really appreciated to help Iranian people have free access to information.

Thanks

---

### Post by juicyoner on 2009-09-02
bump

---

### Post by knight9 on 2009-09-10
> **juicyoner said:**
> bump
 
pardon me?!

---

