---
title: "3G HSDPA USB Modem detected as CD Drive"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by kadal27 on 2010-08-29
I am trying a 3G HSDPA USB Modem inUbuntu 10.04.
It detects it as a CD Drive.

When I tried to 'Safely Remove Drive' 
                                  I got the following error:

 > Unable to stop drive
Error detaching: helper exited with exit code 1: Detaching device /dev/sr1
USB device: /sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directoryOutput of lsmod |egrep “usb|option” is as follows:

> usb_storage               39425   0
option                            15654   0
usbserial                     33019   1 optionOutput of 'lsusb'

> Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 011: ID 1c9e:6061  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubA few lines which I think related to this from the output of sudo lsusb -vvv

> Bus 004 Device 009: ID 1c9e:6061  
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1c9e 
  idProduct          0x6061 
  bcdDevice            0.00
  iManufacturer           1 3G USB Modem        ??
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          108
    bNumInterfaces          4
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xa0
      (Bus Powered)
      Remote Wakeup
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 3G Devices    
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0010  1x 16 bytes
        bInterval             128
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 3G Devices    
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              3 3G Devices    
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x86  EP 6 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        3
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk (Zip)
      iInterface              3 3G Devices    
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
Device Status:     0x0000
  (Bus Powered)A few lines which I think related to this from the output of 'dmesg'

