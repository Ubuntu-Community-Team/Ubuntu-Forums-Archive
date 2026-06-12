---
title: "After raring upgrade I can't connect to virtual box from Remmina RDP"
date: 2013-06-12
forum: Networking &amp; Wireless
---

### Post by twinturbotom on 2013-06-12
There is a windows machine on my network which usually runs an oracle Vbox virtual box in headless mode.  I used to connect to both the windows machine and the VM on it through Remmina RDP on a regular basis.

I upgraded to Raring and now I cannot connect to the Virtual machine with RDP!  I can reach the VM files in terminal and nautilus and I can connect to the main machine with RDP.  I can also connect to the VM with RDP on all other machines and devices.

I re-created the connection in RDP and still can't connect to the VM with RDP.  I'm not sure where to start.  RDP raring libraries? RDP package?

Ideas? Any direction is appreciated.

Thanks

---

### Post by twinturbotom on 2013-06-16
So I pinged my machine successfully and noticed the ping output added something to the DNS name:
~$ ping NAME-PC
PING NAME-PC (192.168.0.100) 56(84) bytes of data.
64 bytes from tmello-PC.PK5001Z (192.168.0.100): icmp_req=1 ttl=128 time=1.11 ms

I was able to connect with RDP using NAME-PC.PK5001Z 

Don't need to do that from any other computer on the network!  wonder why on raring?


Thoughs?

---

