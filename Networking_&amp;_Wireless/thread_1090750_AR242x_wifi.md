---
title: "AR242x wifi"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by Simyager on 2009-03-08
**1. How were you trying to get online? e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.**
I can only go online via wifi

**2. What hardware are you using? The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc. You can generally identify external components from their labelling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).**
fujitsu-siemens V5535 Ubuntu 8.10 64bit, dualboot windows vista, atheros ag5007eg in Ubuntu it's called atheros AR242x

**5. Can you get online with any other method? e.g. if you have a wifi problem, can you connect with ethernet?**
Unfortunatly no that is my only connection.

**6. How are you getting online to post on this forum?**
Via wifi with the same laptop on vista

**7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.**

[I]Code:
lspci
lsusb
lshw -class network
ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 [www.opendns.com](www.opendns.com)[/I]


:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

sudo lshw -C network
*-network 
description: Ethernet interface
product: 191 Gigabit Ethernet Adapter
vendor: Silicon Integrated Systems [SiS]
physical id: 4
bus info: pci@0000:00:04.0
logical name: eth0
version: 02
serial: 00:a0:d1:cd:80:66
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=half latency=0 link=no module=sis190 multicast=yes port=MII speed=10MB/s
*-network UNCLAIMED
description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix cap_list
configuration: latency=0
*-network DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: f6:5b:71:16:e4:1e
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
-----------------------------------------------------------------

------------------------------------------------------------------------------------------------
:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
00:1f.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
------------------------------------------------------------------------------------------------
:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
------------------------------------------------------------------------------------------------
:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:a0:d1:cd:80:66
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 latency=0 module=sis190 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:6f:96:db:99:fa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
------------------------------------------------------------------------------------------------
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:cd:80:66  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15408 (15.4 KB)  TX bytes:15408 (15.4 KB)
------------------------------------------------------------------------------------------------
:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
------------------------------------------------------------------------------------------------
:~$ ping -c 3 208.67.219.101
connect: Network is unreachable
------------------------------------------------------------------------------------------------
:~$ ping -c 3 [www.opendns.com](www.opendns.com)
ping: unknown host [www.opendns.com](www.opendns.com)
------------------------------------------------------------------------------------------------
Please help me I tried many things, but nothing worked

---

### Post by ugm6hr on 2009-03-08
Separate thread started.

Download the following files (pick local mirror):

