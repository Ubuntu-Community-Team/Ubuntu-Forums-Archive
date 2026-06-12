---
title: "Wireless network card disabled"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by Betobuntu on 2010-06-09
About 3 days ago, i remeve the battery from my laptop (Lenovo U350). and when i put the battery back on the laptop, the wifi card was not picking up any networks. my wireless card is a: Intel Pro Wireless 5100 abgn i have check out other threads but not have had this is issue by removing the battery. i thinking maybe the card got fried, but i dont see how that could happen

---

### Post by maestrobwh1 on 2010-06-09
This is a hunch: open a terminal and issue these commands:

service network-manager stop
rm /var/lib/NetworkManager/NetworkManager.state
service network-manager start


then try to connect.

---

### Post by Betobuntu on 2010-06-10
i tried the commands you supplied, but i must treport that they did not Enable the wireless card. I tried them twice;
 
The first time i did it with the switch set to ON, typed in the commands, and nothing happened
 
The second time i tried it i did it with the switch set to OFF, typed in the commands and nothing again.

---

### Post by Iowan on 2010-06-10
Does the file get rebuilt - or does it stay deleted?
If you right-click Network Manager icon, does it show networking enabled?

---

### Post by Betobuntu on 2010-06-10
right clicking the network icon shows that networking is enabled, but wireless is disabled

---

### Post by Betobuntu on 2010-06-10
wired internet works fine, wireless is still grayed and labeled "Disabled" when right click on Network Manager icon.
Wireless network manual switch is set to "on" position.
Have tried rebooting with switch in both "on" and "off" position

---

### Post by Betobuntu on 2010-06-10
[EMAIL="luis@ubuntu:~$"]luis@ubuntu:~$[/EMAIL] ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:f2:2b:f5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)
 
 
[EMAIL="luis@ubuntu:~$"]luis@ubuntu:~$[/EMAIL] iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
 
 
[EMAIL="luis@ubuntu:~$"]luis@ubuntu:~$[/EMAIL] sudo lshw -C Network
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       logical name: wlan0
       version: 00
       serial: 00:22:fb:90:10:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:f2000000-f2001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:08:00.0"]pci@0000:08:00.0[/EMAIL]
       logical name: eth0
       version: 01
       serial: 00:23:8b:f2:2b:f5
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb v2.05 latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:33 memory:f4500000-f450ffff

---

### Post by Betobuntu on 2010-06-11
still have not solved issue, can anybody help?

---

### Post by Betobuntu on 2010-06-11
im tryin something i read in another thread, to remove the battery, press the power button to release any stored energy in the capicitors, and reinstall the battery after a day

---

### Post by Betobuntu on 2010-06-14
i have solved the issue by pressing "F2" at initial boot, to enter the BIOS menu. Then i pressed "F9" to reset BIOS and then "F10" to save and exit.

---

### Post by panoet on 2010-06-15
I have the same problem and  solve it by force turning off my computer, for example by removing the  battery. Then turn it on, of course after the file  system check first. It worked, but I  think this is not the solution. Ubuntu, how about this? Are you going to fix this?

---

