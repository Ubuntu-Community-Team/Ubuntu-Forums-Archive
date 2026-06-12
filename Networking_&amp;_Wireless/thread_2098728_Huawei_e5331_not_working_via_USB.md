---
title: "Huawei e5331 not working via USB"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by TADsince1995 on 2012-12-27
Hello all,

I purchased a Huawei e5331 device, I can use it via wifi, but not via usb. First of all sometimes the system cannot manage to recognize as usb modem, sometimes yes (usb_modeswitch installed). If I reboot the device while connected it's recognized.

When I can get it recognized this is the lsusb output:

```
Bus 001 Device 005: ID 12d1:1506 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
```

this is dmesg output:

```
[  161.500025] usb 1-4: >new high-speed USB device number 5 using ehci_hcd
[  161.632951] usb 1-4: >New USB device found, idVendor=12d1, idProduct=1506
[  161.632956] usb 1-4: >New USB device strings: Mfr=2, Product=1, SerialNumber=0
[  161.632959] usb 1-4: >Product: HUAWEI Mobile
[  161.632961] usb 1-4: >Manufacturer: HUAWEI
[  161.634881] option 1-4:1.0: >GSM modem (1-port) converter detected
[  161.634981] usb 1-4: >GSM modem (1-port) converter now attached to ttyUSB0
[  161.635094] option 1-4:1.2: >GSM modem (1-port) converter detected
[  161.635159] usb 1-4: >GSM modem (1-port) converter now attached to ttyUSB1

```

and I can see ttyUSB0 and ttyUSB1 under /dev. Network manager recognizes there is a mobile broadband option, correctly reading my provider name, but after having it configured it cannot connect.

So, I tried with wvdial, this is the result:

```
--> WvDial: Internet dialer version 1.61
--> Initializing modem.
--> Sending: ATZ
--> Sending: ATQ0
--> Re-Sending: ATZ
--> Modem not responding.
```

I tried both with ttyUSB0 and ttyUSB1. I tried on Ubuntu 12.10 x86_64 and Linuxmint 14 with the same result.

It's a really strange problem, it seems that the modem is recognized but doesn't work. I didn't find nothing on the internet about Huawei e5331 and linux.

Some hints?

Thank you in advance.

[EDIT]

Ok, I solved with this:

[http://www.huaweidevice.com/worldwide/downloadCenter.do?method=toDownloadFile&flay=software&softid=NDcwMzU=](http://www.huaweidevice.com/worldwide/downloadCenter.do?method=toDownloadFile&flay=software&softid=NDcwMzU=)

after you install, it doesn't do a normal modem connection, but some sort of tethering with the device that adds a wired network connection.

Hope this helps someone with the same problem. Thank you anyway! :)

---

### Post by bmork on 2013-01-04
> **TADsince1995 said:**
> 
Ok, I solved with this:

