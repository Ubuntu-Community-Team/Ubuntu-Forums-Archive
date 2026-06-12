---
title: "wireless connection with ubuntu 9.10?"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by phawnex on 2010-01-01
i posted this in the apple section, but felt here would probably be a little more appropriate after browsing the forums much more indepth 

> i just successfully downloaded and installed ubuntu koala (9.10 i think...) and its a great interface. i am just having extreme difficulty trying to set up the wireless connection.

when i log back in osx, i am able to access the router and use the internet as i am doing now when i post in the forum. i am just trying to learn how to configure the wireless in ubuntu as well.

i posted in this forum instead of another one because maybe i can luck out and have someone who has successful been able to connect wirelessly on an imac, or apple laptop in ubuntu....

any help would be GREATLY appreciated. 

thanks for your time.

ps. i did some searching on the forums, how does one update or load drivers (if applicable for the built in airport wi-fi in the imac)


any extra advice would be greatly appreciated.

thanks you all

---

### Post by phawnex on 2010-01-01
no luck eh?

---

### Post by phawnex on 2010-01-01
was browsing through some old threads similar to mine and one person asked to put the command 'lspci'

and here are my results if they help

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M76XT [Mobility Radeon HD 2600 XT]
03:00.0 FireWire (IEEE 1394): Agere Systems FW643 PCI Express1394b Controller (PHY/Link) (rev 05)
04:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller (rev 13)

---

### Post by focwiz on 2010-01-01
> **phawnex said:**
> was browsing through some old threads similar to mine and one person asked to put the command 'lspci'

and here are my results if they help

Try this...?...The 4328 is actually a 4321 or 4322...

[http://ubuntuforums.org/showthread.php?t=1368699]("http://ubuntuforums.org/showthread.php?t=1368699")

---

### Post by phawnex on 2010-01-01
another command i was looking through when i went through the help program on ubuntu told me to enter this to troubleshoot the wireless network

command: sudo lshw -C network

> daniel@daniel-desktop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:50300000-50303fff memory:50000000-500fffff(prefetchable)
  *-network
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 13
       serial: 00:1b:63:99:48:3b
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:50200000-50203fff ioport:2000(size=256) memory:50800000-5081ffff(prefetchable)
daniel@daniel-desktop:~$ 

no words saying 'claimed, unclaimed, disabled, enabled'

after that command. it obviously shows to me that it reads my wireless builtin (its internal) but wont actually utilize it?

thanks focwiz, but its a wireless connection , not a wired connection. the router is a linksys, and i have build in airport in my mac.  it reads it but wont work it i think?

---

### Post by focwiz on 2010-01-01
> **phawnex said:**
> 

thanks focwiz, but its a wireless connection , not a wired connection. the router is a linksys, and i have build in airport in my mac.  it reads it but wont work it i think?

Yes, I know it is wireless...but READ the document...The WIRED connection it refers to will help you get the wireless working. There are instructions either way, but those are instructions to make the Broadcom WIRELESS chipset YOU HAVE work in Ubuntu.

And..I have a Linksys router...you need to configure the Airport (Broadcom chipset) in your Mac for Ubuntu as per the directions in the post I lead you to.  Then...it may work for you.

Good Luck

---

### Post by phawnex on 2010-01-02
thanks man will check it out and post results

---

### Post by phawnex on 2010-01-03
you guys are the greatest!... im typing on this forum wirelessly on ubuntu. i need to install adobe flash and reader. but other then that nice start!

thanks focwiz!

---

