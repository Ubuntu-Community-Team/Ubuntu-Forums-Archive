---
title: "Help!!!"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by piedog98 on 2011-06-30
I am trying to get an internet connection on my newly-installed ubuntu computer. 

i have tried <sudo apt-get install b43-fwcutter>.
it responded <E: Unable to locate package b43-fwcutter>.

i then tried a <dmesg | grep -i firm>.
the it spat back at me.
[  0.161805][Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[  0.245165] pci 0000:05:08.0: Firmware left e100 interrupts enabled; disabling
[  17.328521] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[  18.302783] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  18.302790] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[  18.302794] b43-phy0 ERROR: You must go to [http://wireless.kern](http://wireless.kern)
el.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

i read the instructions, but no downloads. i'm an ubuntu noob, so i need help. and fast, too; caus if i don't set up my friends computer by sunday i dont get $50. i would appreciate help.
:confused::confused::confused:

---

### Post by nm_geo on 2011-06-30
Are you connect to ethernet cable?  Did you have Synaptic open when you tried the sudo apt-get cpommand in terminal?

---

### Post by piedog98 on 2011-06-30
1. no
2. what the **** is synaptic? i told you i was a major noob.

---

### Post by nm_geo on 2011-06-30
No problem .. but we need the computer hooked up to the ethernet before you try to install firmware.

in terminal 

```
lspci -nn
```

Just to make sure what chipset we are dealing with.

---

### Post by piedog98 on 2011-06-30
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
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
02:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
05:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
05:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
05:05.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
05:05.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
05:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 02)

---

### Post by piedog98 on 2011-06-30
its 9:12 EST so i would like help as soon as i can get it

---

### Post by nm_geo on 2011-06-30
Ok you need the firmware-b43-installer.

Hook that baby up to an ethernet cable..

```
sudo apt-get update
``````
sudo apt-get install firmware-b43-installer
```

---

### Post by piedog98 on 2011-06-30
dont got an ethernet, but if you can give me a url to go to so i can move a file over via usb that would be great.

---

### Post by nm_geo on 2011-06-30
> **piedog98 said:**
> dont got an ethernet, but if you can give me a url to go to so i can move a file over via usb that would be great.

instruction here under installing b43 without internet.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by dFlyer on 2011-06-30
Here is a link for 10.10 don't know what version your using.

[http://pkgs.org/ubuntu-10.10/ubuntu-multiverse-i386/firmware-b43-installer_4.150.10.5-4_all.deb.html](http://pkgs.org/ubuntu-10.10/ubuntu-multiverse-i386/firmware-b43-installer_4.150.10.5-4_all.deb.html)

---

### Post by piedog98 on 2011-06-30
11.04

---

### Post by nm_geo on 2011-06-30
> **piedog98 said:**
> 11.04

The one I gave you is for 11.04.  It would be simplier to carry the laptop to an ethernet cable but go with it the way you want.

---

### Post by nm_geo on 2011-06-30
Question?  How is the computer you are using connected right now.

---

### Post by piedog98 on 2011-07-01
wait i have a time window to use an ethernet cable. give me instructions to the point that i can run wireless.

---

### Post by piedog98 on 2011-07-01
I followed the STA and B43 Internet Access steps, and connected directly next to the router. i am about 25 metres (30 yards) from the router. whats wrong?

---

### Post by nm_geo on 2011-07-01
> **piedog98 said:**
> I followed the STA and B43 Internet Access steps, and connected directly next to the router. i am about 25 metres (30 yards) from the router. whats wrong?
  Read the answer to you private message piedog and if we keep our discussion here others might be helped.
 
Remove the STA driver.. Install b43-fwcutter and firmware-b43-installer.. We will address blacklist problems if you respond. I have to go for now.

---

### Post by piedog98 on 2011-07-01
This really helped. nm_geo is a user who can really help.

he sent me this message 'bout blacklists.


     You do not need both drivers I would recommend you remove      the STA driver. Keep the b43 and install the firmware-b43-installer. JUst go to Synaptic and make sure you only have b43-fwcutter and the above firmware. remove the others.. 

I will send more information about how the STA blacklisted the b43 & ssb module later. You can look under /etc/modprobe.d/ (files) review them all if you see blacklist b43 or blacklist ssb we need to fix them. 

You can do this gksudo gedit /etc/modprobe.d/* That opens the directory of modprobe.d with root priviledges then if you see blacklist b43 just put a # in fornt of the statement like this example (# blacklist b43) & (# blacklist ssb) then save the file... and exit 

That danged STA driver creates some major problems and generally doesn't work on most computers.. 

I use B43-fwcutter and firmware-b43-installer and I have 4 version or more on my laptop starting with Lucid 10.04, Maverick 10.10, Natty 11.04 and testing Oneiric 11.10 and they all run b43 with the Broadcomb4311 chipset.

Let me know in the forum how it goes I will be looking tonight.

---

### Post by nm_geo on 2011-07-01
So did you get it working??.. We need the $50 ..
If so please mark the thread Solved.. Next to title

---

