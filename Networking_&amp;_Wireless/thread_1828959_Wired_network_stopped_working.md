---
title: "Wired network stopped working"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by Shompol on 2011-08-19
Hello, I have not used wired network on my desktop for some time, and now it appears to be not functional. Wifi works fine. 

[SIZE=1][COLOR=DarkRed][COLOR=#00cccc]sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes[/COLOR][/COLOR][/SIZE][COLOR=DarkRed]
[/COLOR]
I tried to manually update the config to managed=true, but that did not help:

 [SIZE=1][COLOR=#33ccff]shompol@htpc:~$ cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true[/COLOR][/SIZE]

---

### Post by Iowan on 2011-08-20
That color is hard to read...
You an see if [this]("http://ubuntuforums.org/showthread.php?t=1409587") thread helps.

---

### Post by Shompol on 2011-08-20
Ok, completely removed Virtualbox from the system. Now:

[FONT=Courier New][SIZE=1][COLOR=Navy]$ sudo lshw -C network
  *-generic               
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:08:54:8d:6d:f4
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.0.196 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:20 memory:f9000000-f900ffff[/COLOR][/SIZE][/FONT]

Full lshw found the following:
[FONT=Courier New][SIZE=1][COLOR=Navy]        *-serial UNCLAIMED
             description: SMBus
             product: 82801JI (ICH10 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 00
             width: 64 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:f9106000-f91060ff ioport:500(size=32)[/COLOR][/SIZE][/FONT]

---

### Post by Shompol on 2011-08-20
sudo lspci -vvv
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
    Subsystem: Giga-byte Technology Device 5001
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 4
    Region 0: Memory at f9106000 (64-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

---

### Post by Shompol on 2011-08-20
after [FONT=Courier New][COLOR=Sienna]sudo modprobe  i2c-i801[/COLOR]

I get a driver in use!!!

 $ sudo lspci -vvv

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
    Subsystem: Giga-byte Technology Device 5001
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin C routed to IRQ 18
    Region 0: Memory at f9106000 (64-bit, non-prefetchable) [size=256]
    Region 4: I/O ports at 0500 [SIZE=32]
    [B][SIZE=1]Kernel driver in use: i801_smbus
    Kernel modules: i2c-i801[/SIZE][/B][/SIZE][/FONT]


However ifconfig still only shows lo and wlan, --> no lan.

---

### Post by praseodym on 2011-08-21
Can you show:

```
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by Shompol on 2011-08-21
[FONT=Courier New]$ lspci -nnk 
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
        Kernel driver in use: i801_smbus
            Kernel modules: i2c-i801
04:00.0 Network controller [0280]: RaLink RT2800 802.11n PCI [1814:0601]
        Kernel driver in use: rt2860
            Kernel modules: rt2860sta

$ lsmod
Module                  Size  Used by
i2c_i801                   9306  0 
rt2860sta             542482  1 
[/FONT]

---

### Post by praseodym on 2011-08-21
Did you check the BIOS-settings?

The interface name is vboxnet0 according to the first posting. Do you use Ubuntu in a virtual machine? In that case you have do deactivate wireless in your VBox/VMWare settings and activate cable.

---

### Post by Shompol on 2011-08-21
> **praseodym said:**
> Did you check the BIOS-settings?

The interface name is vboxnet0 according to the first posting. Do you use Ubuntu in a virtual machine? In that case you have do deactivate wireless in your VBox/VMWare settings and activate cable.

I have not touched BIOS since the last time LAN worked. Since you think it could be BIOS. any setting in particular I should look at?

Interface vboxnet0 was installed by virtualbox-ose. I use it to run Windows XP inside Ubuntu. As mentioned above I completely uninstalled the package, and hence the interface is gone too. While it is possible that it could cause the problem originally, virtualbox is no longer relevant.

"...and activate cable" -- that's the part I need help with.

Thank you
- Shompol

---

### Post by praseodym on 2011-08-21
Tried to reinstall the kernel via wireless?

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) dkms build-essential
```
and reboot.

---

### Post by Shompol on 2011-08-21
> **praseodym said:**
> Tried to reinstall the kernel via wireless?

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) dkms build-essential
```and reboot.

Ok. No observable change.

---

### Post by praseodym on 2011-08-21
Errrr, what about the reinstallation of virtualbox-ose?! Does it occur after that?

---

### Post by Shompol on 2011-08-21
> **praseodym said:**
> Errrr, what about the reinstallation of virtualbox-ose?! Does it occur after that?

We already established that LAN did not work with virtualbox installed, not to mention that it is a 3rd party program not designed to fix kernel issues. While anything is possible, some experiments are not worth the salt.

---

### Post by Shompol on 2011-10-05
[SIZE=4]Solution found!! 
[/SIZE]
Thank you to everyone who helped, especially Praseodym. 

I just assume that my network port died: bought a new PCI network adapter for $13 on Newegg. Plugged it in, booted and got 1000 Mbps out of the box.

Yes, sometimes the solution is as prosaic as that. 

And now, the logs of a working system, just for kicks and giggles:

[SIZE=3]**sudo lshw -C network**[/SIZE]
  *-network:1
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: eth0
       version: 10
       serial: 00:0a:cd:1e:1f:8e
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1GB/s
       resources: irq:19 ioport:d000(size=256) memory:fa010000-fa0100ff memory:fb700000-fb71ffff(prefetchable)

[SIZE=3]** sudo lspci -vvv**[/SIZE]
04:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: I/O ports at d000 [size=256]
    Region 1: Memory at fa010000 (32-bit, non-prefetchable) [size=256]
    [virtual] Expansion ROM at fb700000 [disabled] [size=128K]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: r8169
    Kernel modules: r8169

---

