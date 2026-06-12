---
title: "[ASK]How to add my usb modem to network manager?"
date: 2011-05-04
forum: Networking &amp; Wireless
---

### Post by allmine on 2011-05-04
Hi, i'm new user of ubuntu, and i have installed ubuntu 10.10 to my laptop.
I have some CDMA USB modem, it's work perfectly using wvdial, but why my modem 
not detected by network manager. I want using gwibber and empathy IM, and i read that's apps using network manager (ex:if i connect using wvdial, i can't update status using gwibber). How to make network manager recognize my USB modem?

Thanks for advise, have a nice day. :)

PS: 
```
 $lsusb
Bus 003 Device 004: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device

$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

```

---

### Post by alexfish on 2011-05-04
need to see if NM can see the device can post results of 
```
nm-tool
```if the device is recognized the the same details of wvdial (dial command , user name and password) should work

also can try creating a dummy interface,not sure if this will work if using wvdial
```
sudu su
```the
```
printf "\niface eth111 inet dhcp\n" >> /etc/network/interfaces
```may need to check if dummy interface remains after fresh boot
```
cat /etc/network/interfaces
```

---

### Post by allmine on 2011-05-04
hi alex, thx for reply

```
~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E0:CB:4E:A3:33:27

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        1C:4B:D6:7B:EE:43

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

```
# cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth111 inet dhcp


```

---

### Post by alexfish on 2011-05-04
Hi

it don,t see it

can post details wvdial.conf

also need some system info, post results of

```
lsusb
```
```
ls -al /dev/serial/by-id
```
```
usb-devices
```also need to redo the dummy interface

```
sudo gedit /etc/network/interfaces
```delete the [FONT=monospace]"[/FONT]iface eth111 inet dhcp"
then **first** run wvdial for the connection.**when connected**, enter the dummy interface
```
sudo su
```[FONT=monospace]
[/FONT]```
printf "\niface eth111 inet dhcp\n" >> /etc/network/interfaces
```then test gwibber and empathy IM. as said not sure if this is going to work

---

### Post by allmine on 2011-05-04
hi alex, 
this is wvdial.conf
```
[Dialer Default]
Modem = /dev/ttyUSB0
Baud = 230400
Modem Name = CDMA
Modem Type = USB Modem
Phone = #777
Username = xxx
Password = xxx
Stupid Mode = 1
FlowControl = Hardware (CRTSCTS)
``````
$ lsusb
Bus 004 Device 002: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
Bus 003 Device 002: ID 046d:c058 Logitech, Inc. M115 Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
~$ ls -al /dev/serial/by-id
total 0
drwxr-xr-x 2 root root 60 2011-05-04 17:40 .
drwxr-xr-x 4 root root 80 2011-05-04 17:40 ..
lrwxrwxrwx 1 root root 13 2011-05-04 17:40 usb-Silicon_Labs_CP2102_USB_to_UART_Bridge_Controller_0001-if00-port0 -> ../../ttyUSB0
``````
~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh=11
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:04.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=04f2 ProdID=b071 Rev=15.15
S:  Manufacturer=Chicony Electronics Co., Ltd.
S:  Product=CNF7129
S:  SerialNumber=SN0001
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 1
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:06.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh=11
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:04.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c058 Rev=54.00
S:  Manufacturer=Logitech
S:  Product=USB Optical Mouse
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=98mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid

T:  Bus=03 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=10c4 ProdID=ea60 Rev=01.00
S:  Manufacturer=Silicon Labs
S:  Product=CP2102 USB to UART Bridge Controller
S:  SerialNumber=0001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=cp210x

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 1
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:06.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0b05 ProdID=1788 Rev=04.49
S:  Manufacturer=Broadcom Corp
S:  Product=BT-270
S:  SerialNumber=1C4BD604030B
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)
```actually, i need to see signal strength too. so it's not only about IM. But, i'll try that's too.
Thanks :)

update:IM still not work :(

---

### Post by alexfish on 2011-05-04
hi

have look up the driver as regards this device
[http://www.etheus.net/CP210x_Linux_Driver](http://www.etheus.net/CP210x_Linux_Driver)
interesting reading.

Looks Network Manager does not have a specific plug-in  for this device(may understand from reading the info in the link) , hence modem-manager will not find it, let alone communicate with it

From where I sit don't think can help much as regards getting other apps to work, esp when they rely on Network Manager. ( maybe there is someone that does )

Can be happy in as much , the device connects through wvdial ,

as regards getting it to work with other apps which depend on NM , try obtaining a cdma device compatible with Network Manager 

If I find further info , will  update post

alexfish

---

### Post by allmine on 2011-05-04
so that's mean this modem currently not supported by network manager :(
my poor modem..
anyway thanks a lot for u help alex :)

---

### Post by alexfish on 2011-05-04
hi

nearly forgot . Signal strength , can try adding this line to the wvdial.conf

```
Init1 = AT+CSQ
```

see what happens


alexfish

---

### Post by allmine on 2011-05-04
> **alexfish said:**
> hi

nearly forgot . Signal strength , can try adding this line to the wvdial.conf

```
Init1 = AT+CSQ
```see what happens


alexfish

i trying add that line in last wvdial.conf and this happen,
```
~$ sudo wvdial 
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CSQ
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CSQ
ERROR
--> Bad init string.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CSQ
ERROR
--> Bad init string.
```

so i removed again that line config.

---

