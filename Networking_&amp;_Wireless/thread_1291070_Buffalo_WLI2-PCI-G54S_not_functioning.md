---
title: "Buffalo WLI2-PCI-G54S not functioning"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by grigjd3 on 2009-10-14
I'm sorry for the lack of detail in the title but since getting ubuntu, I've found the Network Manager to be really scarce on details.  I have a specially built _desktop_PC with the following hardware:

1 Procase Miditower Zirco 5608 
1 Intel Core 2 Duo E8500 FSB1333 S775
1 Intel Mainboard DG45ID S775
1 Zotac GeForce GTX 260-2 896 MB PCIe
1 Kingston 4GB Dual-Kit DDR2-RAM 800MHz
1 LG DVD-Burner GH22N SATA
1 LC Power Netzeil Taurus 560W
1 Buffalo WLan-PCI-Adapter (WLI2-PCI-G54S)

The only other details are cooling and peripherals.  I set it up to dual boot Windows Vista and Ubuntu 9.04 (AMD64 LiveCD installed - standard desktop edition).  

At home, my only internet connection is a DHCP wireless router provided by the landlord to the building.  It's WEP40 encrypted and I have the correct passphrase.  In windows, my wireless card can successfully find and have internet access to the router.  However, I am having trouble in Ubuntu.  Network Manager does not find any networks and when I create a new profile with the correct router information, it does not find that network.  

When I type the following into the console: sudo lshw -C network
the section with the wlan0 heading says it is Disabled.

I tried the command: sudo iwconfig wlan0 
I am told the power of the wireless card is set to 20dB
I have tried upping that power with: sudo iwconfig wlan0 txpower 30
however the max power it allows is 20dB.

I very much want to use this computer for something other than just video games so I really need internet access.  I know the wireless card is functioning because it works fine in Windows.  I believe the correct driver is installed because iwconfig reports data on the part.   Many sites only discuss this with laptops and they only deal with laptops which have a wireless power button (for energy saving).  Lastly, I never turn the device off in windows.    I have not seen any posts about this problem with desktops.  Please help!

---

