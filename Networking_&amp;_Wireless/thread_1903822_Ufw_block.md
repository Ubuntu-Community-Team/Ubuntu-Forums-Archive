---
title: "Ufw block"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by rm06 on 2012-01-03
I have a couple of messages in my /var/log/syslog I am trying to decipher. My wife got a Mac (192.168.0.9) as a gift and I set up access to her nfs share on my Ubuntu server (192.168.0.100) and I have the following error a couple of times:
```
Jan  3 06:44:12 MyServer vmunix: [230819.117675] [UFW BLOCK] IN=eth0 OUT= MAC=00:12:3f:7b:d6:83:68:a8:6d:2c:ac:4a:08:00 SRC=192.168.0.9 DST=192.168.0.100 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55604 PROTO=TCP SPT=1021 DPT=2049 WINDOW=65535 RES=0x00 ACK FIN URGP=0
Jan  3 06:44:19 MyServer vmunix: [230826.074910] [UFW BLOCK] IN=eth0 OUT= MAC=00:12:3f:7b:d6:83:68:a8:6d:2c:ac:4a:08:00 SRC=192.168.0.9 DST=192.168.0.100 LEN=40 TOS=0x00 PREC=0x00 TTL=64 ID=52011 PROTO=TCP SPT=1021 DPT=2049 WINDOW=65535 RES=0x00 ACK RST URGP=0

```
I'm not sure exactly what port being blocked. Here is the output from ufw status:
```
To                         Action      From
--                         ------      ----
2049                       ALLOW       Anywhere
192.168.0.0/24/tcp         ALLOW       192.168.0.0/24/tcp
192.168.0.100 123/udp      ALLOW       192.168.0.0/24 123/udp
192.168.0.0/24 139/tcp     ALLOW       192.168.0.0/24 135/tcp
21/tcp                     ALLOW       Anywhere
8080/tcp                   ALLOW       Anywhere

```

---

### Post by sj1410 on 2012-01-03
TCP port 2049 is being blocked, its used for NFS. you need to open this on your ubuntu machine.


```
ufw allow from 192.168.0.9 to tcp port 2049
```

---

### Post by Doug S on 2012-01-03
To me port 2049 looks to be open already.
 
I think the entries in syslog are a result of confusion between the MAC and the Ubtuntu server during the termination phase of a TCP session. The TCP flags are the key. This type of thing is very common in linux as it tends to use a "half-dulpex" close sequence instead of a full 4 way FIN-ACK handshake close sequence. The connection tracking table already thinks the connection has been closed and has already forgotten about it (I think). When the first packet noted in the syslog file comes along (which is likely another FIN-ACK packet after a previous one), it gets interpreted by iptables as a new connection without the proper SYN bit set and others reset, and get rejected. The MAC then tried to reset the connection via a RST packet, but the same conditions apply.
Is your wife having any troubles accessing the share? If no, then don't worry about it. If yes, then my analysis and text above might be incorrect.

---

### Post by rm06 on 2012-01-03
> **Doug S said:**
> To me port 2049 looks to be open already.
Is your wife having any troubles accessing the share? If no, then don't worry about it. If yes, then my analysis and text above might be incorrect.

The port is open, at least according to UFW. I'm not sure if the Mac is connecting or not as it is a new OS for my wife and she isn't yet too proficient with it, I will check later tonight to see what is happening as I was viewing my server logs from work.

---

### Post by rm06 on 2012-01-04
I am able to get to the nfs shares from the Mac and view files and folders without a problem. So ignore the error messages at this point?

---

### Post by Doug S on 2012-01-04
> **rm06 said:**
> I am able to get to the nfs shares from the Mac and view files and folders without a problem. So ignore the error messages at this point?Yes.

---

