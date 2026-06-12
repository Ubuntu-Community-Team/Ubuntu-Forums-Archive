---
title: "Wireless Disabled Broadcom BCM 4312, Dell Vostro 1700"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by CHUMitu on 2010-08-22
I have a Dell Vostro 1700 with the Broadcom BCM4312 card (obviously). Running 10.04.

Earlier today the wireless was working fine, then after a reboot, it stopped. I have the Broadcom STA wireless driver installed already, and have read all the other applicable threads on the forums pertaining to my situation and tried various fixes posted, all to no avail.

I can access the internet via wired tethered connection through my Droid, and it doesn't detect the wireless tether, again, obviously. I have my wireless switch on, and 'rfkill list' returns:

matt@ubuntu:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

When its switched off, it returns:

matt@ubuntu:~$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Oddly it appears to be open when it's off and blocked when it's on. When the wireless switch is set to off I can search for hidden networks, and it finds my network when I type it in or use the one I've set in already, but it just sits at connecting and repeatedly asks for my passkey (which is inputted correctly). After three tries it says 'wireless disconnected'. When the wireless switch is set to on, it says my wireless is disabled.

Here's the iwconfig: (tethered to my phone)

matt@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

usb0      no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

Output for sudo lshw -C network: (again, tethered to my phone)

matt@ubuntu:~$ sudo lshw -C network
[sudo] password for matt: 
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:6d:f3:2d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f9ffc000-f9ffffff

lshw -C network with my wireless set to 'off':

matt@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:6d:f3:2d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:82:02:1c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 96:dc:f8:45:4d:33
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.224 link=yes multicast=yes

  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:82:02:1c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 96:dc:f8:45:4d:33
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.224 link=yes multicast=yes

Sorry for the long post, I just wanted to cover most of the commands that are usually asked here. And this question has been asked a million and half times, but none of the situations have been quite like mine and all the 'fixes' I tried didn't help. Drivers are installed, and have been reinstalled numerous times. Help? 

Thanks :)

---

### Post by CHUMitu on 2010-08-22
Bumping for help

---

### Post by vladkonan on 2010-08-23
deleted..

---

### Post by sonofcronus on 2010-10-01
I have the exact same problem with my Dell 1520. Did you ever find a solution?

---

### Post by lrios on 2010-10-19
[SIZE=4]Hi, I solve this same problem on my dell inspiron 1764, i3. These link will help you,

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9972124](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9972124)

[https://bugzilla.kernel.org/show_bug.cgi?id=14098](https://bugzilla.kernel.org/show_bug.cgi?id=14098)

See you, and best regards.

Luis Ríos[/SIZE]

---

