---
title: "cannot ping internet"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by sam_grz on 2011-10-24
system is Ubuntu server 11.04
very excited to install Ubuntu server in my office, problem is i cannot ping outside adsl router (windows pc connected to lan do ping)
ping works fine in lan (also SSH, ftp, VNC...) but no internet ..
went looking for a solution but nothing till now, please help:

btw , i can ping router (128.1.1.254) , also the internet ip of
the router but nothing beyond (ex 8.8.8.8 of Google) ?? weird

/etc/network/interfaces
=======================
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 128.1.1.1
netmask 255.255.255.0
network 128.1.1.0
broadcast 128.1.1.255
gateway 128.1.1.254
dns-nameservers 8.8.8.8
dns-search xxx.com

route -n
========
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
128.1.1.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         128.1.1.254     0.0.0.0         UG    100    0        0 eth0

---

### Post by dandnsmith on 2011-10-24
What sort of error messages do you get from:
ping google.com
traceroute google.com
I can't, immediately, see what might be wrong, but it has to be something like dns resolution or router blocking.
As an afterthought, are the Windows PCs using IP4 or IP6? and is this the same as you are set for on ubuntu server?

---

### Post by sam_grz on 2011-10-24
Derek, Thank you for helping indeed.
ok, replies to your questions :
- looks like router-or-server blocking , as ping 8.8.8.8 gives no feedback... so i dont take care of DNS really
- i have disabled IP6 in ubuntu server (after fresh installation)
- and windows pcs (i want to get away..) are using IP4

Sam

---

### Post by dandnsmith on 2011-10-24
I'm feeling a bit non-plussed now as to what to suggest.
If you can ping other machines on your LAN (and see the replies), is it possible that you have a firewall blocking the returns (selectively)?
Can other machines on the LAN ping the ubuntu server?

I've only ever heard of one router problem of this type - UK BT Homehub, which was selective against linux (which it could identify by the packet content, somehow).

---

### Post by sam_grz on 2011-10-24
i am not in my office now, but i will provide you with some replies.
other pcs (windows) on lan can ping ubuntu server (even VNC and FTP in)
i made a fresh install of Ubuntu server so i suppose firewall is off by
default, the worst case is that ISP is blocking ?? but why on earth they block ? as i changed one of the windows pc's IP to 128.1.1.1 (which is the Ubuntu server static IP) and it pinged internet fine.

---

### Post by dandnsmith on 2011-10-25
Sam, we're now at the situation where, to advance further, you need to supply more info and try something new.

Ubuntu version
Windows PC version
Router details

I suggested, earlier in the thread, traceroute (tracert on PC), but you haven't provided any results.

---

### Post by sam_grz on 2011-10-25
Derek, i must thank you for all the help , as i contacted my ISP , router was changed and Ubuntu connected to the internet finally.
turned out to be an old router.
what i will never understand is why windows do ping and not ubuntu ?
ubuntu must rely on some special network configation.
anyway, thank you and all the best :)

---

### Post by dandnsmith on 2011-10-25
Glad it's resolved - you should mark this thread *SOLVED* now

---

