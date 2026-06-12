---
title: "openVPN client  No buffer space available (code=105)"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by sandrocchio_0.1 on 2010-01-26
Hi there,
I'm using OpenVPN 2.1 on Ubuntu 8.10 to connect to LAN behind an IPCOP server.
Everything works fine except when I move across the tunnel files which are over 180kb, then I get

 UDPv4 []: No buffer space available (code=105)

surfing the Internet I've found post that suggest to increase these settings on the kernel

>  sysctl -w net.core.rmem-max=8388608
>  sysctl -w net.core.wmem-max=8388608
>  sysctl -w net.core.rmem-default=65536
>  sysctl -w net.core.wmem-default=65536

those have actually made a small difference, but not enough for uploading even an image over http. 
I guess that I can keep increasing those values till I'm not satisfied, but as I'm not sure on what I am dealing with, can anyone tell me if there's a rule of thumb?

My machine is a laptop with a dual core processor and 2GB ram.

Thanks in advance

Alessandro

---

### Post by sandrocchio_0.1 on 2010-01-26
This evening I tried to run OpenVpn client with --mtu-test parameter and I got the following result

Tue Jan 26 23:51:14 2010 Initialization Sequence Completed
Tue Jan 26 23:51:17 2010 NOTE: Beginning empirical MTU test -- results should be available in 3 to 4 minutes.
Tue Jan 26 23:54:25 2010 NOTE: Empirical MTU test completed [Tried,Actual] local->remote=[1437,1389] remote->local=[1437,1437]
Tue Jan 26 23:54:25 2010 NOTE: This connection is unable to accomodate a UDP packet size of 1437. Consider using --fragment or --mssfix options as a workaround.

---

