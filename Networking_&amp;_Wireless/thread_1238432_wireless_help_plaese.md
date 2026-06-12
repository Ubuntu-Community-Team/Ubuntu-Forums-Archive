---
title: "wireless help plaese"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by kseniya-ubi on 2009-08-12
hi all,
I have a new Dell Vostro A840 Laptop computer,
the computer came with a ubuntu os installed on it and was working great,
in order to learn the linux a bit more (i am a new user) I reinstalled the os.
everything is in the right place and I am very happy with the linux except for one thing:
I can't get the wireless card to work..
if I open the Hardware drivers it shows: "Support for Atheros 802.11 wireless LAN card" - in use  but the wireless card does not show in "NETWORK"
I tried everything working on it all day long.

here are some detail about my os and drivers:

kseniya@linux-ubi:~$ uname -a
Linux linux-ubi 2.6.24-24-generic #1 SMP Fri Jul 24 22:46:06 UTC 2009 i686 GNU/Linux
kseniya@linux-ubi:~$ cat /etc/issue
Ubuntu 8.04.3 LTS \n \l

kseniya@linux-ubi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kseniya@linux-ubi:~$ iwlist wlan0 scanning
wlan0     Interface doesn't support scanning.

kseniya@linux-ubi:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:22:19:f4:b2:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=10.0.0.158 latency=0 module=r8169 multicast=yes




Please help me solve out this issue (again I am a linux user for the last 3 days only)


thanx

Kseniya

---

### Post by The Toxic Mite on 2009-08-12
> **kseniya-ubi said:**
> hi all,
I have a new Dell Vostro A840 Laptop computer,
the computer came with a ubuntu os installed on it and was working great,
in order to learn the linux a bit more (i am a new user) I reinstalled the os.
everything is in the right place and I am very happy with the linux except for one thing:
I can't get the wireless card to work..
if I open the Hardware drivers it shows: "Support for Atheros 802.11 wireless LAN card" - in use  but the wireless card does not show in "NETWORK"
I tried everything working on it all day long.

here are some detail about my os and drivers:

kseniya@linux-ubi:~$ uname -a
Linux linux-ubi 2.6.24-24-generic #1 SMP Fri Jul 24 22:46:06 UTC 2009 i686 GNU/Linux
kseniya@linux-ubi:~$ cat /etc/issue
Ubuntu 8.04.3 LTS \n \l

kseniya@linux-ubi:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

kseniya@linux-ubi:~$ iwlist wlan0 scanning
wlan0     Interface doesn't support scanning.

kseniya@linux-ubi:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:22:19:f4:b2:f3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=10.0.0.158 latency=0 module=r8169 multicast=yes




Please help me solve out this issue (again I am a linux user for the last 3 days only)


thanx

Kseniya

What version of Ubuntu are you running?

---

### Post by kseniya-ubi on 2009-08-12
as far as I know its an ubuntu 9.04 or 8.04,
how can I check it ?

one more thing, ever since I tried some things from all forums the wireless card on the hardware drivers show as "Not in use"

---

### Post by superprash2003 on 2009-08-12
do add a sudo to the iwlist scanning command.. post output of **sudo iwlist scanning**

---

### Post by kseniya-ubi on 2009-08-12
kseniya@linux-ubi:~$ sudo iwlist scanning
[sudo] password for kseniya: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

kseniya@linux-ubi:~$

---

### Post by kseniya-ubi on 2009-08-17
eventually I installed the ubuntu 9.04 (first the 8.10) and everything is working great

---

### Post by The Toxic Mite on 2009-08-17
> **kseniya-ubi said:**
> eventually I installed the ubuntu 9.04 (first the 8.10) and everything is working great

Hey! Nice to hear :D

):P

---