[http://www.huaweidevice.com/worldwide/downloadCenter.do?method=toDownloadFile&flay=software&softid=NDcwMzU=](http://www.huaweidevice.com/worldwide/downloadCenter.do?method=toDownloadFile&flay=software&softid=NDcwMzU=)

after you install, it doesn't do a normal modem connection, but some sort of tethering with the device that adds a wired network connection.


Good to hear that you managed to get it working with that driver.  But I wonder if we cannot make this device work by default using existing mainline drivers.  Could you post the output of "lsusb -vd 12d1:1506" (and any other device IDs the device might appear as if it does any mode switching)?


Bjørn

---

### Post by jwm4096 on 2013-01-12
Hello. Here is a copy of the "sudo lsusb -v" output.

```

Bus 002 Device 008: ID 12d1:1c1f Huawei Technologies Co., Ltd. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x12d1 Huawei Technologies Co., Ltd.
  idProduct          0x1c1f 
  bcdDevice            1.02
  iManufacturer           2 HUAWEI
  iProduct                1 HUAWEI Mobile
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          149
    bNumInterfaces          3
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         2 Communications
      bInterfaceSubClass      2 Abstract (modem)
      bInterfaceProtocol    255 Vendor Specific (MSFT RNDIS?)
      iInterface              0 
      CDC Header:
        bcdCDC               1.10
      CDC ACM:
        bmCapabilities       0x00
      CDC Call Management:
        bmCapabilities       0x00
        bDataInterface          0
      CDC Union:
        bMasterInterface        0
        bSlaveInterface         0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass     13 
      bInterfaceProtocol      0 
      iInterface              0 
      CDC Header:
        bcdCDC               1.10
      UNRECOGNIZED CDC:  06 24 1a 00 01 1f
      CDC Ethernet:
        iMacAddress                      3 582C80139263
        bmEthernetStatistics    0x00000005
        wMaxSegmentSize               1514
        wNumberMCFilters            0x0003
        bNumberPowerFilters              1
      CDC Union:
        bMasterInterface        2
        bSlaveInterface         2 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       1
      bNumEndpoints           3
      bInterfaceClass         2 Communications
      bInterfaceSubClass     13 
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval              32
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)

```I haven't tried the driver linked by TADSince1995 above yet.

This E5331 thing seems to work like a regular wireless router, with the wireless access point side bridged with an "Ethernet over USB" device.

Under Windows: 

The Huawei drivers set this up as some kind of Ethernet over USB device. You get a DHCP address in the same subnet as the wireless clients, and the E5331 forwards packets between the USB and Wireless like they are on the same network segment. Handy.

MAC address of the client USB-Ethernet device == iMacAddress below.
"arp" shows the USB MAC address of the router == routers wireless MAC (same as the MAC address given in the web UI).

```

      UNRECOGNIZED CDC:  06 24 1a 00 01 1f
      CDC Ethernet:
        iMacAddress                      3 582C80139263

```

---

### Post by jwm4096 on 2013-01-12
Here is the dmesg output I am getting when I plug this in. Running Ubuntu 12.04, kernel 3.2.0-35-generic x86_64.

```

[34478.604524] usb 2-6: new high-speed USB device number 21 using ehci_hcd
[34478.741154] scsi20 : usb-storage 2-6:1.0
[34479.739994] scsi 20:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[34479.742827] sr0: scsi-1 drive
[34479.743092] sr 20:0:0:0: Attached scsi CD-ROM sr0
[34479.743350] sr 20:0:0:0: Attached scsi generic sg4 type 5
[34480.072873] usb 2-6: USB disconnect, device number 21
[34482.398035] usb 2-6: new high-speed USB device number 22 using ehci_hcd
[34482.538485] usb 2-6: bad CDC descriptors
[34482.538701] usb 2-6: bad CDC descriptors
[34482.539141] scsi21 : usb-storage 2-6:1.1
[34482.539320] usb 2-6: bind() failure
[34483.537264] scsi 21:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[34483.540029] sr0: scsi-1 drive
[34483.540324] sr 21:0:0:0: Attached scsi CD-ROM sr0
[34483.540459] sr 21:0:0:0: Attached scsi generic sg4 type 5

```

---

### Post by bmork on 2013-01-14
> **jwm4096 said:**
> Hello. Here is a copy of the "sudo lsusb -v" output.

```

    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         2 Communications
      bInterfaceSubClass     13 
      bInterfaceProtocol      0 
      iInterface              0 
      CDC Header:
        bcdCDC               1.10
      UNRECOGNIZED CDC:  06 24 1a 00 01 1f
      CDC Ethernet:
        iMacAddress                      3 582C80139263
        bmEthernetStatistics    0x00000005
        wMaxSegmentSize               1514
        wNumberMCFilters            0x0003
        bNumberPowerFilters              1
      CDC Union:
        bMasterInterface        2
        bSlaveInterface         2 

```

That's fascinating.  This looks like a proper CDC NCM configuration, except for the combined master and slave interface (which probably is why you get the "[FONT=monospace]bad CDC descriptors" messages)[/FONT] .  But I believe this should work just fine with a very recent update to cdc_ncm, available in 3.7 and in the latest 3.6.y stable kernels. It makes cdc_ncm accept such combined interfaces as long as there is a proper CDC Union descriptor like here.

I assume this device runs its own dhcp and web server for configuration?  It might expose other management interfaces as well.  Is interface #0 a serial interface or is it really RNDIS as suggested by lsusb?


> 
I haven't tried the driver linked by TADSince1995 above yet.

This E5331 thing seems to work like a regular wireless router, with the wireless access point side bridged with an "Ethernet over USB" device.

Under Windows: 

The Huawei drivers set this up as some kind of Ethernet over USB device. You get a DHCP address in the same subnet as the wireless clients, and the E5331 forwards packets between the USB and Wireless like they are on the same network segment. Handy.

MAC address of the client USB-Ethernet device == iMacAddress below.
"arp" shows the USB MAC address of the router == routers wireless MAC (same as the MAC address given in the web UI).

```

      UNRECOGNIZED CDC:  06 24 1a 00 01 1f
      CDC Ethernet:
        iMacAddress                      3 582C80139263

```
Yes, that's where we pick up the MAC address.  And the UNRECOGNIZED CDC descriptor is a NCM functional descriptor, which wasn't recongnized and decoded by lsusb until very recenly (in git only).  See [https://github.com/gregkh/usbutils](https://github.com/gregkh/usbutils) for a lsusb version supporting this descriptor.


Bjørn

---

### Post by DerHut on 2013-04-17
> **TADsince1995 said:**
> 
Hope this helps someone with the same problem. Thank you anyway! :)

Yes, it helps. **Thank you** for this driver hint. :) 

I'm using Ubuntu 12.04 LTS [GERMAN Version] on my netbook.
At the end of the driver installation was a mistake. --- look at the Installation log
Nevertheless, it works fine!  --- I love my E5331 
After installation, I had to make some adjustments in the network settings. (eth1, mac-address, auto-dhcp, ...) 


