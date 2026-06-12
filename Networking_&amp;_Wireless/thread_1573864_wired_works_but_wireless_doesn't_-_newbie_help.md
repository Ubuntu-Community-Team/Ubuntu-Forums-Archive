---
title: "wired works but wireless doesn't - newbie help"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by guzinters on 2010-09-13
Dear helpful people
I am reasonably uneducated in the finer points of linux. Recently I have been trying and failing to establish a wireless internet connection using Network Manager on Ubuntu. With a wire connection to the modem I get through to the internet no problem. However, with the wireless I seem to connect only to the local network, and try as I might can't persuade it to connect any further.
 
I'm not quite sure where to look to get a better idea of how to fix the problem and am hoping someone can point me in the right direction.

Some things I have found: With the line in netstat -nr gives me


Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.42.43.0      0.0.0.0         255.255.255.0   U         0 0          0 eth0
10.42.43.0      0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         10.42.43.1      0.0.0.0         UG        0 0          0 eth0


with the line out and wireless apparently connected (Network Manager says so) I get


Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.42.43.0      0.0.0.0         255.255.255.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0


if I then try to add the gateway manually with 

sudo /sbin/route add -net 0.0.0.0 gw 10.42.43.1

I get no internet connection, and when I try to connect using Putty I get "no route to host"

The contents of my /etc/network/interfaces

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

auto wlan0
iface wlan0 inet manual



Not sure what it all means or what other info to provide. You're advice would be greatly appreciated.

Thanks

---

### Post by Iowan on 2010-09-13
What are results of **ifconfig -a**? It looks like eth0 and wlan0 both try to get an address in the 10.42.43.0 subnet. (That usually creates problems...)

---

### Post by utilitytrack on 2010-09-13
> **Iowan said:**
> What are results of **ifconfig -a**? It looks like eth0 and wlan0 both try to get an address in the 10.42.43.0 subnet. (That usually creates problems...)

Yes, and this problems often the result of work buggy NetworkManager. Sorry for flood...

---

### Post by guzinters on 2010-09-13
ifconfig -a returns

eth0      Link encap:Ethernet  HWaddr 00:21:85:4d:4e:27  
          inet6 addr: fe80::221:85ff:fe4d:4e27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23654609 (23.6 MB)  TX bytes:5663540 (5.6 MB)
          Interrupt:27 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60703 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25557956 (25.5 MB)  TX bytes:25557956 (25.5 MB)

ppp0      Link encap: Point-to-Point Protocol  
          inet addr:119.139.69.175  P-t-P:119.139.68.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:5152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:2977867 (2.9 MB)  TX bytes:1145341 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:d0:e6:0a  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fed0:e60a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80106 (80.1 KB)  TX bytes:77162 (77.1 KB)

if this sheds any light? By the way I am using 10.04.

---

### Post by Iowan on 2010-09-14
Hmmm... :-k Curious - since wlan0 (wireless?) seems to have an IP address where eth0 (wired?) doesn't... yet the wired is working?

---

### Post by guzinters on 2010-09-15
Hi Iowan

thanks for considering my problem

Yes the wired connection works. However, when I connect the wire I immediately receive the message "ifupdown (eth0) connection established". 
"DSL connection" then appears on the Network Manager list, I select that and successfully connect to the internet.

Alternatively if I remove the wire (or don't plug it in in the first place) I get "HomePlusPlus500-F0612504 connection established" (presumably on wlan0)
No new connections appear on the list and this is as far as I get

could it be one of the DSL settings?

---

### Post by guzinters on 2010-09-16
You have to help me! I'm about to give up and reinstall windows!! *sob*

---

### Post by dineshs on 2010-09-17
```
gksudo gedit /etc/network/interfaces
```
comment out all lines (put a # before each line)except
```
auto lo
iface lo inet loopback

```Restart
Now to connect wired,
plugin the cable rightclick NM click DSL connection
For wireless ,disconnect wired then
use the terminal command```
sudo pon dsl-provider
```
Any progress?

---

### Post by guzinters on 2010-09-17
Yes!! You are a god!! 

Seems so simple. Am I right in thinking by using pon dsl-provider we are not trusting the dsl connection to NM? Care to explain what's going on here?

Great though, excellent, really appreciate it!

---

### Post by dineshs on 2010-09-17
From my experience the DSL configuration in NM will not work for wireless
If what I remember is correct,you can try this.
1) Run ```
sudo pppoeconf wlan0
```to configure DSL via wifi .Follow instructions.This will create a file named [COLOR="Blue"]dsl-provider[/COLOR] in */etc/ppp/peers*.
2) Rename  [COLOR="Blue"]dsl-provider[/COLOR] to [COLOR="Blue"]wlan[/COLOR] using ```
sudo mv  /etc/ppp/peers/dsl-provider /etc/ppp/peers/wlan
```
3) Now run```
sudo pppoeconf eth0
```to configure DSL via wired and follow instructions to create dsl-provider in /etc/ppp/peers again 
4) Rename  [COLOR="Blue"]dsl-provider[/COLOR] to [COLOR="Blue"]eth[/COLOR] using  ```
sudo mv  /etc/ppp/peers/dsl-provider /etc/ppp/peers/eth
```
5)Now backup your /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
6) Edit the file */etc/network/interfaces*```
gksudo gedit /etc/network/interfaces
```
so that it contains only these two lines
```
auto lo
iface lo inet loopback

```
Restart PC.Now,
To connect wifi use```
sudo pon wlan
```
To disconnect wifi ```
sudo poff wlan
```
7)Similarly,
To connect wired use```
sudo pon eth
```
and to disconnect wired```
sudo poff eth
```

---

