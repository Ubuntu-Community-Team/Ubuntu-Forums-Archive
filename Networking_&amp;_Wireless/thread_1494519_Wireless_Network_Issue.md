---
title: "Wireless Network Issue"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by TheWeakSleep on 2010-05-27
Hi there, I just installed Ubuntu 10.04 on my netbook (not the netbook remix) which is an lg x120-N CSLAA9, if that will help.

So, this is the first linux distribution that I've used, so I'm a complete beginner. I tried searching the forum for any answers to this, but I either can't figure it out, or just didn't see it :)

So anyway! here's my issue. My wireless networks aren't being picked up! if I right-click the icon, it has a little check-mark beside enable wireless, but still nothing. I tried troubleshooting at help.ubuntu.com, and i put in the sudo lshw etc. command it told me to see about the network card, and this is what i got

PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:e0:91:3d:5e:e3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:2000(size=256) memory:f8000000-f8000fff(prefetchable) memory:f6000000-f600ffff(prefetchable) memory:f6020000-f603ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:f2000000-f200ffff

Anyways, I'm sorry if the answer was already somewhere else (I'm sure it was, but i couldn't find it! ) and i updated after I installed it. thanks in advance for any help you can give me!

---

### Post by v1ad on 2010-05-27
basic steps.
1. make sure wireless button is on.
2. ifconfig (check for wlan0)
3. if wlan0 exists then (ifconfig wlan0 up)
4. once on my laptop i had to click on the networking tab and select enable networking.

if no wlan0 in ifconfig post that here please.

---

### Post by Kirkland14 on 2010-05-27
on my dell 1545 i had to hardwire into the router and then went to accessories>system>hardware drivers and then click on whatever driver is there.  Don't know if it will work with what you have but maybe.

---

### Post by TheWeakSleep on 2010-05-27
Thanks for the quick reply :)
1. There isn't a physical wireless button :(
2. I didn't see anything to do with Wlan0, I'm pretty new at this though, so I'll post what came up :)


eth0      Link encap:Ethernet  HWaddr 00:e0:91:3d:5e:e3  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:91ff:fe3d:5ee3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14573483 (14.5 MB)  TX bytes:1543479 (1.5 MB)
          Interrupt:26 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:132 errors:0 dropped:0 overruns:0 frame:0
          TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11180 (11.1 KB)  TX bytes:11180 (11.1 KB)

---

### Post by v1ad on 2010-05-27
yea the wireless is not detected.

do 
sudo apt-get install ndiswrapper

then download the windows driver from the manufacturers website for your computer. 

if it is an .exe file, extract it and find the .inf file.

go to System > Administration > Ndiswrapper
 
select add a driver or something like that. find the .inf file select it and apply it.

then try this command again

ifconfig wlan0 up.

if you can't find the wireless driver for your computer ill come back after work and post the .inf file here through a download link.

---

### Post by TheWeakSleep on 2010-05-27
Hi thanks for the help! I'm just not quite sure how to extract the .inf file from a .exe file! It just keeps giving me an error

---

### Post by TheWeakSleep on 2010-05-27
if you could post the .inf file it would be a lifesaver :)

---

### Post by v1ad on 2010-05-27
k i sec.

---

### Post by v1ad on 2010-05-27
[http://www.2shared.com/fadmin/13720595/a84ddbc2/WINXP2K.zip.html](http://www.2shared.com/fadmin/13720595/a84ddbc2/WINXP2K.zip.html)

here you go, unzip it and make sure u select the .inf file in there.

---

### Post by TheWeakSleep on 2010-05-27
Thanks, but I'm not sure if that's the right one? i installed it from ndiswrapper, but it says hardware present: no
i tried what you said before with the ifconfig, but still no wlan0
its a raLink rt3090 Wireless 802.11n 1T/1R PCIe
Any ideas?

I can get the software from ralinktech.com, but i have no idea what to do with it! 

Thanks for your help :)

---

### Post by v1ad on 2010-05-27
k the specs i found online where different ill post the new 1 soon.

---

### Post by v1ad on 2010-05-27
I found this seems there is an open source alternative.
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages](https://launchpad.net/~markus-tisoft/+archive/rt3090/+packages)

download link below
[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

try this. inf file coming soon. but in my opinion this will should work the best.

---

### Post by v1ad on 2010-05-27
if the above does not work let me know. i couldn't get the .inf file out of the download so i will try something else if that does not work.

---

### Post by TheWeakSleep on 2010-05-27
No worries it worked perfectly!! Thanks so much for your help, you're a lifesaver :)
Ubuntu definitely has the best community :)

---

### Post by v1ad on 2010-05-27
:] great glad i could help.

once your issue is solved if you can please select thread tools on top and mark it as solved. so others won't get confused.

---

