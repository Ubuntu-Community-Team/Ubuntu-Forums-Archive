---
title: "Both Wired and Wireless network not working"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by venkatana on 2010-07-26
I recently switched over from Windows XP to Ubuntu 10.04. I am unable to connect to the network. Both wired and wireless are not working. I tried to connect by assigning the IP address manually and also by automatic DHCP assigning. It did not work. In the wired network when I access a site I get the message unable to connect to server. Pinging in wired network is 100% success. With my limited knowledge and with the help of Help menu I checked the current connections and also checked the device recognition for Wireless. The results are:
 
 
home@home-laptop:~$ sudo lshw -c network
*-network 
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:18 memory:99500000-99503fff
*-network
description: Ethernet interface
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:04:00.0
logical name: eth0
version: 02
serial: 00:23:5a:29:08:fc
size: 100MB/s
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
resources: irq:31 ioport:3000(size=256) memory:93410000-93410fff(prefetchable) memory:93400000-9340ffff(prefetchable) memory:93420000-9343ffff(prefetchable)
*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:21:00:ac:c6:04
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
home@home-laptop:~$ 
 
 
home@home-laptop:~$ ifconfig eth0
eth0 Link encap:Ethernet HWaddr 00:23:5a:29:08:fc 
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::223:5aff:fe29:8fc/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:171 errors:0 dropped:0 overruns:0 frame:0
TX packets:214 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:18674 (18.6 KB) TX bytes:21934 (21.9 KB)
Interrupt:31 Base address:0x6000 
 
 
home@home-laptop:~$ 
 
 
 
 
 
 
home@home-laptop:~$ ifconfig wlan0
wlan0 Link encap:Ethernet HWaddr 00:21:00:ac:c6:04 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
 
home@home-laptop:~$ 
 
Please help.

---

### Post by Iowan on 2010-07-26
> **venkatana said:**
> In the wired network when I access a site I get the message unable to connect to server. Pinging in wired network is 100% success. HAve you tried pinging internet site by IP address?  If it works, verify you have correct nameservers in */etc/resolv.conf*.

---

### Post by venkatana on 2010-07-26
Pinging is 100%successful. Name server is correct.  Used the sudo pppoecof command to configure the connection. Got the message Access Concentrator did not respond. Don't know how to proceed further.

---

### Post by venkatana on 2010-08-02
I am sad that I am not getting any help from this forum.  I am without internet connectivity for more than a week. Can anyone help me?  After going through postings in this forum I disabled the ipv6 and the result is pinging is not working. The programme is not responding and I had to force quit the programme.

---

### Post by arewethereyet on 2010-08-02
I would start by hard resetting your modem. there should be a tiny little button you can press with a small pointy object.

From there your Internet should automatically be available. If it is not then you will need to investigate what drivers you need to acquire, and if you need to modify them at all to make them work.

if you post you router brand/model, and your laptop brand/model I will research and see what i can find for you. If possible also post any relevant information you have on the network card/chipset you are using.

---

### Post by venkatana on 2010-08-03
After disabling ipv6 I tried the update center and the updates were downloaded.  It was not downloading before disabling ipv6.  Thereafter I downloaded from software center google chrome.  I am now able to connect to the internet.  However, Firefox is still not working and the time out message is still coming.  I have made goodle chrome my default browser.  The wireless problem still continues.  It is still shown as disconnected.  However I am able to ping ubuntu.com successfully with wireless device in network tools.  I am giving the information required
Router brand model: Huawei WA1003A
Laptop Compaq Presario CQ40
Network card: ethernet: Realtek RTL 8102E Family PCI-E fast Ethernet NIC
Wireless: Broadcom 802.11b/g WLAN
Looking forward to solving my wireless problem.

---

### Post by dineshs on 2010-08-03
I havent tried wireless.But can tell you how to make the wired part perfect.
_Method -1 Modem in bridge mode_
(If the modem is in bridge mode you need a PPPoE dialler in the Operating system to connect/disconnect)To do this in ubuntu,
step-1 First backup your /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now run
```
 gksudo gedit /etc/network/interfaces
```
Copy and paste the following into the file(The file should contain only this)
```
auto lo
iface lo inet loopback
```
[COLOR="Blue"]Restart your machine[/COLOR]
step-2 Now configure your connection as in this link
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

_Method-2 Modem in PPPoE mode_ 
(The connection will always be ON)follow step-1 above then configure the modem as explained here
[http://ernakulam.sancharnet.in/ernakulam/bbservice.html](http://ernakulam.sancharnet.in/ernakulam/bbservice.html)
 under modem/CPE config (select your modem type)
I suggest you use the second method so that configuring wireless will be more easy

---

### Post by venkatana on 2010-08-03
Thank you very much. I tried the first method and finally i got the contents of etc/network/interfaces like this 
auto lo
iface lo inet loopback

I am now able to internet immediately on starting the laptop.  However the issue regarding wireless still remains.  In the network manager under wireless it is shown as device not ready.

---

### Post by dineshs on 2010-08-03
The lshw  output says wireless disabled.Is it possible to enable it.(Regarding ethernet you can click NM icon and tick enable networking.I dont know about wireless)

---

### Post by venkatana on 2010-08-20
With help from answers.launchpad.net the problem is solved. 
The network driver is not activated. It was activated with the following procedure
In the Terminal enter <lspci-vvnn | grep 14e4>
you will get the location and details of the network card.  After identifying the card
enter<sudo aptitude install bcmwl-kernel-source>
Thereafter go to system>administion>hardware drivers, select the driver and activate it.  Restart the laptop and wireless network is on.

---

