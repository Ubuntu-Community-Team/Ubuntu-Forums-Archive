---
title: "Beginner. Can someone point me in the right direction to install wireless drivers?"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by shawndh on 2009-03-15
I have two wireless cards and I can't get either of them to work. One is a AirLink+ card with a TI chipset and the other (I just bought) is a Hercules card with a RALINK chipset. I've downloaded the drivers for the RALINK chipset but I can't figure out this installing packags thing. I've been at this for 3 days and I've been reluctant to post for fear of sounding like I hadn't done any research. I give. I just can't figure this out. Someone help, please. 

I'm using Ubuntu 8.10 on an old Compaq machine. 
The comand: lspci procuces: RaLink Rt2561/RT61 rev B 882.11G
uname -mr produces: generic 2.6.27.7 i686

That was as much info I could get at the time.

---

### Post by chili555 on 2009-03-16
I suggest, from a terminal:```
sudo modprobe rt61pci
iwconfig
```Do you now see a wireless interface? *ra0*, perhaps? If so, you should be able to click the Network Manager icon, select a network and connect.

---

### Post by shawndh on 2009-03-17
> **chili555 said:**
> I suggest, from a terminal:```
sudo modprobe rt61pci
iwconfig
```Do you now see a wireless interface? *ra0*, perhaps? If so, you should be able to click the Network Manager icon, select a network and connect.

When I type the first command, nothing happens. When I type the second command, I see info For wlan1 and my network name. When I click ton the network icon, it sees the network and tres to connect, but after a few seconds I get a yellow notification box that says "the network connection has been disconnected". I can still see my networks Signal stregnth but- I cant connect to it. Is it the driver or other issue?

---

### Post by chili555 on 2009-03-17
I think it's a Network Manager issue, based on searches of this forum. If your computer is stationary, that is, doesn't roam down to the university, coffee shop or similar, you might just remove Network Manager and configure things by hand. If you do need to roam, check here: [http://ubuntuforums.org/showthread.php?t=1082146&highlight=rt61pci](http://ubuntuforums.org/showthread.php?t=1082146&highlight=rt61pci)

Post back if you get stuck.

---

### Post by shawndh on 2009-03-17
> **chili555 said:**
> I think it's a Network Manager issue, based on searches of this forum. If your computer is stationary, that is, doesn't roam down to the university, coffee shop or similar, you might just remove Network Manager and configure things by hand. If you do need to roam, check here: [http://ubuntuforums.org/showthread.php?t=1082146&highlight=rt61pci](http://ubuntuforums.org/showthread.php?t=1082146&highlight=rt61pci)

Post back if you get stuck.

How do I configure without Network Manager? I've already removed it and tried to enable some other network programs but I need an internet connection to do it. :(

---

### Post by chili555 on 2009-03-18
Here is what I suggest:```
sudo iwlist wlan1 scan
```Verify the exact name of your network, Linksys is not the same as linksys is not the same as linksys5.

Next edit your */etc/network/interfaces* file to make it look like this:```
# The loopback network interface
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan1
iface wlan1 inet dhcp
wireless-essid <your_network_name>
```

Then do:```
sudo /etc/init.d/networking restart
```Did you connect? It should connect on boot from now on.

All this assumes you have no encryption; WEP, WPA, etc. If you do, post back and we'll set it up.

---

### Post by shawndh on 2009-03-19
I reinstalled Ubuntu and all of a sudden, it connected to my network without installing any drivers or anything. Woo Hoo! I don't know what it was but this is my third time reinstalling it. But maybe the 2nd time with this new wireless card. Thanx for the replies; I'm sure I need some more help though. This time I can post from my Linux computer. :D

---

