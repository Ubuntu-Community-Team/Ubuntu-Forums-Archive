---
title: "Wired connection Cannot connect to internet :("
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by MAD_JIHAD on 2009-03-25
Ok i just did a fresh instal of ubuntu 8.10 and i cannot connect to the internet, Im using a wired connection and it worked on the live cd so i dont know why it wont work now.

My other ubuntu pc connects fine using the same router it just worked automaticaly so its not the router or internet that doesnt work, also the cable works because i can plug it into my xbox and connect to the internet.

Any help is much appreciated :)!


/sigh i just want to run folding at home on this pc lol...

---

### Post by Iowan on 2009-03-25
Post results of *ifconfig -a* and contents of */etc/network/interfaces*. Are you getting IP address via DHCP (as opposed to setting static)?

---

### Post by MAD_JIHAD on 2009-03-25
madjihad@madjihad-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37132 (37.1 KB)  TX bytes:37132 (37.1 KB)

pan0      Link encap:Ethernet  HWaddr 8a:0e:ef:18:35:8a  
          inet6 addr: fe80::880e:efff:fe18:358a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)

edit: heres the contents of the interfaces file

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

edit: hm i restarted then booted into the live cd which i installed ubuntu from and i was able to connect to the internet, then i restarted back into my actual instal of ubuntu and it worked? strange well i guess it fixed its self, thanks for the quick reply though.

---

