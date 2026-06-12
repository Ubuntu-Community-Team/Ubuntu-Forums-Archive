---
title: "Ethernet Issue- Can't edit the static IP &amp; unable connect to network"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by nicholastee on 2012-08-16
Hi All,
 
My Ubuntun 10.04 LTS facing connection issue. I can't edit the static IP setting under Network Connections..Due to i can't find this in my ***Preferences –> Network Connections.***
And my Wired connection not connected. The error details as below :
 
[IMG]http://i48.tinypic.com/28in79u.png[/IMG]
 
Please advise how to solve this issue. Because i'm newbie in ubuntun.
 
Thanks in advanced.

---

### Post by chili555 on 2012-08-16
Can you find the Network Manager icon at the top panel? Click it and select Edit connections; select Wired and change the Automatic (DHCP) to Manual and fill in your details including DNS nameservers. Save, close and connect.

Please see attached. Post back if you need additional guidance.

---

### Post by nicholastee on 2012-08-16
I can't find the network Manager icon at on top the panel. Disappear at the panel.

---

### Post by chili555 on 2012-08-16
Please open a terminal and type:```
nm-applet &
```Does it appear? Any errors or warnings?

---

### Post by nicholastee on 2012-08-16
I get this error message.
 
THe Program "nm-applet" can be found in the follwing packages:
*network-manager-gnome
*mythbuntu-diskless-client
try: sudo apt-get install <selected package>

---

### Post by unevenflow on 2012-08-17
then type sudo apt-get install network-manager-gnome

---

### Post by chili555 on 2012-08-17
> **nicholastee said:**
> I get this error message.
 
THe Program "nm-applet" can be found in the follwing packages:
*network-manager-gnome
*mythbuntu-diskless-client
try: sudo apt-get install <selected package>I'd suggest you *NOT* type sudo apt-get install network-manager, since you don't have a network connection and can't get on line. I suggest you do:```
sudo gedit /etc/network/interfaces
```Add your details here:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 999.168.1.108
netmask 255.255.255.0
gateway 999.168.1.1

```Of course, substitute your details here. Proofread, save and close gedit. Then do:```
sudo gedit /etc/resolv.conf
```Add nameservers:```
nameserver 8.8.8.8
nameserver 999.168.1.1
```Again, substitute your details here. Proofread, save and close gedit.

Now restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
```Are you connected?```
ping -c3 www.google.com
```

---

### Post by nicholastee on 2012-08-17
i had try gedit the files. But i still unable to connect.
 
when i run this "sudo ifdown eth0 && sudo ifup eth0", i get this error message.
 
siocaddrt : file exists
Failed to bring up eth0.

---

### Post by chili555 on 2012-08-17
I wonder why eth0 isn't coming up. Please check the message files:```
dmesg | grep eth0
```

---

### Post by nicholastee on 2012-08-17
[    1.930881] eth0: Tigon3 [partno(BCM57780) rev 57780001] (PCI Express) MAC address 00:25:64:ba:46:b4
[    1.930884] eth0: attached PHY driver [Broadcom BCM57780] (mii_bus:phy_addr=200:01)
[    1.930886] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.930888] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   21.357938] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.954759] tg3: eth0: Link is down.
[   24.141222] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   24.141224] tg3: eth0: Flow control is on for TX and on for RX.
[   24.141350] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   34.192005] eth0: no IPv6 routers present

---

### Post by chili555 on 2012-08-18
> [ 24.141222] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 24.141224] tg3: eth0: Flow control is on for TX and on for RX.
[ 24.141350] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 34.192005] eth0: no IPv6 routers presentThis all looks pretty solid. Are you quite sure of your DNS nameservers, address, netmask and gateway? Were they provided by your internet service provider? University? Landlord? Or..??

---

### Post by nicholastee on 2012-08-20
I'm sure the dns server name & gateway is correct. 
Fyi, ubuntu server had been used few months ago. since last week. This server facing etherner issue.

---

### Post by chili555 on 2012-08-20
Maybe we can diagnose where it's failing. Please do:```
sudo ifdown eth0 && sudo ifup -vv eth0
ifconfig
sudo cat /var/log/syslog | grep eth0 | tail -n20
```Thanks.

---

