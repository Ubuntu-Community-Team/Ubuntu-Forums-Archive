---
title: "Realtek WLAN Adapter not working on Acer TravelMate 250 with Ubuntu 10.10"
date: 2011-06-22
forum: Networking &amp; Wireless
---

### Post by MagnoliaKaki on 2011-06-22
Hello.

(For the record, I have already read the other threads. Either they don't work for me or are too difficult.) 

My laptop is an Acer TravelMate 250. I have installed Ubuntu 10.10 (2.6.35-28 generic i686) after erasing Windows 7. 

At first, the usb wireless adapter worked. Then, I restarted the PC because of some updates and it didn't work anymore. In "edit connections" I find "Auto SpeedTouch8350DB" which is the wireless connection (on my sis's computer it works). When it tries to connect, I'm asked the password but it doesn't work. 

*lspci*
> 02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C C+ (rev10)

*lsusb*
> Bus 001 Device 010: ID Obda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

*iwconfig*
> lo no wireless extensions.
etho no wireless extensions.

*network configuration*
> descripion: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: a
bus info: pci@0000:02:0a.0
logical name: eth0
version: 10
serial: 00:0a:e4:03:4e:e7
size: 10MB/s
capacity: 100MB/s 
width: 32 bits
clock; 33MHz
capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotation
configuration: autonegotation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=19MB/s

*scan for networks*
> lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.

Thankyou very much for your help! :D And be patient, I don't have any experience in this matters.

---

### Post by chili555 on 2011-06-22
I don't suppose you'd care to update to 11.04 where there is a newer go-fast driver...?? No? OK, let's gather some diagnostic data. You can copy and paste from a terminal to a text document and post it here; transfer the text document on a USB key if needed.

Open a terminal and run and post:> lsmod | grep 819
dmesg | grep -e 819 -e wlan
rfkill list allThe pipe symbol | is on the right side of my US keyboard on the same key with \. Once we have your readings, we'll know a bit more about what's happening under the hood.

---

### Post by MagnoliaKaki on 2011-06-22
11.04 doesn't work because my graphic card is old...

Anyway:

*lsmod | grep 819*
> r819_usb     287340     0 
eeprom_93cx6          1345     1   r8192s_usb

*dmesg | grep -e 819 -e wlan*
> [    0.458191] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT] 
[  729.132736] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned. 
[  729.153368] Linux kernel driver for RTL8192 based WLAN cards 
[  729.450492] usbcore: registered new interface driver rtl819xU 
[  729.543574] udev[1907]: renamed network interface wlan0 to wlan1 
[  729.701588] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a 
[  729.701953] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a 
[  729.726974] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a 
[  729.727307] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a 
[  729.727318] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed! 
[  729.763201] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a 
[  729.763462] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a 
[  729.785899] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a 
[  729.786181] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a 
[  729.786192] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed! 

*rfkill list all*
it doesn't say anything...

thankyou for helping me.

---

### Post by chili555 on 2011-06-22
> rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a This ain't good! Do you have an ethernet connection? If so, please open a terminal and do:```
sudo mkdir /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/
```Reboot and tell us if it's working.

---

