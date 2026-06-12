---
title: "Tata Photon Whiz - 64bit - Errors &amp; Issues"
date: 2010-09-30
forum: Networking &amp; Wireless
---

### Post by randolf_ambrose on 2010-09-30
Hi, i have a Tata Photon Whiz USB device with me. I'm not able to set it up in my Lucid Lynx. Here are the things i know and the issues.

1. Device is not HUAWEI Modem like i saw in the queries from other posts. Instead mine is Haier MMC Storage.
2. When i connect the device, sometimes it is mounted as CD Drive in /dev/sr1 and the mounted device has the label Tata Photon Whiz.
3. Sometimes when i connect, the green light on the devices goes on for 3-5 seconds and then goes off.
4. I tried lspci - nothing about the device was shown
5. I tried lsusb - nothing about the device was shown
6. From the info i got from an article i edited wvdial.conf and set the phone number as #777 and uname & pword as internet. - no use
7. I edited /etc/usb/modeswitch.d/12d1:1446 and added 140b to devices list. - no use
8. after steps 6 & 7, when i tried sudo wvdial i got this
> --> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
ATQ0
OK
--> Re-Sending: ATZ
ATZ
OK
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

I have installed modeswitch and have a Reliance Netconnect working perfectly.

wvdial
> --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy
--> Cannot open /dev/ttyUSB0: Device or resource busy

usb-devices
> T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:04.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-22-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=19d2 ProdID=fffe Rev=00.00
S:  Manufacturer=ZTE, Incorporated
S:  Product=ZTE CDMA Tech
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option

T:  Bus=03 Lev=01 Prnt=01 Port=04 Cnt=02 Dev#= 10 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=201e ProdID=1008 Rev=00.00
S:  Manufacturer=Haier MOBILE LTD 
S:  Product=USB MMC Storage
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-22-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:04.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

What are the possibilities of getting this device working.
Is any more data required to resolve this issue.

please someone help.

---

### Post by randolf_ambrose on 2010-09-30
Anyone successfully installed a HAIER model Tata Photon Whiz and got it working???

please help...

---

### Post by alexfish on 2010-09-30
hi

from your listing you have two devices list

The zte looks fine at firts glance , yet of note , may have been incorrectly switched
note the EPs=3 which usually indicates the modem part of the device , then look at all the drivers,
they all show the option drivers on each part of the device,normally there is a driver which would indicate the mass
storage part of the device , other managers may have difficulty finding the correct
port if they rely on plugins (although could be proved wrong)

your device
S: Manufacturer=ZTE, Incorporated
S: Product=ZTE CDMA Tech
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I: If#= 0 Alt= 0 #EPs= 3  Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 1 Alt= 0 #EPs= 2  Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 2 Alt= 0 #EPs= 2  Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 3 Alt= 0 #EPs= 2  Cls=ff(vend.) Sub=ff Prot=ff Driver=option

usual zte device
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE CDMA Technologies MSM
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option <-- normaly usb0
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option <-- normaly usb1
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage <-- as it says
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option <-- normaly usb2

The other device there is no usb_modeswitch listing (un-switched state) so perhaps the usb modeswitch forum
would be the place to look for advice ( what happens if you eject the device or safely remove )

Also what happens if the usb modeswitch is disabled

regards

alexfish

---

### Post by randolf_ambrose on 2010-10-01
> **alexfish said:**
> hi

from your listing you have two devices list

The zte looks fine at firts glance , yet of note , may have been incorrectly switched
note the EPs=3 which usually indicates the modem part of the device , then look at all the drivers,
they all show the option drivers on each part of the device,normally there is a driver which would indicate the mass
storage part of the device , other managers may have difficulty finding the correct
port if they rely on plugins (although could be proved wrong)

your device
S: Manufacturer=ZTE, Incorporated
S: Product=ZTE CDMA Tech
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=100mA
I: If#= 0 Alt= 0 #EPs= 3  Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 1 Alt= 0 #EPs= 2  Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 2 Alt= 0 #EPs= 2  Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 3 Alt= 0 #EPs= 2  Cls=ff(vend.) Sub=ff Prot=ff Driver=option

usual zte device
S:  Manufacturer=ZTE,Incorporated
S:  Product=ZTE CDMA Technologies MSM
S:  SerialNumber=1234567890ABCDEF
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option <-- normaly usb0
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option <-- normaly usb1
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage <-- as it says
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option <-- normaly usb2

The other device there is no usb_modeswitch listing (un-switched state) so perhaps the usb modeswitch forum
would be the place to look for advice ( what happens if you eject the device or safely remove )

Also what happens if the usb modeswitch is disabled

regards

alexfish

thanks for the info... lemme try the usb-modeswitch forum and i'll get back with my results...

---

### Post by randolf_ambrose on 2010-10-08
My Issues Still Remain!!!

I couldn't find any info to resolve my problems...

let me give more info... 

USB-DEVICES
> 
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 5
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:04.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-22-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=201e ProdID=1008 Rev=00.00
S:  Manufacturer=Haier MOBILE LTD 
S:  Product=USB MMC Storage
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 5
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-22-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:04.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


/etc/wvdial 

> [Dialer Defaults]
Modem = /dev/sr1
Baud = 230400
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2
Init3 = AT+CRM=1
Stupid Mode = 1
Modem Type = USB Modem
Phone = #777
ISDN = 0
Username = internet
Password = internet 

lspci
> 00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


lsusb
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 201e:1008  
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


sudo wvdial
> --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory
--> Cannot open /dev/ttyUSB0: No such file or directory

So i tried changing /dev/ttyUSB0 to /dev/sr1
> --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/sr1: Invalid argument
--> Cannot open /dev/sr1: Invalid argument
--> Cannot open /dev/sr1: Invalid argument

Changed it to /dev/ttyUSB2 since
> T:  Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=201e ProdID=1008 Rev=00.00
S:  Manufacturer=Haier MOBILE LTD 
S:  Product=USB MMC Storage
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage showed that Dev#=2
sudo wvdial
> --> WvDial: Internet dialer version 1.60
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory

So what shall i do next... i'm not able to interpret any of the results i've shown here... i need help...

---

### Post by alexfish on 2010-10-08
Hi Randolf

previous other posts you had a ZTE device + Haier MOBILE

Now we only have the Haier MOBILE to deal with on above post

you will not be able to connect with this device until you get a reading similar to the ZTE device

looking throw the info the device is in an un-switched state (Driver = usb-storage)
and the initial state of ID's are Vendor=201e ProdID=1008  see below  

T: Bus=03 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 2 Spd=12 MxCh= 0
D: Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs= 1
P: Vendor=201e ProdID=1008 Rev=00.00
S: Manufacturer=Haier MOBILE LTD
S: Product=USB MMC Storage
C: #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I: If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

if a device appears on the desktop try "rightclick device" and select eject , (best connect device after boot)
see if the device ID's change

looking through the usb_modswitch data the does not appear to be a listing for the device
so also advise looking up the modeswitch forum and submit details of the above ,see if they can help 

Does the ZTE device work 

alexfish

---

### Post by randolf_ambrose on 2010-10-09
@alexfish

the ZTE device is working perfectly... no issues... all i had to do was install modeswitch and congigure the device in network manager...

in my initial post, i had ZTE device connected...

i posted second time to make sure that i dont give any wrong data here...

Let me check with your info and get back!!!

---

