---
title: "eee 1000h sleep disables wireless in bios"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by rockstar on 2009-09-02
I put a fresh copy of 9.04 netbook remix on my eee 1000h and it worked fine.  After I ran updates, the wireless stopped working.  I discovered that every time my computer would go to sleep, it would disable wireless in the BIOS.  The only way to fix it that I know of is to reset it, enter the bios and re-enable it.  There was a similar thread [http://ubuntuforums.org/showthread.php?t=1218753&highlight=1000h+wireless&page=2]("http://ubuntuforums.org/showthread.php?t=1218753&highlight=1000h+wireless&page=2") but that didn't really solve the problem or come to any conclusion on how to fix it.  I don't see why updating the wireless drivers would keep it from messing up my BIOS.  any suggestions? thanks

here are some outputs. thanks again

01:00.0 Network controller: RaLink RT2860
	Subsystem: RaLink Device 2790
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: rt2860
	Kernel modules: rt2860sta

paul@eee-1000h:~$ iwconfig
lo        no wireless extensions.

paul@eee-1000h:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:3c:20:30
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 module=atl1e multicast=yes
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:42:c6:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.0.103 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e2:31:f9:6f:d4:f2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



eth0      no wireless extensions.

ra0       RT2860 Wireless  ESSID:"disfunction"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:13:46:CA:40:FA   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=96/100  Signal level:-70 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

---

### Post by Chronon on 2009-09-02
Weird.  Going to sleep makes my backlight stop working until I log out and back in again.  No issues with wireless, though.  

One other odd behavior on my Eee PC 1000HEB is associated with hooking up an external monitor.  It appears that when I do this, the functionality of Fn + F8 changes from switching the screen to another "increase brightness" action.  Some kind of ACPI bugs maybe?

---

