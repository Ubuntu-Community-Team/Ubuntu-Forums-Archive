---
title: "Wireless not working after updating Ubuntu 10.04 netbook edition"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by samvedan on 2012-02-28
I updtaed ubuntu 10.04 netbook edition one week ago through update manager. Since then, there is no wireless icon and wireless has stopped working. How can i solve this problem?

---

### Post by samvedan on 2012-02-28
Here are the results of some commands: 

**lspci**

[I]00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)[/I]

 **lspci -nvn | grep 8192**
 
*Kernel modules: r8192ce_pci*

---

### Post by samvedan on 2012-02-28
iwconfig
[I]lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
[/I]

---

### Post by varunendra on 2012-03-01
Try compiling and installing rtl8192ce driver from realtek's site here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

The installation instructions are usually given in a README file included in the downloaded archive. One thing to take care of, as some people have reported, is to become root while compiling and installing by:
```
sudo su
```
Just adding *sudo* before each command apparently does not work with this driver for some reason unknown to me. Simply use '*exit*' command after the installation is finished.

Another thing before compiling the driver is to make sure that the packages required to build it are preinstalled. If not sure, this would do it (while you are connected via ethernet):
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
```
It would reinstall the packages even if they are already installed.

If having any problems before or after trying above, please post back with the outputs of following commands:
```
lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list all
```

While posting the outputs, click on **# **at the top of edit box to auto-generate [ code]..[ /code] tags, then copy-paste the output code in-between those tags.

---

