---
title: "&quot;ifconfig eth0 up&quot; on unresponsive router"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by Beeblebrx on 2011-09-27
I am trying to wok on an unresponsive AP and I need to set a static IP for eth0 on my PC.  I have tried to do this through ifconfig and also from /etc/network/interfaces. When I try to bring up networking (/etc/init.d), system hangs for some time. After the cli prompt becomes available again and I try to ping, I get a "Network Unreachable" error.

When I run tcpdump on a second console while bringing up eth0, I see that it keeps looking for 192.168.1.1 to register on the master bowser and the DHCP server of my normal network.  So it seems, somehow I am not able to flush all of the info for eth0 when I change to static.

What I would like to get (what should happen) is a nice, regular "Request timed out" message for ping from a direct cable connection between the PC and the unresponsive AP.  I would like to figure out the command to bring up eth0 with such setup (is this under promiscous mode?).

I sort of know that "Network Unreachable" error is usually a DNS error; I am also unable to flush the DNS when I bring up interfaces after the boot and get "Network Unreachable" error for pings based on DNS (in lieu of IP pings).

Thanks for reading.

---

### Post by jonobr on 2011-09-27
Hi 

Could you share your /etc/network/interfaces contents?

also ifconfig to see what your eth0 shows?

---

### Post by Beeblebrx on 2011-09-27
Thanks for your answer. Network is functional with DHCP, but not with static...
/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp  #static
#address 192.168.1.9
#netmask 255.255.255.128
#broadcast 255.255.255.127
#gateway 192.168.1.1

auto wlan0
iface wlan0 inet dhcp

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:39:32:ac:37  
          inet addr:192.168.1.11  Bcast:192.168.1.127  Mask:255.255.255.128
          inet6 addr: fe80::200:39ff:fe32:ac37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1522 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1638415 (1.6 MB)  TX bytes:250735 (250.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:79 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5725 (5.7 KB)  TX bytes:5725 (5.7 KB)

---

### Post by jonobr on 2011-09-27
Hello


I notce for your static config, I think your broadcast is wrong

Your netmask is 255.255.255.128
which means your boradcast should be 192.168.1.127
Im not sure it will fix your problem but I think its wrong.

Im also surprised to see you subnetting your 192 address space.
Nothing wrong with it, but I want to check that you know you cant have anything greater then 192.168.1.126 on that segment

cheers

---

### Post by Beeblebrx on 2011-09-28
Re Broadcast Address: Silly me I knew that; but as Tolstoy once said:
"When you bang your head against a problem long enough, all you will see is red"

I'm pretty good with setting up and fixing linux/bsd but I have a long way to go for networks/wifi/firewalls. So re my subnet settings: It's a small (home) network and I wanted to figure out how to run a second dhcp on the second sub-network for thinclient testing (but never got around to it).

Anywhoo, correcting the broadcast cures the problem intermittently - meaning that I still get "network unreachable" error every other or third attempt, then I stop and re-start networking to get pinging back.  For comparison I tried the same tasks on an win XP with static addr set, and everything worked without problems / as expected.

Thanks for your help, mate.

---

### Post by jonobr on 2011-09-28
Sounds like you know your stuff, so I dont mind suggesting wireshark/tcpdump,

have you tried that? has it shown you anything?

---

### Post by Beeblebrx on 2011-10-03
Sorry for the late reply but sometimes I get sidetracked with other stuff.

In my original problem I was trying to catch the tftp window (at boot time) of a semi-bricked Access Point. I found that it is unresponsive and needs for sure a com port connection to un-brick. Thanks for the help in any event.

---

