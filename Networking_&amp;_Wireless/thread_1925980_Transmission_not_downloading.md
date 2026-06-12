---
title: "Transmission not downloading"
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by gjw0 on 2012-02-15
I'm using the latest version of Ubuntu and Transmission.According to Transmission, the file I am downloading has 0 peers and is idle, even though there are a few peers seeding it.

Here's a batch of error messages from Transmission's log:*Could not connect to tracker. Tracker gave HTTP response code 503, 504*

This is the firewall's status:[I]To Action From -- ------ ---- 51413/tcp ALLOW Anywhere 51413/udp ALLOW Anywhere 51413/tcp ALLOW Anywhere (v6) 51413/udp ALLOW Anywhere (v6) 51413/tcp ALLOW OUT Anywhere 51413/udp ALLOW OUT Anywhere 25,53,80,110,443/tcp ALLOW OUT Anywhere 53/udp ALLOW OUT Anywhere 67,68/udp ALLOW OUT Anywhere 5050/tcp ALLOW OUT Anywhere 51413/tcp ALLOW OUT Anywhere (v6) 51413/udp ALLOW OUT Anywhere (v6) 25,53,80,110,443/tcp ALLOW OUT Anywhere (v6) 53/udp ALLOW OUT Anywhere (v6) 67,68/udp ALLOW OUT Anywhere (v6) 5050/tcp ALLOW OUT Anywhere (v6)

[/I]Also, Transmission says that port 51413 is open.

How can I fix this?

---

### Post by elliotbeken on 2012-02-15
What i would do it try to download a torrent with many peers and see if that works. Here is a good torrent to test/try as i know i am seeding it on a dedicated server:

[http://releases.ubuntu.com/11.10/ubuntu-11.10-alternate-amd64.iso.torrent](http://releases.ubuntu.com/11.10/ubuntu-11.10-alternate-amd64.iso.torrent)

Hope this helps Elliot

---

### Post by gjw0 on 2012-02-15
> **elliotbeken said:**
> What i would do it try to download a torrent with many peers and see if that works. Here is a good torrent to test/try as i know i am seeding it on a dedicated server:

[http://releases.ubuntu.com/11.10/ubuntu-11.10-alternate-amd64.iso.torrent](http://releases.ubuntu.com/11.10/ubuntu-11.10-alternate-amd64.iso.torrent)

Hope this helps Elliot

I downloaded the torrent. Transmission still says that it's idle and has 0 peers. And the message log reads, "Could not connect to tracker.".

Edit: Here's the firewall log:

**Feb 15 20:07:21 ubuntu kernel: [ 4200.736106] [UFW BLOCK] IN= OUT=ppp0 SRC=my ip DST=91.189.90.143 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=4917 DF PROTO=TCP SPT=33948 DPT=6969 WINDOW=4344 RES=0x00 SYN URGP=0 **

---

### Post by gjw0 on 2012-02-17
Running "sudo ufw allow out 6969/tcp" fixed my problem.

---