Installation log:
```
derhut:~/Desktop$ cd driver/
derhut:~/Desktop/driver$ pwd
/home/derhut/Desktop/driver
derhut:~/Desktop/driver$ sudo ./install /home/derhut/Desktop
[sudo] password for derhut: 
DRIVER COPY START
STA_PATH_FLAG=.
STA_PATH_FULL=/home/derhut/Desktop/driver/install
START_PATH_DRIVER=/home/derhut/Desktop/driver
CURRENT install from ./install
INSTALL_PATH=/home/derhut/Desktop
DRIVER COPY END
have usb_modeswitch rules to HUAWEI DataCard: COUNT=2
RULESFILE =/lib/udev/rules.d/40-usb_modeswitch.rules~
COUNT_START=2
COUNT_END=1
RULESFILE =/lib/udev/rules.d/40-usb_modeswitch.rules
COUNT_START=1
COUNT_END=0
2
ttyUSB%n COUNT=2
1-2:1.2 unbind and bind option
COUNT_END=1
1-2:1.0 unbind and bind option
COUNT_END=0
ERROR: Removing 'cdc_ether': No such file or directory
ERROR: Removing 'usbnet': No such file or directory
ERROR: Removing 'hw_cdc_driver': No such file or directory
make -C src/ clean
make[1]: Betrete Verzeichnis '/home/derhut/Desktop/driver/ndis_driver/ndis_src/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
/home/derhut/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "clean" "/lib/modules/3.2.0-40-generic/build/include/linux/usb"
rmmod -f hw_cdc_driver
ERROR: Removing 'hw_cdc_driver': No such file or directory
make[1]: *** [clean] Fehler 1
make[1]: Verlasse Verzeichnis '/home/derhut/Desktop/driver/ndis_driver/ndis_src/src'
make: *** [clean] Fehler 2
make -C src/ modules
make[1]: Betrete Verzeichnis '/home/derhut/Desktop/driver/ndis_driver/ndis_src/src'
#/home/derhut/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "modules" "/lib/modules/3.2.0-40-generic/build/include/linux/usb"
make -C /lib/modules/3.2.0-40-generic/build SUBDIRS=/home/derhut/Desktop/driver/ndis_driver/ndis_src/src modules
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-3.2.0-40-generic'
  CC [M]  /home/derhut/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/derhut/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.mod.o
  LD [M]  /home/derhut/Desktop/driver/ndis_driver/ndis_src/src/hw_cdc_driver.ko
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-3.2.0-40-generic'
strip --strip-debug hw_cdc_driver.o
make[1]: Verlasse Verzeichnis '/home/derhut/Desktop/driver/ndis_driver/ndis_src/src'
make -C src/ install
make[1]: Betrete Verzeichnis '/home/derhut/Desktop/driver/ndis_driver/ndis_src/src'
#install -m 744 -c hw_cdc_driver.o /lib/modules/3.2.0-40-generic/kernel/drivers/usb/net
#depmod -a
#modprobe hw_cdc_driver
/home/derhut/Desktop/driver/ndis_driver/ndis_src/src/add_header.sh  "install"
modprobe hw_cdc_driver
make[1]: Verlasse Verzeichnis '/home/derhut/Desktop/driver/ndis_driver/ndis_src/src'

The Linux NDIS driver is installed successfully.
USBSERIAL_TARGET_PATH = 
ACM_TARGET_PATH = 
AUTORUNPATH=/home/derhut/.wine/drive_c/users/derhut/Startmenü/Programme/Autostart
AUTORUNPATH=/home/derhut/.wine/drive_c/users/Public/Startmenü/Programme/Autostart
ADDRUNLEVEL=/etc/rc2.d
»/etc/rc2.d/S99runhwactivator“ -> »/etc/init.d/runhwactivator“
»/etc/rc2.d/K10runhwactivator“ -> »/etc/init.d/runhwactivator“
ADDRUNLEVEL=/etc/rc4.d
»/etc/rc4.d/S99runhwactivator“ -> »/etc/init.d/runhwactivator“
»/etc/rc4.d/K10runhwactivator“ -> »/etc/init.d/runhwactivator“
ADDRUNLEVEL=/etc/rc3.d
»/etc/rc3.d/S99runhwactivator“ -> »/etc/init.d/runhwactivator“
»/etc/rc3.d/K10runhwactivator“ -> »/etc/init.d/runhwactivator“
ADDRUNLEVEL=/etc/rc5.d
»/etc/rc5.d/S99runhwactivator“ -> »/etc/init.d/runhwactivator“
»/etc/rc5.d/K10runhwactivator“ -> »/etc/init.d/runhwactivator“
./install: Zeile 309: chkconfig: Kommando nicht gefunden.
qmi_wwan interface not exist,ok
derhut:~/Desktop/driver$ 
```

---

