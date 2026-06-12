---
title: "Another Broadcom 43xx issue"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by DeanZF on 2009-07-12
[FONT=Times New Roman][SIZE=3][COLOR=Navy][COLOR=Navy]I've got a BCM4312 that says that it has a 4315 chipset (rev 1).

I'm using Jaunty on a Dell Inspiron 1545. I was on line and doing fine on Friday, and then Saturday came and I booted up to no wireless network. Talked to a guy who's a Linux/Fedora kinda guy and he poked around for a bit and declared that it was probably a driver issue.

I've searched some and read some. In microsoft terms, it feels like something is corrupted. I found a thread started by Crackmonkey91 who admits to being an Ubuntu noob. I can identify. I got no beans yet, and a wireless disconnect!

On that [Crackmonkey thread]("http://ubuntuforums.org/showthread.php?t=1202760"), there was a suggestion to "disable" the driver, power down, connect via wired connection, reboot, and enable the connection so that it could go find whatever packets it needed to correct itself. First, it was not activated, but other than not being active, is there a way to also disable it? Where would I find that? Did all that to no avail.

What's my next course of action? My Ubuntu-ese is still very shaky, so as much English as you can, please![/COLOR]     :lolflag:
--
DeanZF
KCMO

 [/COLOR][/SIZE][/FONT]

---

### Post by DeanZF on 2009-07-12
[FONT=Times New Roman][SIZE=3][COLOR=Navy][COLOR=Navy]Bumping this now that there seems to be activity on the board.

Broadcom 4312 card with 4315 chipset, Ubuntu 9.04 Jaunty. Thinking it's a corrupted STA driver, but don't know how to get rid of it and reinstall it.

Please help.
[/COLOR] --
DeanZF
KCMO[/COLOR][/SIZE][/FONT]

---

### Post by t0mppa on 2009-07-12
The thing referred by the other thread simply means going to System / Administration / Hardware Drivers and disabling the STA from there, then getting wired access and enabling it from the same place, so it can download the packets.

If you never activated it through there (or compiled the packages manually), it isn't even installed on your system and can't be giving any trouble as b43 is the default driver for Broadcom wireless cards, if I'm not mistaken.

To get some troubleshooting done, open up a terminal, run **lshw -C network** and post back with the output to see what's up with your interface and which driver is associated with it.

---

### Post by DeanZF on 2009-07-12
> **t0mppa said:**
> To get some troubleshooting done, open up a terminal, run **lshw -C network** and post back with the output to see what's up with your interface and which driver is associated with it.

I thought that it was activated, since I could use it for several weeks. Here is the data from the lshw.  THANKS SO MUCH for coming to my rescue.

  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:af:2a:0b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:3f:6e:c7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.101 latency=0 module=sky2 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 66:89:2f:ee:7b:72
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by superprash2003 on 2009-07-13
also post output of the following 2 commands
1)iwconfig
2)sudo iwlist scanning

---

### Post by DeanZF on 2009-07-13
Again, thank you for your time on this. I hope to become knowledgeable enough so that I can help, too.

[B] iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.
====================================
sudo iwlist scanning 
  
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

pan0      Interface doesn't support scanning.
[/B][FONT=Times New Roman][SIZE=3][COLOR=Navy]--
DeanZF
KCMO[/COLOR][/SIZE][/FONT]

---

### Post by superprash2003 on 2009-07-13
wifi cards come with a wirless switch which has an on/off button , make sure its ON..

for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by DeanZF on 2009-07-13
[FONT=Times New Roman][SIZE=3][COLOR=Navy]Arrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrgh!!


I need a Snoopy as my avatar. Or a pirate.

This new machine has only one idiot light and only one switch on it. On/off, power/no power.

Yes, it was an on/off situation for the wireless card. It's an electronic switch on this machine, not a manual, visible, well-labeled physical switch. Doggone Dell designertwits used the F2 key as the on/off switch for the wireless. Has to be held for more than what I don't know, but that was it. I'm BAAAAAAAAAACK!!

Thanks to all. Color this one SOLVED.
--
DeanZF
KCMO[/COLOR][/SIZE][/FONT]

---

