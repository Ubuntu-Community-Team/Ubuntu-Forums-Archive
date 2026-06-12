---
title: "Wireless-N driver installed, but no internet"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by g-raf on 2010-10-26
I have no internet available, but the driver seems to be installed (kernel driver r8169). I'll follow the steps for posting on the wireless forum this time:

1) I'm using a desktop. Intel Core i7-870 2.93Ghz 8md Quad Core. Motherboard is an ASRock H55M-LE LGA1156. 4GB RAM DDR3. 

2) The wireless card is:

  	 	 	 	p { margin-bottom: 0.08in; }  01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)  
         Subsystem: ASRock Incorporation Device 8168  
         Flags: bus master, fast devsel, latency 0, IRQ 28  
         I/O ports at c800 [size=256]  
         Memory at cfdff000 (64-bit, prefetchable) [size=4K]  
         Memory at cfdf8000 (64-bit, prefetchable) [size=16K]  
         Expansion ROM at f7ee0000 [disabled] [size=128K]  
         Capabilities: <access denied>  
         Kernel driver in use: r8169  
         Kernel modules: r8169  
 

 04:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190  
         Subsystem: Realtek Semiconductor Co., Ltd. Device 8190  
         Flags: bus master, medium devsel, latency 32, IRQ 6  
         I/O ports at d800 [size=256]  
         Memory at f7fff000 (32-bit, non-prefetchable) [size=4K]  
         Capabilities: <access denied> 



lspci:


01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190




What can I do to get internet? I'm currently using my friends usb wireless card.

---

### Post by g-raf on 2010-10-26
Here's more info:

  	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  sudo lshw -C network 
  	 	 	 	p { margin-bottom: 0.08in; *-network                        description: Ethernet interface 
        product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:01:00.0 
        logical name: eth0 
        version: 03 
        serial: 00:25:22:66:94:8e 
        size: 10MB/s 
        capacity: 1GB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
        resources: irq:28 ioport:c800(size=256) memory:cfdff000-cfdfffff(prefetchable) memory:cfdf8000-cfdfbfff(prefetchable) memory:f7ee0000-f7efffff(prefetchable) 
   *-network UNCLAIMED 
        description: Network controller 
        product: Realtek Semiconductor Co., Ltd. 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 



Please help. I'm clueless at this point.

---

### Post by g-raf on 2010-10-26
I've had pretty bad luck getting feedback on ubuntu forums. If there's something I'm doing wrong, please let me know. I really need to get help with this wireless problem.

---

### Post by chili555 on 2010-10-26
You have the r8169 driver installed all right; it's for your wired ethernet card. A driver for the wire*less* is not yet installed. Please run this command:```
lspci -nn
```You will find the pci.id for the wireless card:> 04:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8190
Subsystem: Realtek Semiconductor Co., Ltd. Device 8190 It might be something like 10ec:8190.

With that detail, we can Google and search this forum for the driver and install it.

I will be back in about 9 hours.

---

### Post by g-raf on 2010-10-27
Yes

> 01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03) 
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8190] 

10ec:8190. Looks like the [Realtek 8190 might not have a linux driver]("http://ubuntuforums.org/showthread.php?t=1552893") that works. jlucio in [this thread]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1433401") said they got it working on 9.10. What do you think?

---

### Post by chili555 on 2010-10-27
I agree that, at this time, ndiswrapper is the preferred solution.

You can skip the blacklist step. There is no module rtl8190.

Do you have these?> The one I used was exactly the one that came with the product, more precisely the WinXP x86 driver named "rtl8190p.sys" and "net8190.inf".Please let me know if you get stuck.

---

### Post by g-raf on 2010-10-27
When I try to install the net819xp.inf driver that comes with the hardware, the ndiswrapper installer tells me that "Driver is Already Installed." I know it's not installed because it's not in the /lib/firmware/ spot that it should be.

---

### Post by chili555 on 2010-10-27
> **g-raf said:**
> When I try to install the net819xp.inf driver that comes with the hardware, the ndiswrapper installer tells me that "Driver is Already Installed." I know it's not installed because it's not in the /lib/firmware/ spot that it should be.Actually, it is installed in /etc/ndiswrapper.


[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)> 3.4.2. Installing Windows driver using command line

In a Terminal, run the following command:

    *

        sudo ndiswrapper -i ~/drivers/drivername.inf

      (assuming the driver is in a directory in your home folder called drivers, and is named drivername.inf) 

ndiswrapper then copies the .inf and sys files into /etc/ndiswrapper/.... Don't forget that the filename you type in is case-sensitive. Does this command say that the driver is installed?```
ndiswrapper -l
```(l is for 'list.')

Do you have a wireless interface, wlan0 perhaps?```
iwconfig
```

---

### Post by g-raf on 2010-10-27
I'm currently using my friend's usb wireless card and it's working under wlan0 device. 

ndiswrapper -l gives me this:

> autorun : invalid driver!
net819xp : invalid driver!

---

### Post by chili555 on 2010-10-27
I'm not quite sure where 'autorun' came from. I'd suggest you do:```
sudo ndiswrapper -e autorun
sudo ndiswrapper -e net819xp.inf
sudo rm -rf /etc/ndiswrapper/*
```Proofread these commands carefully before you press Enter.

Now make sure the files net819xp.inf and rtl819xp.sys *and nothing else* are in the same folder. Now navigate to that folder:```
cd folderyoucreated
ndiswrapper -i net819xp.inf
```The system should grab the .sys file automatically. Next, do:```
sudo depmod -a
sudo modprobe ndiswrapper
```Post back and let me know how it goes.

---

### Post by g-raf on 2010-10-27
[FONT=monospace]sudo mobprobe ndiswrapper

[/FONT]> [FONT=monospace]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-network, it will be ignored in a future release.[/FONT]

That's what I got, but the wireless connection is working now! Glory!

Thanks a lot. I'm going to restart the computer to make sure it works. I'll need to mark this thread as [solved]....you know how to do that?

---

### Post by g-raf on 2010-10-27
Nevermind. I just restarted the computer and no internet. Back to my friend's usb wireless card. What can i do to keep it working?

---

### Post by g-raf on 2010-10-27
Now i unplugged my friend's usb wireless card, then did sudo modprobe ndiswrapper

and now I have internet again. Is there some way to keep it working so I don't need to type that all the time?

---

### Post by chili555 on 2010-10-28
Open a terminal and do:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```You should be all set.

---

### Post by g-raf on 2010-10-29
Wireless is working no problem now. Thanks for the help chili555. If anyone is using a Realtek 8190 chipset on a wireless-n pci card, the above posted solution worked on my system with Ubuntu 10.04. Good stuff.

---

