---
title: "ACPI BT43 and Nvidia"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by bibble235 on 2011-04-25
Hi,

I have a laptop whose wireless button does not seem to work all of the time. It is an Compaq F500. I bought a usb wireless key to solve the issue. 

However under linux after shutting down or resuming the wireless never gets enabled even with the stick plugged in. I have to boot to windows surf a bit with my wireless key (A TP-Link something or other) and eventually the wireless on the PC goes from orange (not working) to blue (working). If I then remove the key and boot back to linux the onboard wireless works.

If I shut the lid and open the lid it then fails and the log looks like this

Apr 25 20:21:54 billy kernel: [32861.460524] PM: resume of drv:forcedeth dev:0000:00:14.0 complete after 520.312 msecs
Apr 25 20:21:54 billy kernel: [32861.476047] b43-pci-bridge 0000:03:00.0: Refused to change power state, currently in D3
Apr 25 20:21:54 billy kernel: [32861.492047] b43-pci-bridge 0000:03:00.0: Refused to change power state, currently in D3
Apr 25 20:21:54 billy kernel: [32861.492057] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 20 (level, high) -> IRQ 20
Apr 25 20:21:54 billy kernel: [32861.492658] ssb: Failed to switch to core 0
Apr 25 20:21:54 billy kernel: [32861.493252] ssb: Failed to switch to core 0
Apr 25 20:21:54 billy kernel: [32861.523606] sd 2:0:0:0: [sda] Starting disk
Apr 25 20:21:54 billy kernel: [32861.532269] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.532390] PM: resume of devices complete after 1583.822 msecs
Apr 25 20:21:54 billy kernel: [32861.532551] PM: resume devices took 1.584 seconds
Apr 25 20:21:54 billy kernel: [32861.532594] PM: Finishing wakeup.
Apr 25 20:21:54 billy kernel: [32861.532596] Restarting tasks ...
Apr 25 20:21:54 billy kernel: [32861.532890] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.533494] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.534094] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.534694] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.535292] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.535904] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.536278] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.537132] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.537769] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.538415] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.539014] ssb: Failed to switch to core 1
Apr 25 20:21:54 billy kernel: [32861.539019] b43-phy0: Radio hardware status changed to DISABLED

I believe the probably to be related to ACPI but have already tried ACPI=off and ACPIT-noirq and both of these caused issues with the Graphics card but did make the wireless led go blue (working)

Some output to hopefully help.

iwiseman@billy:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

iwiseman@billy:~$ lsmod  |grep b43
b43                   163524  0
mac80211              205402  1 b43
cfg80211              126528  2 b43,mac80211
led_class               2864  1 b43
ssb                    38934  1 b43

iwiseman@billy:~$ lsmod  |grep nvi
nvidia               9961216  41
agpgart                31724  1 nvidia

---

### Post by bibble235 on 2011-04-26
Sorry folks slightly mislead you.

The usb key does work. The kernel was updated to .31 and this caused the ndiswrapper not to work for my TP-Link key. (documented on another post). 

Putting the usb key in does work however the on board network card still does not work unless I work to windows and wait for 3-10 mins.

---

