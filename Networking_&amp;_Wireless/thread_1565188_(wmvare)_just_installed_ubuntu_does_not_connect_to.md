---
title: "(wmvare) just installed ubuntu does not connect to the wireless network"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by dragonfly.000 on 2010-08-31
I have got an interesting problem. So please read patiently..
my host computer has windows xp op sys. I used to install ubuntu op sys on vmware and it used to connect to the internet automatically and ping to other ips. however now it does not. i want to underline again i have just installed ubuntu.

**1-**ifconfig results shows:

eth0      Link encap:Ethernet  HWaddr 00:0c:29:55:65:49  
          inet6 addr: fe80::20c:29ff:fe55:6549/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:317 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26715 (26.7 KB)  TX bytes:69091 (69.0 KB)
          Interrupt:18 Base address:0x1400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:880 (880.0 B)  TX bytes:880 (880.0 B)

problem is eth0 does not show inet addr after this line
=>inet6 addr: fe80::20c:29ff:fe55:6549/64 Scope:Link

**2-**
i opened interfaces file by using this command
-->gksudo gedit /etc/network/interfaces

and i restarted networking by
-->sudo /etc/init.d/networking restart

[B]2.1-
[/B]the result was as follows 

auto lo
iface lo inet loopback

**2.2-** 
after these lines, i added 

auto eth0
iface eth0 inet dhcp

then i restart networking again ...
(i also tried 'wlan' but i got error, there is no device or sth like this)


**3-**
I checked resolv.conf file as typing
gksudo gedit  /etc/resolv.conf

result: file was empty...

i tried to add 'nameserver 192.168.15.1' (which is my wireless router ip. it didnt work as well)


**ALSO**
I checked my network connections which shows all adapters I have got.. It seems, I have got 2 VMware adapter (VMNet1 - 192.168.28.1 and VMNet8 - 192.168.16.1)


 It does not ping anywhere at all. Can anyone help me to solve this problem.new installations were working properly before. I did nothing but it does not work now. there is a settings problem i know, but i dont know where it is.

**PS. **why i cannot see eth0 'ip addr '???
eth0    Link encap:Ethernet  HWaddr 00:0c:29:55:65:49  
[COLOR=Red]          HERE I suppose to see a line for ip addr[/COLOR]
          inet6 addr: fe80::20c:29ff:fe55:6549/64 Scope:Link

Any help is appreciated.
Thanks in advance..

---

