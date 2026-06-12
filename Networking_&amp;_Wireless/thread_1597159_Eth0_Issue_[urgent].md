---
title: "Eth0 Issue [urgent]"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by BaronAtLeast on 2010-10-15
Hello people...
Before anything, I would like to apologize for my grammar mistakes (since I'm from Brazil and english is my second language, there will be many)...
Anyway...
I'm kinda a noob, but a friend asked me to install Ubuntu for him...
Well, everything went fine...
Till the moment of setting the network ._.
He have a modem, a wired router, and like 3 other computers...
I've tryed to just connect to the internet, with no success...
Then I've edited the /etc/network/interfaces as it follows:
 
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static
address 192.168.0.153
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.1
 
Then I've edited the /etc/resolv.conf
 
nameserver 200.204.0.10
 
Saved everything...
sudo /etc/init.d/networking restart
 
And woa, a "icon" poped up saying I was connected...
But I just can't access any sites...
I think I'm connected to the router, but not to the modem...
 
What can I do to fix it? D:
Thanks
 
*btw, i already tryed to set it to dhcp, but not even the "connected icon" appears =/
**bbtw: it's like 02:09 a.m. here ._. i'm kinda tired, but must finish this before going to sleep ._.

---

### Post by endotherm on 2010-10-15
well, it sounds like a dns issue, but your resolv.conf looks fine, as long as that address is valid.
can you nslookup anything?
```
nslookup www.ubuntuforums.org
```?
if not, can you ping the dns server? if not, can you ping your gateway? if so, how about [URL="http://www.google.com?"]www.google.com? 
[/URL]

---

### Post by darab on 2010-10-15
Please copy/paste the outputs of the following commands:

ifconfig

route

---

### Post by BaronAtLeast on 2010-10-15
No, I can not lookup anything... And THANKS GOD you guys are that fast xD
 
btw, i'm copying the outputs now:
 
eth0      Link encap:Ethernet  HWaddr 00:21:97:70:0a:6f  
          inet addr:192.168.0.157  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:97ff:fe70:a6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xe400 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52973 (52.9 KB)  TX bytes:52973 (52.9 KB)
wlan0     Link encap:Ethernet  HWaddr 00:08:54:93:53:b8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by BaronAtLeast on 2010-10-15
route:
 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

---

### Post by BaronAtLeast on 2010-10-15
Need anything more guys?

---

### Post by endotherm on 2010-10-15
well, eth0 is not transmitting or receiving anything, despite having a valid address, so you are not actually online. 

do you have ethtool installed? I think it's part of the default install:
```

sudo ethtool eth0

```

are you certain your cabling is correct? are you connecting to a switch or router, or directly to another PC?

---

### Post by BaronAtLeast on 2010-10-15
I'm connected to a D-Link 524 Wireless Router...
Also, if it something is not installed, I can't install (i think... no net = no apt-get ._.)
Also... sudo ethtool eth0 >> command not found

---

### Post by endotherm on 2010-10-15
> **BaronAtLeast said:**
> I'm connected to a D-Link 524 Wireless Router...
Also, if it something is not installed, I can't install (i think... no net = no apt-get ._.)
Also... sudo ethtool eth0 >> command not found
I know what you mean. ethtool gives you some good info about the state of a network card, so it can show duplex mismatches, or cabling problems. 

I'm at a loss sir, I don't know where to go next.

do you get any errors from 
```
sudo ifdown eth0
sudo ifup eth0
```?
anything show up in the kernel or system logs (System -> Administration -> Log File Viewer)?

---

### Post by BaronAtLeast on 2010-10-15
Ohh damn ._.
I'll copy whatever I see in those logs... Hope you can help me ._. Otherwise I'll have to spend hours installing win xp, drivers, bla bla bla ._.
 
Nothing on "sudo ifdown eth0" or "sudo ifup eth0"...
Also, there's lots of things on "log file viewer" > kern...
But it appears to be just the commands i've typed...
 

Anything else I can try? D:

---

### Post by darab on 2010-10-15
Can you ping your default gateway?

---

### Post by BaronAtLeast on 2010-10-15
Nope... I can not ._. What does it mean?
 
btw, i just copied the gateway from a "ipconfig" of this computer that I'm using right now (it's running windows xp sp 2, and was configured a long time)

---

### Post by BaronAtLeast on 2010-10-15
*UP*
 
sorry for bumping a post that it's not even a day old, but i really need this ASAP D:

---

### Post by darab on 2010-10-15
Does the network uses DHCP, or fix IP addresses? If it uses DHCP, try the following commands:

sudo ifdown eth0
sudo dhclient eth0

---

### Post by BaronAtLeast on 2010-10-15
I'm not sure if it is a DHCP... But I'm almost sure it's...
I've sent those commands without changing the /etc/network/interfaces bla bla bla...
Hope it make no diffence...
Anyway...
There was some "DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval X"...
X was 3,8,10,13,8,12,7
 
Then: "No DHCPOFFERS received"
and "No working leases or persistent database - sleeping"
 
 
*btw, this computer that i'm using to send those msgs uses DHCP... So yea, it's a DHCP
 
Anyway, internet still not working D:

---

### Post by darab on 2010-10-15
Try to switch te cable, and the router interface between your working windows computer and the one with the ubuntu, just to be sure there is everything is ok in there.

---

### Post by BaronAtLeast on 2010-10-15
Darab... And the other dude which I forgot the nick...
Thanks very much for the help...
But I don't know how to change the interface in the windows-pc ._.
I'm going to change the cables... I'll be back soon...
 
*btw... the network icon just... disapeared from the "panel" ._. how can i put it back there XD

---

### Post by darab on 2010-10-15
dont change the interface on the pc, just plug in the router the computer with ubuntu where the windows pc was.

---

### Post by BaronAtLeast on 2010-10-15
Did it ._. The windows pc just lost the internet...
The other one had no change (even using the same ip/etc the windows one was using)...
Blargh, the world is going to end... This is the ugliest storm evahh ._. I'll shutdown the pcs and come back as soon as the storm ends... Thanks...

---

### Post by darab on 2010-10-15
So it seems there is no link between the pc and the router. If the cable and the router interface is ok, it must be the NIC (Network Interface Controller, network card). If they're not integrated try to switch them between the two PCs.

---

### Post by BaronAtLeast on 2010-10-15
Ok... I'm back... The storm is gone...
Sadly the NIC is integrated...
 
 
 
****EDIT****
OH MY ****ING GOD... IT'S WORKING ._. I DON'T  KNOW WHY BUT IT ISSSSSSSSSSSSSSSS
HALLELUJAH
 
Thanks you all people...
Thank you very much!

*btw, i think it's related to the sudo dhclient eth0 xD

---

### Post by chili555 on 2010-10-15
Your nameserver 200.204.0.10 was not pingable; I doubt it is a valid DNS nameserver. When you did 'dhclient,' the gateway wrote its own DNS nameserver into /etc/resolv.conf. I suspect it is working because you now have a valid DNS nameserver.

By the way, your interfaces file is a bit busy. All mine contains is like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.153
netmask 255.255.255.0
gateway 192.168.0.1
```I wonder what your /etc/resolv.conf looks like now.

---