> [  115.244017] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  115.405177] usb 4-2: configuration #1 chosen from 1 choice
[  115.457192] Initializing USB Mass Storage driver...
[  115.457416] scsi4 : SCSI emulation for USB Mass Storage devices
[  115.457961] usbcore: registered new interface driver usb-storage
[  115.457967] USB Mass Storage support registered.
[  115.459988] usb-storage: device found at 2
[  115.459992] usb-storage: waiting for device to settle before scanning
[  118.448053] usb 4-2: USB disconnect, address 2
[  121.912020] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  122.095176] usb 4-2: configuration #1 chosen from 1 choice
[  122.114623] scsi5 : SCSI emulation for USB Mass Storage devices
[  122.114894] usb-storage: device found at 3
[  122.114898] usb-storage: waiting for device to settle before scanning
[  127.113342] usb-storage: device scan complete
[  127.116330] scsi 5:0:0:0: CD-ROM            HSDPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[  127.149281] sr1: scsi-1 drive
[  127.149526] sr 5:0:0:0: Attached scsi CD-ROM sr1
[  127.149675] sr 5:0:0:0: Attached scsi generic sg2 type 5
[  699.032071] usb 4-2: USB disconnect, address 3
[  720.252019] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  720.413150] usb 4-2: configuration #1 chosen from 1 choice
[  720.416311] scsi6 : SCSI emulation for USB Mass Storage devices
[  720.416697] usb-storage: device found at 4
[  720.416701] usb-storage: waiting for device to settle before scanning
[  723.584059] usb 4-2: USB disconnect, address 4
[  726.856050] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  727.038278] usb 4-2: configuration #1 chosen from 1 choice
[  727.060289] scsi7 : SCSI emulation for USB Mass Storage devices
[  727.064528] usb-storage: device found at 5
[  727.064534] usb-storage: waiting for device to settle before scanning
[  732.065363] usb-storage: device scan complete
[  732.069352] scsi 7:0:0:0: CD-ROM            HSDPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[  732.100291] sr1: scsi-1 drive
[  732.100544] sr 7:0:0:0: Attached scsi CD-ROM sr1
[  732.101416] sr 7:0:0:0: Attached scsi generic sg2 type 5
[10674.088053] usb 4-2: USB disconnect, address 5
[10688.636032] usb 4-2: new full speed USB device using uhci_hcd and address 6
[10688.799190] usb 4-2: configuration #1 chosen from 1 choice
[10688.803191] scsi8 : SCSI emulation for USB Mass Storage devices
[10688.803369] usb-storage: device found at 6
[10688.803372] usb-storage: waiting for device to settle before scanning
[10691.944053] usb 4-2: USB disconnect, address 6
[10695.172069] usb 4-2: new full speed USB device using uhci_hcd and address 7
[10695.353464] usb 4-2: configuration #1 chosen from 1 choice
[10695.380713] scsi9 : SCSI emulation for USB Mass Storage devices
[10695.382879] usb-storage: device found at 7
[10695.382884] usb-storage: waiting for device to settle before scanning
[10700.381614] usb-storage: device scan complete
[10700.384595] scsi 9:0:0:0: CD-ROM            HSDPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[10700.413612] sr1: scsi-1 drive
[10700.413998] sr 9:0:0:0: Attached scsi CD-ROM sr1
[10700.416278] sr 9:0:0:0: Attached scsi generic sg2 type 5
[11508.856072] usb 4-2: USB disconnect, address 7
[11593.760023] usb 4-2: new full speed USB device using uhci_hcd and address 8
[11593.922195] usb 4-2: configuration #1 chosen from 1 choice
[11593.926664] scsi10 : SCSI emulation for USB Mass Storage devices
[11593.926954] usb-storage: device found at 8
[11593.926958] usb-storage: waiting for device to settle before scanning
[11597.144125] usb 4-2: USB disconnect, address 8
[11600.364017] usb 4-2: new full speed USB device using uhci_hcd and address 9
[11600.547181] usb 4-2: configuration #1 chosen from 1 choice
[11600.567654] scsi11 : SCSI emulation for USB Mass Storage devices
[11600.571125] usb-storage: device found at 9
[11600.571130] usb-storage: waiting for device to settle before scanning
[11605.570358] usb-storage: device scan complete
[11605.573312] scsi 11:0:0:0: CD-ROM            HSDPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[11605.603286] sr1: scsi-1 drive
[11605.603553] sr 11:0:0:0: Attached scsi CD-ROM sr1
[11605.603714] sr 11:0:0:0: Attached scsi generic sg2 type 5
[13917.680103] usb 4-2: USB disconnect, address 9
[14550.796019] usb 4-1: new full speed USB device using uhci_hcd and address 10
[14550.956163] usb 4-1: configuration #1 chosen from 1 choice
[14550.959306] scsi12 : SCSI emulation for USB Mass Storage devices
[14550.959579] usb-storage: device found at 10
[14550.959583] usb-storage: waiting for device to settle before scanning
[14554.048071] usb 4-1: USB disconnect, address 10
[14557.400035] usb 4-1: new full speed USB device using uhci_hcd and address 11
[14557.580766] usb 4-1: configuration #1 chosen from 1 choice
[14557.603656] scsi13 : SCSI emulation for USB Mass Storage devices
[14557.607081] usb-storage: device found at 11
[14557.607085] usb-storage: waiting for device to settle before scanning
[14562.605930] usb-storage: device scan complete
[14562.608911] scsi 13:0:0:0: CD-ROM            HSDPA    MMC Storage      2.31 PQ: 0 ANSI: 2
[14562.643914] sr1: scsi-1 drive
[14562.644251] sr 13:0:0:0: Attached scsi CD-ROM sr1
[14562.644412] sr 13:0:0:0: Attached scsi generic sg2 type 5Output of 'dmesg | grep -e "modem" -e "tty"'

> [    0.000000] console [tty0] enabled
[    0.287919] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.288456] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.945852] USB Serial support registered for GSM modem (1-port)
[   34.946121] option: v0.7.2:USB Driver for GSM modemsI searched, read and tried several guidances from several forums, blogs etc. Some of the outputs are mentioned above.  But still I can't detect and use my modem.

[CENTER] Please help me.
[/CENTER]
 
(Make of the modem not known)

---

### Post by halj32 on 2010-08-29
try installing usb-modeswitch + usb-modeswitch-data
then you should see the dongle in your network manager
then you just have to enter (if in UK)
go to edit connections, mobile broadband, new connection,
give your network a name ie; 3G
Number; *99#
APN: 3internet
done
enjoy

---

### Post by kadal27 on 2010-08-29
Hi halj32,
I've already tried but no use.
Network manager does not detect the modem.

For information, I'm from India.

---

