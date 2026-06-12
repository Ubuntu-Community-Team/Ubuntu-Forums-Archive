---
title: "SSH: connection refused"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by cb951303 on 2009-11-11
Here is the original thread: [http://ubuntuforums.org/showthread.php?t=1323008](http://ubuntuforums.org/showthread.php?t=1323008)

I'm making a new one because the problem became independent from the previous thread subject thus I may have better luck with this one.

My problem is that I can't connect to my SSH server outside of the local network. When I try it I get this error: ```

ssh: connect to host XX.XX.XX.XX port 22: Connection refused

```

I already
1. Disabled ubuntu firewall: [http://pastebin.com/m4f11d9a](http://pastebin.com/m4f11d9a)
2. Forwarded port 22 from router, and set router firewall settings to allow SSH connections. Any online port scanner that I tried sees the port 22 as open.

I read a lot of threads about it but none of them recommends anything other than above 2 solutions(!)

I also tried adding ALL:ALL to /etc/hosts.allow just because it made sense but it didn't work.

Note that after every change I made I restarted the SSH service just to be sure.

Any help would be appreciated, thanks.

---

### Post by Iowan on 2009-11-11
Is there another "local" machine you can use to connect - not the server but on the same side of the router?

---

### Post by cb951303 on 2009-11-11
Yep, there is, and the result is same.
It can connect through local IP but it can't through global IP.

I also tried another service. Transmission web client. The result is the same. I can connect to transmission web client from local network but not from outside.

Just to make sure I disabled the firewall of the router and deleted all the firewall rules. Opened necessary ports with NAT/Port Forwarding. Restarted the router and scanned the ports from outside of the local network and confirmed that they are in fact open and firewall is not to blame.

I really can't think of anything else :confused:

---

### Post by Iowan on 2009-11-11
I'm not sure what the Transmission web client results are telling you, or I'd have suggested checking settings in */etc/ssh$/etc/ssh/sshd_config*.

---

### Post by cb951303 on 2009-11-12
I'm out of ideas. I tried apache, transmission and ssh. none of them worked but their ports are open and there is no firewall.

---

### Post by Iowan on 2009-11-12
Wish I knew a log file to have you check to see if it's the server refusing the connection(s).

---

