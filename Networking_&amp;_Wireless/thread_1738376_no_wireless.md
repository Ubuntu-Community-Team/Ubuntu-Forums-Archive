---
title: "no wireless?"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by dreadpiratenicole on 2011-04-24
Hi All!  I just installed Ubuntu 10.10 Netbook remix on a Toshiba NB505...  My wireless internet is not working :(  I can connect fine wired, but it doesn't even give me any kind of option for wireless.

If anyone would help it would be greatly appreciated!

Thanks!

---

### Post by josephmills on 2011-04-24
hi there could you please go to **applications-->accessories-->terminal**
then type in ```
sudo apt-get update 
``` then ```
 sudo apt-get upgrade
``` then post the out come of ```
rfkill list all 
``` here thanks

---

### Post by dreadpiratenicole on 2011-04-24
I typed in the get update and get upgrade and it did some thinking.  Then I typed in
> rfkill list all

and nothing happened at all :(

---

### Post by josephmills on 2011-04-24
> **dreadpiratenicole said:**
> I typed in the get update and get upgrade and it did some thinking.  Then I typed in


and nothing happened at all :(
ok try ```
sudo apt-get install rfkill
```
what rfkill does is shows if there is a hard over-ride or a soft one so after you get install it try ```
rfkill list all 
``` then post here thanks

---

### Post by dreadpiratenicole on 2011-04-24
It still didn't seem to work...  this is what I got:
> 
sudo apt-get install rfkill
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rfkill is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
cole@MrHumperdink:~$ rfkill list all
cole@MrHumperdink:~$ 


Thanks

---

### Post by josephmills on 2011-04-24
> **dreadpiratenicole said:**
> It still didn't seem to work...  this is what I got:


Thanks

ok it is installed hmmm... try ```
rfkill list wifi
``` or just ```
rfkill list 
``` please show what happens thanks

---

### Post by dreadpiratenicole on 2011-04-24
> 
cole@MrHumperdink:~$ rfkill list wifi
cole@MrHumperdink:~$ 


The same thing happened where it just goes down to the next line.

---

### Post by josephmills on 2011-04-24
:confused:ok then lets see a ```
sudo lshw -c network
``` thanks**it takes a while to load **

---

### Post by dreadpiratenicole on 2011-04-24
Here ya go:

> 
sudo lshw -c network
[sudo] password for cole: 
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:81:39:9b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.107 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff
cole@MrHumperdink:~$ 


Thanks

---

### Post by josephmills on 2011-04-24
cool found one thing that is wrong  lets see a ```
lspci -nn
```

---

### Post by dreadpiratenicole on 2011-04-24
> 
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
cole@MrHumperdink:~$ 


thanks

---

### Post by josephmills on 2011-04-24
ok make sure that you are wired in and try this 
1)```
sudo add-apt-repository ppa:lexical/hwe-wireless
```
2)```
sudo apt-get update
```
3)```
sudo apt-get install rtl8192ce-dkms
```
4)```
sudo reboot 
```
tell us what happens

---

### Post by dreadpiratenicole on 2011-04-24
I typed everything in, in order, and the computer installed it and rebooted.  There still is no wireless option, however.  

My computer is being feisty.

Thanks

---

### Post by josephmills on 2011-04-24
lets see ```
sudo lshw -C network
``` lets see if the driver is there now

---

### Post by dreadpiratenicole on 2011-04-24
okay, cool

```

cole@MrHumperdink:~$ sudo lshw -C network
[sudo] password for cole: 
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0100000-f0103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 05
       serial: 1c:75:08:81:39:9b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.107 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:3000(size=256) memory:f050c000-f050cfff memory:f0508000-f050bfff
cole@MrHumperdink:~$ 

```

thanks

---

### Post by josephmills on 2011-04-24
dang the driver did not load please go to synaptic package manager then go to setting-->repositories now make sure all are ticked (see pic) press the **EDIT**reload button then close out of synaptic and then ```
sudo apt-get update
```then ```
 sudo apt-get upgrade
``` then reboot again anything?

---

### Post by dreadpiratenicole on 2011-04-24
It worked!  Everything is good!

Thanks so much for your help, I have wireless internets again!

---

### Post by josephmills on 2011-04-24
> **dreadpiratenicole said:**
> It worked!  Everything is good!

Thanks so much for your help, I have wireless internets again!

cool I am glad that everything worked out could you please take a screen shot of your other software tab I think when we tried to add the repo earlier it did not work or a typo or some thing if I could see the synaptic-->settings-->repo--> other tab. Then I will know thanks ohh to take a screen shot just go to applications-->accessories-->take screenshot please put a 3 second delay on it thanks

---

