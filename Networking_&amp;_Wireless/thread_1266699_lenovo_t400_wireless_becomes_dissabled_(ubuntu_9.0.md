---
title: "lenovo t400 wireless becomes dissabled (ubuntu 9.04)"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by drak10687 on 2009-09-14
Hi,
Just installed ubuntu 9.04 the other day.  Everything was working fine, then my wirless stopped working.  After complete reinstall, it was working fine again on ath5k driver, until about 1 hour after reinstall, when it disconnected from one network, and I couldn't connect to any other either.  After reboot, no networks are detected (all hard switches seem to be on).

I tried switching to madwifi driver through System/Administration/Hardware Drivers ... but after reboot, this makes the wireless card disappear completely from network manager.  I can only get it back by blacklisting ath_hal and ath_pci... so basically reverting to ath5k... but then the same problem persists as described above.

the chipset is an Atheros AR242x 802.11abg Wireless PCI Express Adapter, heres some output from various diagnostics... most notably (to me) lshw -C network says that it is DISABLED.

```
lshw -C network  
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:22:68:0c:d4:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 latency=0 module=e1000e multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2c:e3:b4:6b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 5a:90:b5:6d:fe:81
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)
00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)
00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)
00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)
15:00.3 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev ff)
15:00.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)
15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11)
```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
```

Any suggestions?  Should I try installing madwifi drivers manually?  Some other driver?


Thanks.

---

### Post by chili555 on 2009-09-15
Often, the notation DISABLED tells us that that hardware wireless switch has been nudged over to OFF. Please check. Also please check the state of the Fn key. Fn+F5, perhaps? Is the wireless LED on or flickering?

---

### Post by drak10687 on 2009-09-19
> **chili555 said:**
> Often, the notation DISABLED tells us that that hardware wireless switch has been nudged over to OFF. Please check. Also please check the state of the Fn key. Fn+F5, perhaps? Is the wireless LED on or flickering?

Ok, first of all the wireless LED has never been on (or flickered) since I installed ubuntu 9.04 (it does work in win 7 properly), even when the wireless is working.

As for the Fn+5 key, I'm not sure what behavior its supposed to have in ubuntu (in windows I could toggle the bluetooth and the wireless with it), but I can only turn the bluetooth radio on/off with it.

I can only turn the wireless off using the hard switch which turns all radios off (including bluetooth).

To update my original post, now that I've had ubuntu 9.04 running for several days.  The wireless DOES work most of the time (using the ath5k drivers), but it chooses seemingly random times to stop working (this happens at least once a day).  By stop working, I mean first it will say its disconnected and will attempt to reconnect with no success.  Then, if I right-click and uncheck "Enable Wirless" and then check it again, it will no longer detect any networks and, IIRC, say "device not ready".

To get my wireless back, I can either wait for a while (say an hour or so) after which it sometimes "magically" comes back.  Or shutting down and restarting the computer has so far proved to re-enable it every time... though clicking "restart" rather than "shut down" does not guarantee so.

I have yet to test madwifi drivers properly since right now the system is usable (though annoying).

---

### Post by EvanCarroll on 2009-10-17
Try this, `rfkill list` you should get something like 
ecarroll@x60s:/etc/acpi$ rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: yes
1: tpacpi_wwan_sw: Wireless WAN
	Soft blocked: no
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Then you can do `rfkill unblock 1`.

Disable/Renable the device in nm-applet for it to catch on.

---

### Post by drak10687 on 2009-10-17
Thanks for the suggestion, I'll give it a try.

Another observation I've made over the past month or so is that the problem only occurs when I'm connected to my university's wireless network (which is known to be unstable for all users)... it has never happened on the two home wireless networks that I use.  Its bizzare though, because its not like the connection just drops, I'm unable to use the device... don't know if its possible that a wireless network would make my adapter go crazy.

---

### Post by drak10687 on 2009-10-17
hmm, I got rfkill from [http://wireless.kernel.org/download/rfkill/](http://wireless.kernel.org/download/rfkill/) , made it and moved the bin to /dev/rfkill... 

when I do `rfkill list`, it just goes in some infinite loop printing something similar to what you have listed in your example, and then "Wrong size of RFKILL event" until I kill it...

I'm not very familiar with compiling programs and I couldn't find any specific instrucitons on how to install this one, so maybe I did something wrong.

---

