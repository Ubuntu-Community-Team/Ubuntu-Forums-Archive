---
title: "Samba and remote desktop on usb drive"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by andrew_g on 2008-12-09
Hi, 
I have ubuntu 8.10 (up to date) installed on a usb hard drive. I can start it on at least 2 computers, but the shared folders and remote desktop only appear when booted from one machine. 

I have set home/andrew/music folder as shared, 

scenario 1
USB-drive boots Ubuntu on machine A, I can see shared folders in ubuntu (machine A) and in Puppy linux on machine B, 

scenario 2 (I boot same installation from usb drive on machine B)
USB-drive boots Ubuntu on machine B, I CAN NOT see shared folders in ubuntu (now on machine B) OR in Puppy linux on machine A, 

I think samba is set up as standard.
Really appreciate ANY help - Thanks in advanced

---

### Post by superprash2003 on 2008-12-09
do both those machines get a unique ip address?? are they able to ping each other?

---

### Post by andrew_g on 2008-12-09
Hi, yes, this is a client status report from my router, and I can confirm that both machines have unique ip address as reported
DHCP Clients
MAC Address-----IP Address-----Host Name
00:a1:72:10:05:c3-----192.168.1.4-----puppypc
00:9f:6c:a4:7a:0e-----192.168.1.2-----andrew-desktop

the above situation fails, but reversed, ie ubuntu on the fist MAChine, puppy on the second, works, so am puzzled here. Thanks

---

### Post by superprash2003 on 2008-12-10
it could be puppy doesnt recognize your ethernet card when connected to machine A.. post ifconfig output from terminal when puppy is connected to both machine A and B

---

### Post by andrew_g on 2008-12-10
Hi this is the ifconfig from puppy, note: on this machine there is also a wireless adapter but is unconfigured.
  
eth0      Link encap:Ethernet  HWaddr 00:60:72:10:05:C3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2364 errors:0 dropped:0 overruns:0 frame:0
          TX packets:137354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1875493 (1.7 MiB)  TX bytes:12821148 (12.2 MiB)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4277 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4277 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:452945 (442.3 KiB)  TX bytes:452945 (442.3 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0E:2E:90:3D:8C  
          inet addr:169.254.9.217  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:969050 (946.3 KiB)  TX bytes:385968 (376.9 KiB)

in puppy pnethood reports no samba servers can be found

puppy report machine 2 
# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:6C:A4:7A:0E  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:828 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5114 (4.9 KiB)  TX bytes:48551 (47.4 KiB)
          Interrupt:11 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:39588 (38.6 KiB)  TX bytes:39588 (38.6 KiB)
in puppy pnethood reports located samba shares on the other machine
I can ping from both machines ok,

Remember, I start ubuntu from a usb hard-drive, When I run ubuntu on one machine it can see it's own shares (via places/network/windows-network/workgroup/andrew-desktop...etc), but when I run it on the other machine it can not. Also I can not see shares on windows on the other machine,  could it be that ubuntu network stuff is setup only for one machine  - thanks

---

### Post by andrew_g on 2008-12-11
Hi, I have three pc's x,y and z. I have two win-xp boxes with shares on (pc-x and pc-y). On pc-z (ubuntu booted from usb) I can see the shares using firefox if I use smb://192.168.1.2 or smb://192.168.1.4 in the address bar, BUT Nautilus fails to display ANY shares, just shows a windows workgroup icon, when clicked displays nothing. - any suggestions - thanks

---

