---
title: "wireless not working"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by skashif3 on 2010-01-20
Hi,
   I am completely new to linux (like 2 days old :) I installed Ubuntu 9.10 on windows 7 through VMware. Everything is okay except that my laptop cant find any wireless network? In windows, it automatically detects number of wireless networks and then I connect to them. However this is not the case with Ubunutu. How can I check that my network card is working? by the way I am using 64 bit Ubuntu on 64 bit system.

---

### Post by drpjkurian on 2010-01-20
> **skashif3 said:**
> Hi,
   I am completely new to linux (like 2 days old :) I installed Ubuntu 9.10 on windows 7 through VMware. Everything is okay except that my laptop cant find any wireless network? In windows, it automatically detects number of wireless networks and then I connect to them. However this is not the case with Ubunutu. How can I check that my network card is working? by the way I am using 64 bit Ubuntu on 64 bit system.

Hi
I presume that your desktop is default Gnome. You can right click the icon network connection which launches the network manager. Select wireless and scan for signals. 
You can also try by navigating to Applications--> Administration--> Network

---

### Post by skashif3 on 2010-01-20
What do you mean by "scan for signals". In Network Manager, when I click the wireless, it only gives me Add, Delete or Edit options.

---

### Post by bkratz on 2010-01-20
I think he meant to say left click. When you right click it is the setup mode for selecting the name of the network the ESSID and the security modes available. Left clicking generally shows the available networks for selection.

If you don't see any networks either there are none around or the wireless card is not setup.

At that point you should drop to the terminal
Applications>>Accessories>>Terminal and type in
sudo lshw -C network
(that is LSHW in lowercase and C in uppercase) and copy/paste the outputs back here for decoding. This will require you to input your password with nothing echoed to the screen--not even ***. After you type this in just hit return.

You can also see all the networks available with the terminal with
sudo iwlist scan
if you want to.

---

### Post by skashif3 on 2010-01-20
Here is the output of "sudo lshw -C network"

description: Ethernet Interface
product: 82545EM Gigabit Ethernet Controller (Copper)
physical id: 1
bus info: pci@0000:02:01.0
logical name: eth0
version: 01
serial: 00:0c:29:96:7f:ff
size: 1GB/s
width: 64 bits
clock: 66Mhz
capabilites: pm pcix bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full fireware=N/A latency=0
               link=yes mingnt=255 multicast=yes port=twisted pair speed =1GB/s
resources: irq:19 memory:d8920000-d893ffff memory:d8900000-d890ffff ioport:2000(size=64) memory:db600000-db60ffff (prefetchable)

I have typed it by my hand, so it may have some typos

---

### Post by skashif3 on 2010-01-20
capacity: 1Gb/s

missed that :)

---

### Post by skashif3 on 2010-01-20
Output of "sudo iwlist scan"

lo	Interface doesn't support scanning

eth0    Interface doesn't support scanning

---

### Post by bkratz on 2010-01-21
OK we are not seeing the wireless card yet. So now to find out which one go back to the terminal and copy/paste the following:

lspci | grep Wireless

If you don't see anything here, then try

lspci

(those are both LSPCI in lowercase)

One of them will tell us what the card is, unless it is a usb card, which would be 

lsusb
(just to cover all bases!)

---

