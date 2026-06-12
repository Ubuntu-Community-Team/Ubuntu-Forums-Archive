---
title: "lenovo s10-2 no wireless, no light, Broadcom BCM4312 rev 01"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by mngbng on 2010-08-02
Hi, I have a lenovo s10-2 running a fresh installation of ubuntu 10.04. I  have installed the Broadcom STA wireless driver, a proprietary driver  as recommended by ubuntu after first startup and as reported by numerous  posts. However, I am not able to get in contact with my wireless  network, but I am afraid that I am not in contact with the wireless card  at all since the LED light beside the wireless symbol is not on. I am  aware of the on/off switch for the wireless, but enabling/disabling  using this switch has no effect. When I click the network manager icon  it says "disconnected" under Wireless networks.

Is the wireless card dead? How can I test it? 

I am grateful for any good tips! Thanks! 

Here is some output, hopefully helpful:

```
$ sudo dmesg | grep Broadcom
[   12.375450] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.60.48.36 

``````
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:b8:15:27
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:56100000-56103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:d0:eb:5a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.0.196 latency=0 link=yes  multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:2000(size=256)  memory:52010000-52010fff(prefetchable)  memory:52000000-5200ffff(prefetchable)  memory:52020000-5203ffff(prefetchable)
``````
$ lspci -vnn | grep  14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:04b5]

```

---

### Post by Joe of loath on 2010-08-02
Have you tried turning the switch on and leaving it 30 seconds? Mine takes that long to actually turn on and start doing stuff.

---

### Post by mngbng on 2010-08-02
> **Joe of loath said:**
> Have you tried turning the switch on and leaving it 30 seconds?

Yes, I have tried that, but with no success.

BTW, all the three lights light when the computer is turned on, but the wireless light goes off after approx. 2 seconds.

---

### Post by sfife on 2010-08-03
> **mngbng said:**
> Hi, I have a lenovo s10-2 running a fresh installation of ubuntu 10.04. I  have installed the Broadcom STA wireless driver, a proprietary driver  as recommended by ubuntu after first startup and as reported by numerous  posts.

I am having the same problem after updating just recently. No wifi extension.

---

### Post by Dmytr on 2010-08-03
I'm having the same problem on Ubuntu 10.04 Netbook edition. No light and no wireless.:(

---

### Post by marshal19 on 2010-09-17
Yes, i have the same problem as well. is there anyone can help ? cuz i'm a beginner on Ubuntu. plzzz~~i just wanna connect to internet, in UBUNTU nothing can be done without internet ..

---

### Post by Dmytr on 2010-09-17
Looks like I have resolved my problem. Steps:
1. Installed Windows XP.
2. Flashed BIOS with latest firmware from the IBM's site (it was not up to date).
3. Installed wifi drivers. Verified that wifi works.
4. Verified wifi works using ubuntu 10.04 live usb.
5. Installed ubuntu 10.04 to the hdd. Wireless switch, light and wifi works.

---

### Post by sfife on 2010-09-18
> **Dmytr said:**
> Looks like I have resolved my problem. Steps:
1. Installed Windows XP.
2. Flashed BIOS with latest firmware from the IBM's site (it was not up to date).
3. Installed wifi drivers. Verified that wifi works.
4. Verified wifi works using ubuntu 10.04 live usb.
5. Installed ubuntu 10.04 to the hdd. Wireless switch, light and wifi works.

I went through with the Bios update and have wifi working :) but what I noticed was that wireless was disabled in the bios before I did any Bios changes. I went from 14cn58ww to 14CN94WW so.. if someone finds enabling this before making changes and rebooting into 10.4 then please give some feedback. Also the 14CN94WW Bios broke my ability to boot from USB cdrom :(

Download source
[http://consumersupport.lenovo.com/ot/en/driversdownloads/drivers_list.aspx?categoryid=43]("http://consumersupport.lenovo.com/ot/en/driversdownloads/drivers_list.aspx?categoryid=43")

---

### Post by mngbng on 2010-09-21
Two questions:

[LIST=1]
[*] Is it possible to upgrade bios without installing Windows? I have only found bios updates for windows on lenovo's site.
[*] How did you install windows on the lenovo? Using a USB-DVD drive?
[/LIST]
  
Thanks!

---

### Post by sfife on 2010-09-23
> **mngbng said:**
> Two questions:

[LIST=1]
[*] Is it possible to upgrade bios without installing Windows? I have only found bios updates for windows on lenovo's site.
[*] How did you install windows on the lenovo? Using a USB-DVD drive?
[/LIST]
  
Thanks!

[FONT="Georgia"][SIZE="2"][LIST=1]
[*]It may be possible but I decided to just install windows via CDRom usb rather than sift through mountains of forums to find the method that worked mind you I did look but couldn't find what I thought was the right info.



[*]I have installed Win 7 on usb using this guide before and it worked great. [[COLOR="Blue"]http://www.maximumpc.com/article/howtos/how_to_install_windows_7_beta_a_usb_key[/COLOR]]("http://www.maximumpc.com/article/howtos/how_to_install_windows_7_beta_a_usb_key")
[/LIST][/SIZE][/FONT]

---

