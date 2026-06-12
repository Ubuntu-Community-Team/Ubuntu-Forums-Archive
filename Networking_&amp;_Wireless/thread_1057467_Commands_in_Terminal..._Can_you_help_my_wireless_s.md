---
title: "Commands in Terminal... Can you help my wireless setup?"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by badbowtie03 on 2009-02-01
Hey everyone, im having trouble with my wireless setup and here are some commands that I put in the terminal to help yall figure out what im doing wrong...

I posted the information here: 

[http://pastebin.com/m703f820f](http://pastebin.com/m703f820f)

Can anyone tell me whats wrong with my setup? thanks alot!

---

### Post by kevdog on 2009-02-01
That info you posted was very worthless without telling us the chipset you want to get up and running!

---

### Post by badbowtie03 on 2009-02-02
I have a thinkpad T500 with the 11 b/g Wireless LAN Mini PCI Express Adapter III and the manufacturer is Atheros Communications. Does that help any? Thanks!

---

### Post by kevdog on 2009-02-02
More info please:

lshw -C network
lspci -nnm

Thanks

---

### Post by badbowtie03 on 2009-02-02
here you go! thanks.

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:9a:44:9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.8-3 latency=0 module=e1000e multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:a0:70:a3:6d:d2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


 lspci -nnm
00:00.0 "Host bridge [0600]" "Intel Corporation [8086]" "Mobile 4 Series Chipset Memory Controller Hub [2a40]" -r07 "Lenovo [17aa]" "Device [20e0]"
00:01.0 "PCI bridge [0604]" "Intel Corporation [8086]" "Mobile 4 Series Chipset PCI Express Graphics Port [2a41]" -r07 "" ""
00:03.0 "Communication controller [0780]" "Intel Corporation [8086]" "Mobile 4 Series Chipset MEI Controller [2a44]" -r07 "Lenovo [17aa]" "Device [20e6]"
00:03.2 "IDE interface [0101]" "Intel Corporation [8086]" "Mobile 4 Series Chipset PT IDER Controller [2a46]" -r07 -p85 "Lenovo [17aa]" "Device [20ea]"
00:03.3 "Serial controller [0700]" "Intel Corporation [8086]" "Mobile 4 Series Chipset AMT SOL Redirection [2a47]" -r07 -p02 "Lenovo [17aa]" "Device [20ec]"
00:19.0 "Ethernet controller [0200]" "Intel Corporation [8086]" "82567LM Gigabit Network Connection [10f5]" -r03 "Lenovo [17aa]" "Device [20ee]"
00:1a.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #4 [2937]" -r03 "Lenovo [17aa]" "Device [20f0]"
00:1a.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #5 [2938]" -r03 "Lenovo [17aa]" "Device [20f0]"
00:1a.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #6 [2939]" -r03 "Lenovo [17aa]" "Device [20f0]"
00:1a.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB2 EHCI Controller #2 [293c]" -r03 -p20 "Lenovo [17aa]" "Device [20f1]"
00:1b.0 "Audio device [0403]" "Intel Corporation [8086]" "82801I (ICH9 Family) HD Audio Controller [293e]" -r03 "Lenovo [17aa]" "Device [20f2]"
00:1c.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801I (ICH9 Family) PCI Express Port 1 [2940]" -r03 "" ""
00:1c.1 "PCI bridge [0604]" "Intel Corporation [8086]" "82801I (ICH9 Family) PCI Express Port 2 [2942]" -r03 "" ""
00:1c.3 "PCI bridge [0604]" "Intel Corporation [8086]" "82801I (ICH9 Family) PCI Express Port 4 [2946]" -r03 "" ""
00:1c.4 "PCI bridge [0604]" "Intel Corporation [8086]" "82801I (ICH9 Family) PCI Express Port 5 [2948]" -r03 "" ""
00:1d.0 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #1 [2934]" -r03 "Lenovo [17aa]" "Device [20f0]"
00:1d.1 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #2 [2935]" -r03 "Lenovo [17aa]" "Device [20f0]"
00:1d.2 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB UHCI Controller #3 [2936]" -r03 "Lenovo [17aa]" "Device [20f0]"
00:1d.7 "USB Controller [0c03]" "Intel Corporation [8086]" "82801I (ICH9 Family) USB2 EHCI Controller #1 [293a]" -r03 -p20 "Lenovo [17aa]" "Device [20f1]"
00:1e.0 "PCI bridge [0604]" "Intel Corporation [8086]" "82801 Mobile PCI Bridge [2448]" -r93 -p01 "" ""
00:1f.0 "ISA bridge [0601]" "Intel Corporation [8086]" "ICH9M-E LPC Interface Controller [2917]" -r03 "Lenovo [17aa]" "Device [20f5]"
00:1f.2 "SATA controller [0106]" "Intel Corporation [8086]" "ICH9M/M-E SATA AHCI Controller [2929]" -r03 -p01 "Lenovo [17aa]" "Device [20f8]"
00:1f.3 "SMBus [0c05]" "Intel Corporation [8086]" "82801I (ICH9 Family) SMBus Controller [2930]" -r03 "Lenovo [17aa]" "Device [20f9]"
01:00.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "Mobility Radeon HD 3650 [9591]" "Lenovo [17aa]" "Device [2117]"
03:00.0 "Ethernet controller [0200]" "Atheros Communications Inc. [168c]" "AR242x 802.11abg Wireless PCI Express Adapter [001c]" -r01 "Atheros Communications Inc. [168c]" "Device [0035]"
15:00.0 "CardBus bridge [0607]" "Ricoh Co Ltd [1180]" "RL5c476 II [0476]" -rba "Lenovo [17aa]" "Device [20c6]"
15:00.1 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -r04 -p10 "Lenovo [17aa]" "Device [20c7]"
15:00.2 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r21 "Lenovo [17aa]" "Device [20c8]"
15:00.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -rff -pff "" ""
15:00.4 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r11 "Lenovo [17aa]" "Device [20ca]"
15:00.5 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -r11 "Lenovo [17aa]" "Device [20cb]"

thanks alot for helping!

---

### Post by kevdog on 2009-02-02
there is your chipset AR242x -- need ath5k driver which is in the backports repository.

---

### Post by Bobbertt on 2009-02-03
Every time I log on to Ubuntu, I have to open a terminal window and type in 
 sudo dhclient wlan0 
before I can get an IP address so That I can get online. #-o
I'm using a Netgear WG111 v2 USB wireless connector with Ubuntu 8.10 Intrepid Ibex and a ndiswrapper.

---

### Post by badbowtie03 on 2009-02-03
> **kevdog said:**
> there is your chipset AR242x -- need ath5k driver which is in the backports repository.

Hey I really appreciate it! but where is the backports repository? Within ubuntu? How do I activate it? With ndiswrapper uitility thing? Sorry for being such a newb.  :popcorn:

---

### Post by kerry_s on 2009-02-03
> **Bobbertt said:**
> Every time I log on to Ubuntu, I have to open a terminal window and type in 
 sudo dhclient wlan0 
before I can get an IP address so That I can get online. #-o
I'm using a Netgear WG111 v2 USB wireless connector with Ubuntu 8.10 Intrepid Ibex and a ndiswrapper.

put: dhclient wlan0 &
in /etc/rc.conf and it will do it at boot.

---

### Post by Crafty Kisses on 2009-02-03
Here's more information on Backports: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports).

---

### Post by kevdog on 2009-02-03
To use ath5k install linux-backports-modules-intrepid

sudo aptitude install linux-backports-modules-intrepid

and then you can enable it in System > Administration > Restricted Drivers Manager, where you will saw a driver for Atheros 5xxx -- specifically you want the ath5k driver.

---

### Post by badbowtie03 on 2009-02-04
> **kevdog said:**
> To use ath5k install linux-backports-modules-intrepid

sudo aptitude install linux-backports-modules-intrepid

and then you can enable it in System > Administration > Restricted Drivers Manager, where you will saw a driver for Atheros 5xxx -- specifically you want the ath5k driver.

Im sorry... I dont know how to follow this. I went into ubuntu and I couldnt find "linux-backports-modules-intrepid"  What does that mean? Is it a program i need to install? Can you give me step by step directions? I am just so new to all this that i dont know how to follow all your lingo. Oh and if it helps, i also looked for the system/sdministration/restricted drivers manager... and thats not listed in there either. Does it only pop up once I install the intrepid thing? thanks alot for the help.

---