### Post by alexfish on 2010-08-29
hi

just try eject device , see what happens

---

### Post by kadal27 on 2010-08-29
Hi alexfish,
I've already tried it also, but nothing happened

I used 
sudo eject sr1

It came back to prompt without any action or error message!
That CD Drive is also staying there!!

---

### Post by alexfish on 2010-08-29
hi

checking the messages shows the driver but there are no ports registering
so  it's shooting in the dark time.

have you tried
register the device in windows , if so , did it work
 
if worked in windows , try in windows again, does it work

if not registered in windows , try registering the device in windows

make sure the device works in windows then try in ubuntu 

once with the device plugged in at boot , see if it works

once after boot , see if it works

just leave any devices showing on the desktop

in both cases post the listing of these commands from the terminal

Code:

[COLOR=Blue]lsusb -t[/COLOR]

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/usb*[/COLOR]

if  it comes up with an error try

Find the Mass Storage of the  device pick only one of these to post

Code:
[COLOR=Blue]
ls -al  /dev/disk/by-id/usb*Mass_Storage*[/COLOR]

or

[COLOR=Blue]ls -al /dev/disk/by-id/usb*Storage*

[COLOR=Black]or

[/COLOR][/COLOR][COLOR=Blue]ls -al /dev/disk/by-id/usb*[/COLOR]

can also suggest to remove usb_modeswitch , but not totally remove

alexfish

---

### Post by kadal27 on 2010-08-29
Hi alexfish,
It worked and works fine in Windows (XP).
In Ubuntu I already tried both attaching before and after boot and there is no difference.

Output when attached after boot:
> arivukkadal@arivukkadal:~$ lsusb -t
4-2:1.0: No such file or directory
4-2:1.1: No such file or directory
4-2:1.2: No such file or directory
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 3, If 0, Class=vend., Driver=, 12M
    |__ Port 2: Dev 3, If 1, Class=vend., Driver=, 12M
    |__ Port 2: Dev 3, If 2, Class=vend., Driver=, 12M
    |__ Port 2: Dev 3, If 3, Class=stor., Driver=usb-storage, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
arivukkadal@arivukkadal:~$ ls -al /dev/serial/by-id/usb*
ls: cannot access /dev/serial/by-id/usb*: No such file or directory
arivukkadal@arivukkadal:~$ ls -al /dev/serial/by-id/usb0
ls: cannot access /dev/serial/by-id/usb0: No such file or directory
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*Mass_Storage*
ls: cannot access /dev/disk/by-id/usb*Mass_Storage*: No such file or directory
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*Storage*
lrwxrwxrwx 1 root root 9 2010-08-30 05:44 /dev/disk/by-id/usb-HSDPA_MMC_Storage-0:0 -> ../../sr1
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*
lrwxrwxrwx 1 root root 9 2010-08-30 05:44 /dev/disk/by-id/usb-HSDPA_MMC_Storage-0:0 -> ../../sr1Output when attached before boot:
> arivukkadal@arivukkadal:~$ lsusb -t
4-2:1.0: No such file or directory
4-2:1.1: No such file or directory
4-2:1.2: No such file or directory
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 2, If 0, Class=vend., Driver=, 12M
    |__ Port 2: Dev 2, If 1, Class=vend., Driver=, 12M
    |__ Port 2: Dev 2, If 2, Class=vend., Driver=, 12M
    |__ Port 2: Dev 2, If 3, Class=stor., Driver=usb-storage, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
arivukkadal@arivukkadal:~$ ls -al /dev/serial/by-id/usb*
ls: cannot access /dev/serial/by-id/usb*: No such file or directory
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*Mass_Storage*
ls: cannot access /dev/disk/by-id/usb*Mass_Storage*: No such file or directory
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*Storage*
lrwxrwxrwx 1 root root 9 2010-08-30 06:01 /dev/disk/by-id/usb-HSDPA_MMC_Storage-0:0 -> ../../sr1
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*
lrwxrwxrwx 1 root root 9 2010-08-30 06:01 /dev/disk/by-id/usb-HSDPA_MMC_Storage-0:0 -> ../../sr1Output after removing usb_modeswitch and re-attached:
> arivukkadal@arivukkadal:~$ lsusb -t
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
    |__ Port 2: Dev 3, If 0, Class=stor., Driver=usb-storage, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*
