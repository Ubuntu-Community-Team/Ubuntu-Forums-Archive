---
title: "Ethernet port issues (Only yellow light blinks) with 12.10 (and 12.04)"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by foobantu on 2012-11-11
Hi,
 
I was using ubuntu 12.04. Overall it was a very enjoyable experience untill I installed some updates. Rebooted the system as prompted and noticed that only yellow light was blinking in the ethernet port. I connected the cable to my work laptop and both yellow and green lights started blinking. So that means no issues with the ISP. I re installed the OS, and the connectivity comes back.
 
Same thing happens with 12.10. When I install the OS, everything works fine. But the moment I installed some updates and boot it up, only yellow light blinks.
 
I am really keen on using Ubuntu as my only dekstop system. But these issues keep hampering the experience. Can anyone suggest a work around?
 
RIght now I am typing this from my office laptop as I am at work and dont have access to the personal laptop.
 
My Personal Laptop is a Lenovo Z570. 
Given below are the specs:
 
IdeaPad Z570 59-069595
Intel® Core i5-2410M
3G DDR3 1333 MHz
640G 9.5mm 5400rpm
Nvidia GeForce GT 520M DDR 3 1GB Graphics
Bluetooth 2.1 /Camera 2.0M /HDMI/
Numpad/Card Reader/Rambo Tray in 12.7mm 
15.6 HD LED Glare 
Black 6Cell 2.2A
 
All other flavours of linux work fine from it. CentOS, OpenSUSE, Fedora, all of these work fine. I really want to use Ubuntu because it gives me the best battery time, a good mix of recent yet stable software and its absolutely great looking distro.
 
Any help will be appreciated.
 
Regards,
 
Foobantu

---

### Post by foobantu on 2012-12-01
Hi,

The issue is resolved.

Here's what I did:

1) Did a clean install of Ubuntu 12.04 (Need LTS for certain requirements). 


2) Ran the pppoeconf tool and downloaded the latest updates.


3) As given in one of the threads, removed the last few lines in /etc/network/interface file so that it now only has the following two lines.:
[B]auto lo
iface lo inet loopback[/B]

4) Disabled the network by right clicking on the Network icon and unchecked "Enable Networking". Rebooted the laptop 2/3 times.

5) Both the green and yellow lights started blinking. So using another thread configured the DSL Network tab to use the pppoe connectivity. Rebooted once again and clicked on it.  Working fine as of now.  :)

---

