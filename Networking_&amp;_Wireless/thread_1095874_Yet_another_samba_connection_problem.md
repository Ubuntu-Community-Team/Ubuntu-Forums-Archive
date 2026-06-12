---
title: "Yet another samba connection problem"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by dreaminhere on 2009-03-14
I upgraded from 8.04 to 8.10 and now my windows xp box can't connect to my linux box via Samba.  I have them connected directly together with a cat 5 cable. Samba is on my Linux box.  I've tried to ping my windows box from my Linux box and am unable to get a reply. I also don't see the other box in places networking, though I don't know if I should.  When one is turned on, I get "network is disconnected" message from my linux box after it tries to connect.  My guess is that it's not a Samba problem but a inter-connect problem, though I've been wrong on guesses before ;) Would this have to do with ipv6?, Anyways, here's my ifconfig

eth0      Link encap:Ethernet  HWaddr 00:50:8d:b7:74:e6  
          inet6 addr: fe80::250:8dff:feb7:74e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17934 (17.9 KB)  TX bytes:2178 (2.1 KB)
          Interrupt:23 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:50:8d:b7:74:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:427 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:149511 (149.5 KB)  TX bytes:149511 (149.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:70.217.84.239  P-t-P:66.174.160.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:648925 (648.9 KB)  TX bytes:143276 (143.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.60.1  Bcast:172.16.60.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:116 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.136.1  Bcast:172.16.136.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I can ping 127.0.0.1 from my windows box but not connect to my share, though that seems like a strange ip address.  If I try to connect to my share with that ip address, it's like it doesn't accept the password.  My samba config file didn't change in the upgrade.  The subnet mask on my win xp box is 255.255.0.0.  Any suggestions?

---

### Post by dreaminhere on 2009-03-18
How do I get my two computers to see eachother?  There's no ip address to connect to except 127.0.0.1 and that is always the local address.

---

### Post by dreaminhere on 2009-03-18
Ok, I'm starting to get somewhere.  I added 

auto eth1
iface eth1 inet dhcp

to my /etc/network/interfaces file and now I get an entry 

eth1:avahi Link encap:Ethernet  HWaddr 00:50:8d:b7:74:e7  
          inet addr:169.254.9.227  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:22 Base address:0x8000 

that I can ping from my windows box.  However, there is a pause of 75 seconds on boot up now.  I assume that it is trying to do something with network since that is the only thing that was changed.  How do I get rid of that?

On a network restart, I get 

Listening on LPF/eth1/00:50:8d:b7:74:e7
Sending on   LPF/eth1/00:50:8d:b7:74:e7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

I think that is what is taking so long, but i don't know how to fix it.

---

### Post by grungedoobie on 2009-03-18
Hello Dreaminhere,

I've posted problems with the new Samba as well.

It seems there's still a lot that the writers havn't hashed out yet.

The following is a link to a post that has yet to be answered.

[http://ubuntuforums.org/showthread.php?t=863405]("http://ubuntuforums.org/showthread.php?t=863405")

The setup I'm using works with Linux boxes, but I havn't found a way to get it to work with Windows boxes.

At first, I was only able to get "SMB4K" to connect to the shares, and later on, I found that changing the address script on Dolphin and Konqueror allows me to use the shares with them.

Here's the script that Dolphin and Konqueror use automatically:

smb://<server name>/

Here's what I have to use to connect to the shares:

smb://<server address>/<shared folder>/

All of the computers can ping the server without a problem.  All of the computers can see the server name.  Upon connect, they all say "Timeout On Server" after about 2 seconds delay.  Only "SMB4K" can connect without help.  The other programs need the auto-address changed.  Only Windows is left to figure out how to connect.

Hope this gives some insight, as I'm quite bewildered myself.
Most things on Linux just plain work, but the new Samba doesn't seem to fit the profile.

I'm hoping sometime soon a guru will post an orderly breakdown of the entire command list for the "smb.conf" in a way that my noobish brain can fathom rather than throwing incomplete tidbits here and there that don't seem to work properly.  (my apologies for the run-on)


Best of luck to you and your quest.


The Grunge

---

### Post by dreaminhere on 2009-03-18
Thanks for the info, but this now seems to be not a samba problem, but a networking problem that occurred on upgrade from 8.04 to 8.10.  I've managed to connect by modifying the /etc/network/interfaces file, but that has added at least 75 seconds to bootup.  I've tried to set up a static ip address, but then I can't ping my computer.  Maybe I'm setting it up wrong?  Any ideas?

---