ls: cannot access /dev/disk/by-id/usb*: No such file or directory
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*Mass_Storage*
ls: cannot access /dev/disk/by-id/usb*Mass_Storage*: No such file or directory
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*
lrwxrwxrwx 1 root root 9 2010-08-30 06:12 /dev/disk/by-id/usb-HSDPA_MMC_Storage-0:0 -> ../../sr1
arivukkadal@arivukkadal:~$ ls -al /dev/disk/by-id/usb*Storage*
lrwxrwxrwx 1 root root 9 2010-08-30 06:12 /dev/disk/by-id/usb-HSDPA_MMC_Storage-0:0 -> ../../sr1Thanks.

---

### Post by JBAlaska on 2010-08-29
On my 3G USB modem, the flash drive part contained both windows and Linux drivers, to be manually installed by the user. Is this the case here?

---

### Post by alexfish on 2010-08-30
Hi Kadal

Can you install Sakis3g , this is a 3g manager, this may or may not work , but it as a logging
facility , also more in control of the modeswitching

How to install latest version in Ubuntu: . Possibly Sakis3g 0.2.0e . now includes usb_modeswitch " Version 1.1.3 (C) Josua Dietze 2010"

leave the existing usb_modeswitch uninstalled

From the terminal:
Codes:

[COLOR=Blue]sudo bash[/COLOR]

[COLOR=Blue]cd /usr/bin[/COLOR]

[COLOR=Blue]wget 'http://www.sakis3g.org/versions/latest/sakis3g.gz'
[/COLOR] 
[COLOR=Blue]echo "dda70fd95fb952dbb979af88790d3f6e sakis3g.gz" | md5sum -c[/COLOR]

You should see: sakis3g.gz: OK

Codes:

[COLOR=Blue]gunzip sakis3g.gz

chmod +x sakis3g[/COLOR] 


then run sakis3g from the terminal

Code:

[COLOR=Blue]sakis3g[/COLOR]


Have a look through the menus , and try the options from the menu , it won't harm your system

also could you post detail of

CODE:

[COLOR=Blue]uname -a[/COLOR]



regards

alexfish 

Ps

---

### Post by kadal27 on 2010-08-31
Hi alexfish,
It worked fine,
on both by desktop and netbook.
Thanks a lot.

Output (from my desktop) for uname -a 

> Linux arivukkadal 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux


Once again thank you so much!

---

### Post by kadal27 on 2010-09-10
The modem works fine
after following the instructions
in post [#9]("http://ubuntuforums.org/showpost.php?p=9783888&postcount=9").

Thanks a lot.

---

### Post by hemavanteru on 2012-05-10
I am using ubuntu 11.10. my modem is ZTE MF190A. It is detected as CD Drive and MMC storage device.

the following is the output. please help.


hemantha@bsnl:~$ lsusb -t
/:  Bus 05.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=uhci_hcd/2p, 12M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/8p, 480M
    |__ Port 2: Dev 2, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 2: Dev 2, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
    |__ Port 7: Dev 4, If 0, Class=vend., Driver=option, 480M
    |__ Port 7: Dev 4, If 1, Class=vend., Driver=option, 480M
    |__ Port 7: Dev 4, If 2, Class=vend., Driver=option, 480M
    |__ Port 7: Dev 4, If 3, Class=vend., Driver=option, 480M
    |__ Port 7: Dev 4, If 4, Class=stor., Driver=usb-storage, 480M
hemantha@bsnl:~$ ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2012-05-10 14:00 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_MF1900ZTED010000-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2012-05-10 14:00 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_MF1900ZTED010000-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2012-05-10 14:00 /dev/serial/by-id/usb-ZTE_Incorporated_ZTE_WCDMA_Technologies_MSM_MF1900ZTED010000-if02-port0 -> ../../ttyUSB2

---

