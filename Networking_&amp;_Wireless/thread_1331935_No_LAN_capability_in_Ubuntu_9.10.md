---
title: "No LAN capability in Ubuntu 9.10"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by Albert Seminatore on 2009-11-19
I have a Toshiba P505 ST5800 Laptop.  I installed U 9.04 and all worked just fine.
I have done both a fresh install and an upgrade to U9.10.  In all cases I have no Ethernet LAN or Wifi.  I need the WiFi to access all the other peripherals.  I have searched and tried everything I thought might work on the internet but NOTHING has worked so far.  Below is some of the commands and outputs I got.  You will notice that both the ethernet and wifi are "Unclaimed".  The WiFi switch is on and the light is on.  I checked the BIOS and the LAN is enabled.  There is nothing there for the WiFi.  Can someone Help Please?????

>>>>>>>>>> 
lspci -v | less
>>>>>>>>>>
06:00.0 FireWire (IEEE 1394): O2 Micro, Inc. Device 10f7 (rev 01) (prog-if 10) 
        Subsystem: Toshiba America Info Systems Device ff50 
        Flags: bus master, fast devsel, latency 0, IRQ 19 
        Memory at f4501000 (32-bit, non-prefetchable) [size=4K] 
        Memory at f4500000 (32-bit, non-prefetchable) [size=2K] 
        Capabilities: <access denied> 
        Kernel driver in use: ohci1394 
        Kernel modules: firewire-ohci, ohci1394 

06:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01) 
        Subsystem: Toshiba America Info Systems Device ff50 
        Flags: bus master, fast devsel, latency 0, IRQ 19 
        Memory at f4503800 (32-bit, non-prefetchable) [size=256] 
        Capabilities: <access denied> 
        Kernel driver in use: sdhci-pci 
        Kernel modules: sdhci-pci 

06:00.2 Mass storage controller: O2 Micro, Inc. Device 8130 (rev 01) 
        Subsystem: Toshiba America Info Systems Device ff50 
        Flags: bus master, fast devsel, latency 0, IRQ 11 
        Memory at f4502000 (32-bit, non-prefetchable) [size=4K] 
        Memory at f4503000 (32-bit, non-prefetchable) [size=2K] 
        Memory at f4500800 (32-bit, non-prefetchable) [size=2K] 
        Capabilities: <access denied> 

07:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0) 
        Subsystem: Toshiba America Info Systems Device ff50 
        Flags: fast devsel, IRQ 16 
        Memory at b6000000 (64-bit, non-prefetchable) [size=256K] 
        I/O ports at 2000 [disabled] [size=128] 
        Capabilities: <access denied> 
        Kernel modules: atl1c 

08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100 
        Subsystem: Intel Corporation Device 1201 
        Flags: fast devsel, IRQ 17 
        Memory at b6100000 (64-bit, non-prefetchable) [size=8K] 
        Capabilities: <access denied> 
        Kernel modules: iwlagn 


>>>>>>>>>>
al@al-toshiba:~$ lsb_release -a
>>>>>>>>>>
 
No LSB modules are available. 
Distributor ID:	Ubuntu 
Description:	Ubuntu 9.10 
Release:	9.10 
Codename:	karmic 

>>>>>>>>>>
al@al-toshiba:~$ lshw -C network
>>>>>>>>>>
 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Ethernet controller 
       product: Atheros AR8132 / L1c Gigabit Ethernet Adapter 
       vendor: Attansic Technology Corp. 
       physical id: 0 
       bus info: pci@0000:07:00.0 
       version: c0 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
       resources: memory:b6000000-b603ffff ioport:2000(size=128) 
  *-network UNCLAIMED 
       description: Network controller 
       product: Wireless WiFi Link 5100 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:08:00.0 
       version: 00 
       width: 64 bits 
       clock: 33MHz 
       capabilities: cap_list 
       configuration: latency=0 
       resources: memory:b6100000-b6101fff 

>>>>>>>>>>
al@al-toshiba:~$ route -n 
>>>>>>>>>>

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

>>>>>>>>>>
al@al-toshiba:/etc/modprobe.d$ dir
>>>>>>>>>>
 
als
a-base.conf		 blacklist-firewire.conf     blacklist-watchdog.conf 
blacklist-ath_pci.conf	 blacklist-framebuffer.conf  libpisock9.conf 
blacklist-ath_pci.conf~  blacklist-modem.conf 
blacklist.conf		 blacklist-oss.conf

---

### Post by JRC903 on 2009-12-02
For about 3 months I have been using the alpha/beta versions of 9.10 Wubi  version without much trouble.  Once installed, and configured, the LAN and WIFI worked well. Then, I started having trouble with updates over writting my boot settings etc and then making them fail on boot up. (in particular,, the boot sequence would kick into a boot command prompt--- a situation that went no-where)

 I then decided to install 9.10 in its own partitions on the laptop (gateway 7xxs series).  Keeping in mind that the exact same CD installed version that worked so well under Wubi----- was now installed as a real OS. 

However, no matter what i did/do--- I can not get the LAN recognized by the OS system. Since I can not get LAN working,i can not download the required files etc to get the wireless LAN working either. 

Now--- I have reinstalled WUBI and have LAN access. But still have not gotten WIFI to work.  to get any work down at all--- i am in windows.  Pretty sad--- actually.. but what Im i suppose to do?

If anyone has any suggestions for what is wrong with this system. please let me know.
thanks

---

### Post by mostlyGood on 2009-12-10
I also used 9.04 without issue but I can not get wireless to work on my P505-s8950 with 9.10. The driver is "unclaimed".

I am also using Windows because I can not get it working.

---

### Post by mcooke1 on 2009-12-17
Toshiba P500 PSPG8A-01U004 same issues access denied.


07:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
    Subsystem: Toshiba America Info Systems Device ff50
    Flags: fast devsel, IRQ 16
    Memory at be000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [disabled] [size=128]
    Capabilities: <access denied>
    Kernel modules: atl1c

08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
    Subsystem: Intel Corporation Device 1201
    Flags: fast devsel, IRQ 17
    Memory at be100000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

I am using a Swann USB ethernet adapter I had purchased for my 2000 model Toshiba while looking for a solution to this problem. It worked immediately plug & play.

---

### Post by mostlyGood on 2010-02-17
Again, I could not get wireless or LAN to work on a fresh install of 9.10 on my Toshiba P505-S8950. I am a beginner and gave up pretty easy and fell back to 9.04. I wasn't very driven to have 9.10.
 
I installed 9.04 and wireless and LAN worked perfectly. Video driver worked after updating. I upgraded to 9.10 and now everything works under 9.10.
 
I wonder if everything would have worked if I could have used a detectable wireless adapter to update 9.10.
 
Hope this helps someone.

---

### Post by Iowan on 2010-02-17
Post results of **sudo lshw -C network** - probably a driver problem, but details will help.

---

### Post by Elfy on 2010-02-17
Thread closed - if the OP stil has issues I will reopen it for them, anyone else can open a thread of their own.

---