[http://packages.ubuntu.com/intrepid-updates/amd64/linux-image-2.6.27-11-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-image-2.6.27-11-generic/download)
[http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download)
[http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-intrepid-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-intrepid-generic/download)

Save to HD or USB, then transfer to Ubuntu and double-click (in correct order).

```
echo ath5k | sudo tee -a /etc/modules
gksudo gedit /etc/modprobe.d/blacklist
```
Add the following to the bottom of this file and save:
```
blacklist ath_hal
blacklist ath_pci 
```

Reboot, and it should hopefully work.

Ref: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

---

### Post by binbash on 2009-03-09
[http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_25.html)
[http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html](http://www.ubuntu-inside.me/2009/02/how-to-get-your-atheros-ar242x-working_27.html)

---

### Post by Simyager on 2009-03-09
> **ugm6hr said:**
> Separate thread started.

Download the following files (pick local mirror):
[http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-intrepid-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-intrepid-generic/download)
[http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download)

Save to HD or USB, then transfer to Ubuntu and double-click (in correct order).

```
echo ath5k | sudo tee -a /etc/modules
gksudo gedit /etc/modprobe.d/blacklist
```
Add the following to the bottom of this file and save:
```
blacklist ath_hal
blacklist ath_pci 
```

Reboot, and it should hopefully work.

Ref: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

unfortunatly it didn´t work, when I double-click on the downloads in Ubuntu I get a window and in it, it says in status in red: 

ERROR: Dependency is not satisfiable: linux-backports-modules-2.6.27-11-generic
and it says this on both of the downloads

---

### Post by ugm6hr on 2009-03-09
> **Simyager said:**
> ERROR: Dependency is not satisfiable: linux-backports-modules-2.6.27-11-generic

I think you have downloaded the same file twice.

[http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download)

This is a link to the package that it is looking for (look at the name), which I'm sure is the same as the one I gave earlier.

---

### Post by Simyager on 2009-03-10
> **ugm6hr said:**
> I think you have downloaded the same file twice.

[http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download)

This is a link to the package that it is looking for (look at the name), which I'm sure is the same as the one I gave earlier.

No I don´t think so, because one of them is 1.192kb and the other is just 3 kb. I even checked out the names of them and the first one is linux-backports-modules-2.6.27-11-generic_2.6.27-11.12_amd64 (1).deb and the second one linux-backports-modules-intrepid-generic_2.6.27.11.14_amd64.deb Unfurtunatly it said that on both of them the order of double clicking the downloads din't matter either.

I should tell you that I installed Ubuntu from within vista without a cd I just used daemon tools and I could install it on my laptop without a cd and the Ubuntu CD said that the only negative would be that my disk performance won't be optimum. But the rest of what I've seen thus far works well.

---

### Post by Simyager on 2009-03-13
I tried it. I downloaded both of the files again and checked their names. But unfortunatly I get the same results.

---

### Post by darrenn on 2009-03-13
Please tell me this is fixed in Jaunty.

---

### Post by ugm6hr on 2009-03-13
> **darrenn said:**
> Please tell me this is fixed in Jaunty.

Yes it is.

The intrepid-backports package is backported from standard Jaunty (sort of).

---

### Post by Simyager on 2009-03-14
I am sorry to report that it still doesn't work for me.

Ubuntu 8.10 2.6.27-7 is what I have, at least that´s what the boot says.
and

**linux-backports-modules-intrepid-generic_2.6.27.11.14_amd64 (1).deb** says in the _description_:

[I]Backported drivers for generic kernel image
This empty package allows people to keep their backported modules up-to-date when upgrading their Linux kernel.
[/I]
While the _status_ is : *ERROR : Dependency is not satisfiable: linux-backports-modules-2.6.27-11-generic*

**linux-backports-modules-2.6.27-11-generic_2.6.27-11.12_amd64.deb** says in the _description_ :

[I]Ubuntu supplied Linux modules for version 2.6.27 on x86/x86_64
This package contains modules supplied by Ubuntu for Linux kernel 2.6.27 on x86/x86_64.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. [/I]

the _status_ : *ERROR : Dependency is not satisfiable: linux-image-2.6.27-11-generic*

Please help me if you can and want to help me. I am sorry for the fact that I am nagging but I want it to work.

( ps : does it matter where I put them I just put those files on my desktop and from there I double-clicked on them )

---

### Post by ugm6hr on 2009-03-14
That explains things.  The 2 errors are not identical at all.

> ERROR : Dependency is not satisfiable: linux-image-2.6.27-11-generic
ERROR : Dependency is not satisfiable: linux-backports-modules-2.6.27-11-generic


You have not updated to the latest kernel, hence the latest backports won't work.

Download this one first:
[http://packages.ubuntu.com/intrepid-updates/amd64/linux-image-2.6.27-11-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-image-2.6.27-11-generic/download)

Double-click it.
Reboot.

Then follow original advice: [http://ubuntuforums.org/showthread.php?p=6861397#post6861397](http://ubuntuforums.org/showthread.php?p=6861397#post6861397)

---

### Post by Simyager on 2009-03-15
I want to thank you for your help and endurance with helping a n00b like me. It finally works, I forgot to put those codes though but it still works as I am using Ubuntu to write this now. Actually it was that I had to double-click in the opposite order so the last first after that the upper one.

> **ugm6hr said:**
> Separate thread started.

Download the following files (pick local mirror):
[http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-intrepid-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-intrepid-generic/download)
[http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download](http://packages.ubuntu.com/intrepid-updates/amd64/linux-backports-modules-2.6.27-11-generic/download)

Save to HD or USB, then transfer to Ubuntu and double-click (in correct order).

```
echo ath5k | sudo tee -a /etc/modules
gksudo gedit /etc/modprobe.d/blacklist
```
Add the following to the bottom of this file and save:
```
blacklist ath_hal
blacklist ath_pci 
```

Reboot, and it should hopefully work.

Ref: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)

Thanks and thanks again for everything ;)

( 1 question what should I do when I upgrade my Ubuntu not install those generic and image files or wait for a later date and install 9.04 of Ubuntu? )

---

### Post by ugm6hr on 2009-03-15
You are of course correct - I confused myself, and perhaps changed the order when it didn't work the first time!  Whatever, it's working now.

You should have no future problems with updates.  The -backports module should update with every new kernel in Intrepid (8.10) if necessary.  If it breaks things, you can just go back to the -11 kernel again.

So yes - feel free to update everything.

```
sudo apt-get update
sudo apt-get upgrade
```

As for a dist-upgrade to 9.04 Jaunty, I would anticipate there being no issue, but a fresh install is probably safer.

---

### Post by Simyager on 2009-03-15
well again thank you. I updated fully and fortunately wifi still is working like a charm ;):P:D:D:D \\:D/

---

