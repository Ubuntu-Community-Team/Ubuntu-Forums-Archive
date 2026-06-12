---
title: "ADSL connection"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by thire on 2006-06-30
I just installed my shipit CD 6.06 and then I followed the instructions at [http://nic.tuwien.ac.at/tunet/adsl/linux.html](http://nic.tuwien.ac.at/tunet/adsl/linux.html) (geman) to connect to the internet via a Alcatel SpeedTouch 510.
I installed (downloaded on a stick) pptp 1.7.0 and changed the ip-adress, netmask and broadcast. Then changed the /etc/ppp/options and the /etc/ppp/chap-secrets and pap-secrets. Finally I changed the /etc/resolf.conf.
Everything as described in the above link.
Still I get nothing (not permitted), when I try pptp 10.0.0.138 or the same with sudo.
Any suggestion?

---

### Post by thire on 2006-07-01
To be exactly, I get these errors.

> thire@thire-laptop:~$ pptp 10.0.0.138
anon warn[pptp_gre_bind:pptp_gre.c:82]: socket: Operation not permitted
anon fatal[main:pptp.c:275]: Cannot bind GRE socket, aborting.
thire@thire-laptop:~$ sudo pptp 10.0.0.138
Password:
anon warn[open_inetsock:pptp_callmgr.c:326]: connect: No route to host
anon fatal[callmgr_main:pptp_callmgr.c:124]: Could not open control connection to 10.0.0.138
anon fatal[open_callmgr:pptp.c:426]: Call manager exited with error 256
anon fatal[main:pptp.c:310]: Child process died
thire@thire-laptop:~$ ping 10.0.0.138
PING 10.0.0.138 (10.0.0.138) 56(84) bytes of data.
From 10.0.0.140 icmp_seq=2 Destination Host Unreachable
From 10.0.0.140 icmp_seq=3 Destination Host Unreachable
From 10.0.0.140 icmp_seq=4 Destination Host Unreachable

--- 10.0.0.138 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3
thire@thire-laptop:~$


---

### Post by mips on 2006-07-02
Search for 'Speedtouch' here. There are also guides in the howtos section of the forum.

---

