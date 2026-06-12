---
title: "Lenovo Wireless not detected"
date: 2011-05-10
forum: Networking &amp; Wireless
---

### Post by siroya on 2011-05-10
Hi

I have been using Ubuntu at my home laptop (Dell) have had no problem. However, recently I installed 11.04 in my office laptop - Lenovo B450, but 'm unable to connect thru wireless.

It is simply not detecting the wireless. I have a dual boot with Windows 7. Windows 7 detects wireless (surprisingly).

I have tried configuring the network connection in all possible way (manual / auto).

Please Help

---

### Post by chili555 on 2011-05-10
> I have tried configuring the network connection in all possible way (manual / auto).Ouch! I hope we don't have to undo much.

Please open a terminal and run and post:```
lspci -nn
```We'll track down that wireless!

---

### Post by siroya on 2011-05-12
Sorry, in the meantime, Windows crashed. had to format HDD. Shall reload Ubuntu again. Hope it works this time. :)

---

### Post by chili555 on 2011-05-12
We'll be glad to help. Post as requested above and we'll proceed.

---

### Post by eipmoc on 2011-06-19
Hi, i have the same problem, good sound and everything works but no Wireless.

Her is my info.

lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
05:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
05:04.0 CardBus bridge [0607]: ENE Technology Inc CB1410 Cardbus Controller [1524:1410] (rev 01)
05:06.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:06.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:06.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:06.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)

Can you help me out

---

### Post by chili555 on 2011-06-19
Please post:```
dmesg | grep b43
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by eipmoc on 2011-06-20
it says this

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by chili555 on 2011-06-20
How about the first command?

---

### Post by eipmoc on 2011-06-20
nothing, it goes to the next line, no data er something

---

### Post by chili555 on 2011-06-20
Please do:```
sudo modprobe b43
dmesg | grep b43
```I'm a bit mystified.

---

### Post by eipmoc on 2011-06-20
again, first line nothing
second gives this


[  127.392160] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[  127.506547] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  127.625214] Registered led device: b43-phy0::tx
[  127.625243] Registered led device: b43-phy0::rx
[  127.625275] Registered led device: b43-phy0::radio
[  127.705464] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  127.705471] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  127.705474] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.



by the way i try this already
sudo apt-get install b43-fwcutter

it said newest already installed
(b43-fwcutter is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.)

---

### Post by chili555 on 2011-06-20
b43-fwcutter is designed to do just this:> download the correct firmware for this driver version.It either didn't perform or the firmware is not in the correct place. Let's see:```
ls -al /lib/firmware/b43
```If it produces no result or there is no b43 directory, let's try again. Hook up an ethernet connection and do:```
sudo apt-get install --reinstall firmware-b43-installer
```

---

### Post by superduperlinuxperson on 2011-06-20
if your firmware is not installed, than you must install it. look at this:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by eipmoc on 2011-06-21
> **chili555 said:**
> b43-fwcutter is designed to do just this:It either didn't perform or the firmware is not in the correct place. Let's see:```
ls -al /lib/firmware/b43
```If it produces no result or there is no b43 directory, let's try again. Hook up an ethernet connection and do:```
sudo apt-get install --reinstall firmware-b43-installer
```

ls: kan geen toegang krijgen tot /lib/firmware/b43: Bestand of map bestaat niet
 that what the first line said.

second started some installer and gives this

Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
De volgende NIEUWE pakketten zullen geïnstalleerd worden:
  firmware-b43-installer
0 pakketten opgewaardeerd, 1 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
Er moeten 3632 B aan archieven opgehaald worden.
Door deze operatie zal er 49,2 kB extra schijfruimte gebruikt worden.
Ophalen:1 [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) natty/multiverse firmware-b43-installer all 4.150.10.5-5 [3632 B]
3632 B opgehaald in 0s (62,3 kB/s)         
Selecteren van voorheen niet geselecteerd pakket firmware-b43-installer.
(Database inlezen ... 151336 files and directories currently installed.)
Uitpakken van firmware-b43-installer (uit .../firmware-b43-installer_4.150.10.5-5_all.deb) ...
Instellen van firmware-b43-installer (4.150.10.5-5) ...
--2011-06-21 08:11:09--  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)
Herleiden van mirror2.openwrt.org... 46.4.11.11
Verbinding maken met mirror2.openwrt.org|46.4.11.11|:80... verbonden.
HTTP-verzoek is verzonden; wachten op antwoord... 200 OK
Lengte: 3888794 (3,7M) [application/x-bzip2]
Wordt opgeslagen als: ‘broadcom-wl-4.150.10.5.tar.bz2’

100%[======================================>] 3.888.794   8,58M/s   in 0,4s    

2011-06-21 08:11:09 (8,58 MB/s) - '‘broadcom-wl-4.150.10.5.tar.bz2’' opgeslagen [3888794/3888794]

This file is recognised as:
  ID         :  FW13
  filename   :  wl_apsta_mimo.o
  version    :  410.2160
  MD5        :  cb8d70972b885b1f8883b943c0261a3c
Extracting b43/pcm5.fw
Extracting b43/ucode15.fw
Extracting b43/ucode14.fw
Extracting b43/ucode13.fw
Extracting b43/ucode11.fw
Extracting b43/ucode9.fw
Extracting b43/ucode5.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/lp0initvals15.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/lp0initvals14.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/lp0initvals13.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/n0initvals11.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/b0g0initvals5.fw


And now, it is correct?

---

### Post by eipmoc on 2011-06-21
Hi after you latest request i now get this
[ 2711.846297] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[ 2711.957628] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[ 2712.087613] Registered led device: b43-phy0::tx
[ 2712.087645] Registered led device: b43-phy0::rx
[ 2712.087677] Registered led device: b43-phy0::radio
[ 2712.504071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

But still no Wlan, i now going to reboot the computer


> **eipmoc said:**
> again, first line nothing
second gives this


[  127.392160] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[  127.506547] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[  127.625214] Registered led device: b43-phy0::tx
[  127.625243] Registered led device: b43-phy0::rx
[  127.625275] Registered led device: b43-phy0::radio
[  127.705464] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  127.705471] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  127.705474] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.



by the way i try this already
sudo apt-get install b43-fwcutter

it said newest already installed
(b43-fwcutter is reeds de nieuwste versie.
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.)

---

### Post by eipmoc on 2011-06-21
YESSSSSSSSSSSSSSSSSSSS


Thank you, i love this support

it works now, thank you 

Greeting from Holland
Eric

---

