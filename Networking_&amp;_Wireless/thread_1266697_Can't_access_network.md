---
title: "Can't access network"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by chloraphil on 2009-09-14
I can't access any network resources.  I'm a frequent user of mythbuntu box, but my troubleshooting skills are weak.  

I am behind a router (Tomato).

8.04

ifconfig output: (some obfuscation of IPs/MACs - also, VMWare Player is installed)

eth0      Link encap:Ethernet  HWaddr 00:11:22:33:44:55  
          inet6 addr: fe80::aaa:aaaa:aaaa:aaaa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6881 (6.7 KB)  TX bytes:492 (492.0 B)
          Interrupt:252 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26604 (25.9 KB)  TX bytes:26604 (25.9 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.177.1  Bcast:172.16.177.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.65.1  Bcast:192.168.65.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Thanks!

---

### Post by Iowan on 2009-09-15
Is eth0 supposed to get address via DHCP or static address?

---

### Post by chloraphil on 2009-09-15
Eventually, static, but I figured it would be easier to get it working via dhcp.  DHCP is fine, I can assign it a static lease in Tomato.

---

### Post by Iowan on 2009-09-15
See if [this]("http://ubuntuforums.org/showthread.php?t=1156441") one helps.  I still haven't worked with virtual, so the vmnet interfaces are foriegn to me.

---

### Post by chloraphil on 2009-09-15
I uninstalled vmware and that removed the vmnet interfaces to make things simpler. 

After that I could ping IP addresses but not google.com, so dns isn't working.  If I run dhclient then everything works until a reboot.

I've tried editing resolv.conf by hand but when I reboot it seems to be overwritten (it's blank except for the first two lines which are commented).  I've also added my router's IP to the DNS tab of the network configuration applet but that doesn't survive a reboot.  My router is running Tomato.

Any ideas?  Should I post a new thread with my dns-specific issues?

---

### Post by Iowan on 2009-09-16
DHCP might overwrite **/etc/resolv.conf**, but you can use the "prepend" line in */etc/dhcp3/dhclient.conf* to push your preferred servers to the top. Is your interface configured via Network Manager or */etc/network/interfaces*?
Both methods *should* have a way to auto-start.

---

### Post by chloraphil on 2009-09-16
I have no idea if my interfaces are configured one way or the other.  How can I tell?

How can I tell if one or the other is configured to auto-start?

---

### Post by Iowan on 2009-09-16
Check contents of */etc/network/interfaces*. It *should* have only an entry for "lo". If eth0 is defined there, it should also have an "auto eth0" line.  I skipped Hardy and Intrepid, so I don't know what the NM applet looks like, but Jaunty has an option to "Connect automatically".

---

