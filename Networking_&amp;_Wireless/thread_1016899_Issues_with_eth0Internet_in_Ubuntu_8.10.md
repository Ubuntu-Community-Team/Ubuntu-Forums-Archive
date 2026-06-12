---
title: "Issues with eth0/Internet in Ubuntu 8.10"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by hajduk on 2008-12-20
Ever since installing Intrepid, I have been having issues with eth0/Internet connection. Right after installation, not even beginning to work with the OS yet, I noticed there was no internet connection. After opening the terminal, I ran ifconfig, which gave me:
```
~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30448 (30.4 KB)  TX bytes:30448 (30.4 KB)
```
There is no eth0 listing. I have had this problem in the past with Hardy, but a reboot of the system fixed that issue. I then ran lspci, which gave me:
```
~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:03.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
```

Everything here seems normal. Since I have not been able to install restricted drivers, running commands in the terminal becomes a nightmare, as the graphics are so bad that if you even move the window the system freezes. Adding auto eth0 / iface eth0 inet dhcp did not fix my issue. Restarting the network gives me SIOCSIFADDR and eth0 errors. Hopefully somebody can help me troubleshoot this issue as best as possible, as I have given as much information as the system has allowed before it froze.

---

### Post by hajduk on 2008-12-20
Anyone have an idea about what I can do?

---

### Post by Ayuthia on 2008-12-20
You might try setting the mtu to 1492:
[https://answers.launchpad.net/ubuntu/+source/network-manager/+question/4630](https://answers.launchpad.net/ubuntu/+source/network-manager/+question/4630)

---

### Post by cariboo on 2008-12-20
Could you run in a terminal:

```
sudo lshw -C network
```

and paste the output in your next post. This will tell us if the driver for your network card is loading.

Jim

---

### Post by gpredrag on 2008-12-20
What does ```
ip link list
``` says?
What's in your /etc/network/interfaces ?

---

### Post by hajduk on 2008-12-20
Running lshw -C network returns:

```
*-network UNCLAIMED     
       description: Ethernet controller
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:23:2d:b1:58:ef
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Sorry for any late responses, I have to switch back and forth between Ubuntu and Windows to run commands.

In /etc/network/interfaces I have
the loopback setting along with
auto eth0
iface eth0 inet dhcp

---

### Post by hajduk on 2008-12-20
For ip link list, it returned:

```
~$ ip link list
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether ce:dd:10:bf:73:20 brd ff:ff:ff:ff:ff:ff
```

---

### Post by wwusnobrdr on 2008-12-20
You can try running sudo ifconfig eth0 up and see if it loads the interface then or let us know if an error popped up.

---

### Post by hajduk on 2008-12-20
Running sudo ifconfig eth0 up returns:

```
~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
```

---

### Post by hajduk on 2008-12-20
I can't mess around with the MTU as the MTU reverts back automatically to 1500, plus network-manager does not seem to load anymore.

---

### Post by gpredrag on 2008-12-20
As far as I know module e100 should manage that card.
does
```
sudo modprobe e100
```

changes anything?

---

### Post by hajduk on 2008-12-20
I added in the e100 for modprobe, and there were no errors, however it doesn't seem to change anything, there is still no internet access.

---

### Post by hajduk on 2008-12-21
Guess I'll have to bump this.

---

### Post by hajduk on 2008-12-21
Any other things you guys can suggest?

---

