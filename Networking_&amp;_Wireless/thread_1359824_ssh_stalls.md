---
title: "ssh stalls"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by z987k on 2009-12-20
recently, ssh has been stalling on a remote computer(over wan - not tested lan, I'm not close enough right now).  It happens whenever it is asked to do something the may be "large" if you will.
For example, ls on a directory with 2 files works, but ls on a directory with 10 files just freezes up and I have to recconect.  So we're not talking large amounts of data going over the net.  vi or nano on syslog also fails, presumably for the same reason, and trying to scp a file also stalls.
I can cd through the entire filesystem fine, so long as I know where I'm going.  
Commands like stopping and starting services works, vi/nano of small files works.
I can ls > tempout of any size directory and then view that file.

I noticed the ssl on the client and server are different.
Client: OpenSSH_5.1p1, Openssl 0.9.8h
Server: OpenSSH_5.1p1, Openssl 0.9.8g

tail auth.log and syslog don't reviel anything related to ssh or ls except for the login/close of a user via ssh.

I'm not sure where else to go with this.

---

### Post by SecretCode on 2009-12-20
Could it be something to do with MTU sizes? What you're seeing could be triggered by packets close to 1500 bytes but not by small packets.

A LAN test would be instructive. Also, do you have any wireless links in the route?

Can you ping the remote computer with increasing sizes and the 'do not fragment' bit set?

Something like (not tested yet)
```
ping -s 1000 -M do 192.168.0.1
```

---

### Post by albandy on 2009-12-20
As SecretCode says, could be an mtu size problem.
Are you connecting by phone(3G/GPRS) or to a VPN?

For example, if connecting to a VPN you should decrease the MTU size to 1492 or less, and some 3G/GPRS services don't support an MTU bigger than 500

---

### Post by z987k on 2009-12-20
Sorry about not giving more information.

The client is a laptop running linux and the server is my home desktop running linux.

I tried pinging, but I think my router is blocking it.  

How would I go about setting the MTU for ssh?

The client is wireless, but would that matter?  Server is wired, and no wireless links or anything.

---

### Post by SecretCode on 2009-12-20
> **z987k said:**
> I tried pinging, but I think my router is blocking it.
So if you type _ping your.server.com_, what do you get - a timeout? What do you get if you type _ping -s 2000 -M do your.server.com_? (Where your.server.com is - obviously - whatever name or IP address you're using in the ssh connection.)

> **z987k said:**
> How would I go about setting the MTU for ssh?
Hmm. Let's see if it's the problem first.

> **z987k said:**
> The client is wireless, but would that matter?  Server is wired, and no wireless links or anything.
Wireless links sometimes introduce lower MTU limits - if the end points don't know about it, you can lose packets.

---

### Post by z987k on 2009-12-21
yes pinging the server times out.  I think the router that the copmuter is behind is blocking them.

---

### Post by z987k on 2009-12-23
well it appears to be the local isp's problem. - mediacom for what it's worth.  I can connect and everything works just fine from multiple other points around here with different isp's.

---

