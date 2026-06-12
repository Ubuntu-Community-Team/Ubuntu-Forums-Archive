---
title: "Direct Internet Connection Problems"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by a_swan89 on 2006-01-04
HI everyone, I am completely new to linux so please bear with me. If possible I would prefer help using GNOME for now as I am an utter linux noob. That said, I am having difficulties conecting to the internet. I am using a direct internet connection into my modem and have dynamic IP SBC DSL. Ubuntu recognizes my ethernet card but when I try to access the internet with firefox it tells me that the site could not be found. THank you in advance for any help provided.

---

### Post by darth_vector on 2006-01-04
hi :)

can you please open up a terminal and post the output of the following three commands:
```
ifconfig
route -n
cat /etc/network/interfaces
```

---

### Post by a_swan89 on 2006-01-04
Here goes:
ifconfig
eth0    link encap: Ethernet hwaddr 00:13:8F:49:9D:ED
inetaddr: 64.217.18.55  Bcast: 64.217.18.255
mask: 255.255.255.0  inet6 addr: fe80::213:8fff:fe49:9ded/164  Scope:Link
UP BROADCAST MULTICAST MTU: 1500    Metric:1
RX Packets: 13 errors: 0  dropped: 0  overruns:0  frame: 0
TX Packets: 0 erros: 8 dropped: 0  overruns: 0  carrier: 8  collisions: 0  txqueuelen: 1000
RX Bytes: 3254 (3.1 KiB)  TX Bytes:0 (0.0 b)
Interrupt: 17  Base Address: 0xe400

lo      link encap: local loopback
inet addr: 127.0.0.1  Mask: 255.0.0.0
inet6addr: ::1/128  Scope:Host
UP LOOPBACK Running MTU: 16436 Metric:1
RX Packets: 422 errors:0  dropped:0 overruns:0  frame:0
TX Packets:422  errors:0  dropped:0 overruns:0 carrier: 0 Collisions:0 txqueuelen:0 
RX Bytes: 36816 (35.9 Kib)  TX Bytes: 36816 (35.9 KiB)


Route -n  kernal 
Destination  Gateway  Genmask  Flags  Metric  Ref  UseIface


cat /etc/network/interfaces
#The Loopback Network Interface
auto lo
iface lo inet loopback

#Hot pluggable network interfaces
mapping hotplug
script grep
map eth0

#Primary Network device
iface eth0 inet DHCP
network 192.1687.0.0
broadcast 192.168.0.255

auto eth0

sorry if there are some typos, I'm pretty sure I got all the important stuff correct

---

### Post by darth_vector on 2006-01-04
thats ok :)

the problem (or a problem) is that you dont have a default route. we can see this because the "route -n" command doesnt return anything. you will have to find out the IP address of your modem and type
```
sudo route add default gw <modem_IP> dev eth0
```
see if that does it.

---

### Post by a_swan89 on 2006-01-04
I tried that and it didn't work. I know my modem's IP is 192.168.0.1 because it says so right on the modem. I even accessed it with firefox in windows. THe terminal responded with no such file or directory exists. Whats wrong?

---

### Post by mips on 2006-01-05
```
#Primary Network device
iface eth0 inet DHCP
[COLOR="Red"]network 192.1687.0.0[/COLOR]
broadcast 192.168.0.255
```
I assume the part in red is a typo ?

Also double check your router config as you are getting a 64.xxx.xxx.xxx address allocated ?

Try to first configure with a static IP address:

**sudo gedit /etc/network/interfaces**
```
iface eth0 inet static
address 192.168.0.10
netmask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.0.255
```

Also follow this guide [http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

You can always switch back to DHCP later once you know what the problem is.

---

### Post by darth_vector on 2006-01-05
[QUOTE=a_swan89]I tried that and it didn't work. I know my modem's IP is 192.168.0.1 because it says so right on the modem. I even accessed it with firefox in windows. THe terminal responded with no such file or directory exists. Whats wrong?[/QUOTE]

well a router ip of 192.168.0.1 wont work with a computer ip of 64.217.18.55 since they are on a different subnet.

---

### Post by a_swan89 on 2006-01-05
Let me give you my connection stats from my working windows connenction. Also, I don't have a router, just a direct line from my computer to the modem. 
Physical Address: 00-13-8F-49-9D-ED
IP Address: 70.252.181.177
Subnet Mask: 255.255.255.0
Default Gateway: 70.252.181.176
DHCP Server: 192.168.0.1
Lease Obtained: 1/5/2006 4:22:49 PM
Lease Expires: 1/5/2006 4:32:49 PM
DNS Servers: 192.168.0.1, 192.168.0.1
WINS Server:

---

### Post by mips on 2006-01-06
**sudo gedit /etc/resolv.conf**
```
nameserver 192.168.0.1
```

If there are any other entries put a # infront of the entry to disable it.

Ignore the sudo gedit /etc/network/interfaces changes I adviced and revert back to your original config using DHCP.

I this still does not work then post the following here:
1. Modem Make & model plus a weblink to it.
2. Full link to your SBC ISP service, the website is indexed by state so I would not know where to look.
3. An **exact** copy of your **ipconfig /all** output in Windows command prompt pasted here.

---

### Post by a_swan89 on 2006-01-10
Here's the link to my modem (its the 4100): [http://subscriber.communications.siemens.com/subscriber_networks/4100.shtml](http://subscriber.communications.siemens.com/subscriber_networks/4100.shtml)
Here's to my ISP support : [http://support.sbcglobal.net/index.php](http://support.sbcglobal.net/index.php)
Here's my ipconfig/all copy: 
Windows IP COnfiguration
Host Name......................:andrew-computer
Primary DNS suffix............:
Node Type......................: Hybrid
IP Routing.......................: No
WINS Proxy Enabled..........: No
DNS Suffix Search List.......: domain_not_set.invalid

Ethernet adaptor Local Area Connection:
Connection-specific DNS suffix......: domain_not_set.invalid
Description................................: ULi PCI Fast Ethernet Controller
Physical Address.........................: 00-13-8F-49-9D-ED
DHCP Enabled.............................: Yes
Autoconfiguration Enabled.............: Yes
IP Address.................................:68.90.159.249
Subnet Mask..............................:255.255.255.0
Default Gateway.........................: 68.90.159.248
DHCP Server..............................: 192.168.0.1
DNS Servers...............................: 192.168.0.1
                                                  192.168.0.1
Lease Obtained...........................: (Not Important)
Lease Expires..............................: (Not Important)

---

### Post by mips on 2006-01-10
Will look at this in the morning when I'm not half asleep...

---

### Post by mips on 2006-01-12
It looks like your speedstream is configured in **bridged** mode seeing it is assigning a public IP address to your computer.

Could I ask you to verify the above and change it to **routed** mode. 

You can check the manual for more details on the above, got a link to an online manual ?

Do you run any special software on your windows PC for the speadstream ?

Unfortunaly I did not have much time today to look at the links but I did notice the sbc link has many sub sections that requires you to know the domain on the drop down menu, what is your email domain, just the part after the @ sign ?

When I have time I will look into this further.

---

