---
title: "ZTE USB modem with wvdial drops out, won't always auto reconnect"
date: 2013-08-15
forum: Networking &amp; Wireless
---

### Post by dazz100 on 2013-08-15
Hi
I have a ZTE usb modem connected to what will be a remote webcam server.
The modem is used to send webcam images to a web server.  The public are then able to access the images.
It is very important that the modem keeps working.  Dropout and recovery is OK, but the server will be located along way from home so it needs to reconnect after any dropout.

I use wvdial to control the modem.  That all works OK.

The problem I have is that about once a day, the modem drops out.  This is OK because I have the auto-reconnect option set in the wvdial.config file.  That feature works and it reconnects within a few seconds.

As a backup, I have a root cron job that runs wvdial once per hour.  If wvdial is running, nothing happens.  If wvdial is not running then it should run it and reconnect.

Occasionally, the connection drops and won't reconnect.  A can't figure out how to get it to reconnect.
The only option I can come up with is to reboot the webcam server.  I'd rather not do that.

Can anyone tell me how to reset and reconnect a ZTE modem?

Diagnostics output is below.
At present, the webcam server is still disconnected from the wireless network.  I can get some more info if that would be useful.
I have tried to provide a lot of info below.

When I run wvdial from the command line I get the following:
```

darren@alpha:/etc$ sudo wvdial
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory
--> Cannot open /dev/ttyUSB2: No such file or directory

```

When I look at the /dev directory, I can see ttyUSB[0,1,3] but not ttyUSB2.
So for some reason, the modem is no longer linked to ttyUSB2.  



Below are log extracts, conf files, diagnostics commands etc.
These were all run while the modem was running but dropped-out.
The blue LED on the modem was constant (on but not connected).

Below are the logged cron jobs to run wvdial.
```
darren@alpha:/var/log$ zcat syslog.7.gz | grep wvdial
Aug  7 07:00:01 alpha CRON[16690]: (root) CMD (wvdial)
Aug  7 08:00:01 alpha CRON[16900]: (root) CMD (wvdial)
Aug  7 09:00:01 alpha CRON[17112]: (root) CMD (wvdial)
Aug  7 10:00:01 alpha CRON[17322]: (root) CMD (wvdial)
Aug  7 11:00:01 alpha CRON[17529]: (root) CMD (wvdial)
Aug  7 12:00:01 alpha CRON[17739]: (root) CMD (wvdial)
Aug  7 13:00:01 alpha CRON[17949]: (root) CMD (wvdial)
Aug  7 14:00:01 alpha CRON[18160]: (root) CMD (wvdial)
Aug  7 15:00:01 alpha CRON[18371]: (root) CMD (wvdial)
Aug  7 16:00:01 alpha CRON[18579]: (root) CMD (wvdial)
Aug  7 17:00:01 alpha CRON[18791]: (root) CMD (wvdial)
Aug  7 18:00:01 alpha CRON[19001]: (root) CMD (wvdial)
Aug  7 19:00:01 alpha CRON[19135]: (root) CMD (wvdial)
Aug  7 20:00:01 alpha CRON[19258]: (root) CMD (wvdial)
Aug  7 21:00:01 alpha CRON[19370]: (root) CMD (wvdial)
Aug  7 22:00:01 alpha CRON[19701]: (root) CMD (wvdial)
Aug  7 23:00:01 alpha CRON[19897]: (root) CMD (wvdial)
Aug  8 00:00:01 alpha CRON[19923]: (root) CMD (wvdial)
Aug  8 01:00:01 alpha CRON[19942]: (root) CMD (wvdial)
Aug  8 02:00:01 alpha CRON[19963]: (root) CMD (wvdial)
Aug  8 03:00:01 alpha CRON[19981]: (root) CMD (wvdial)
Aug  8 04:00:01 alpha CRON[19999]: (root) CMD (wvdial)
Aug  8 05:00:01 alpha CRON[20021]: (root) CMD (wvdial)
Aug  8 06:00:01 alpha CRON[20136]: (root) CMD (wvdial)

```

Below is the syslog for the day the connect dropped and  auto reconnected.
```

darren@alpha:/var/log$ zcat syslog.6.gz | grep pppd
Aug  8 22:28:26 alpha pppd[19765]: LCP terminated by peer
Aug  8 22:28:26 alpha pppd[19765]: Connect time 1440.0 minutes.
Aug  8 22:28:26 alpha pppd[19765]: Sent 29033601 bytes, received 4615227 bytes.
Aug  8 22:28:26 alpha pppd[19765]: restoring old default route to eth0 [192.168.1.2]
Aug  8 22:28:27 alpha pppd[19765]: Modem hangup
Aug  8 22:28:27 alpha pppd[19765]: Connection terminated.
Aug  8 22:28:28 alpha pppd[19765]: Exit.
Aug  8 22:28:34 alpha pppd[23171]: pppd 2.4.5 started by root, uid 0
Aug  8 22:28:34 alpha pppd[23171]: Using interface ppp0
Aug  8 22:28:34 alpha pppd[23171]: Connect: ppp0 <--> /dev/ttyUSB2
Aug  8 22:28:34 alpha pppd[23171]: CHAP authentication succeeded
Aug  8 22:28:34 alpha pppd[23171]: CHAP authentication succeeded
Aug  8 22:28:36 alpha pppd[23171]: Could not determine remote IP address: defaulting to 10.64.64.64
Aug  8 22:28:36 alpha pppd[23171]: replacing old default route to eth0 [192.168.1.2]
Aug  8 22:28:36 alpha pppd[23171]: local  IP address 10.217.XXX.XXX
Aug  8 22:28:36 alpha pppd[23171]: remote IP address 10.64.64.64
Aug  8 22:28:36 alpha pppd[23171]: primary   DNS address 202.27.156.72
Aug  8 22:28:36 alpha pppd[23171]: secondary DNS address 202.27.158.40

```

Below is the log when the modem did not reconnect.  Note the modem hung up rather than peer termination.
```

darren@alpha:/var/log$ zcat syslog.5.gz | grep pppd
Aug  9 10:10:45 alpha pppd[23171]: Modem hangup
Aug  9 10:10:46 alpha pppd[23171]: Connect time 702.2 minutes.
Aug  9 10:10:46 alpha pppd[23171]: Sent 10039888 bytes, received 2936726 bytes.
Aug  9 10:10:46 alpha pppd[23171]: restoring old default route to eth0 [192.168.1.2]
Aug  9 10:10:46 alpha pppd[23171]: Connection terminated.
Aug  9 10:10:47 alpha pppd[23171]: Exit.

```

Below is the wvdial.conf file.  This works 
```

darren@alpha:/etc$ sudo cat wvdial.conf
[sudo] password for darren:
[Dialer Defaults]
Modem = /dev/ttyUSB2
Modem Type = Analog Modem
ISDN = 0
Baud = 460800

Phone = *99#
Password = pass
Username = user
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = ATS7=60 S30=0 S0=0
Init4 = AT+CGDCONT=1,"IP","wap.telecom.co.nz"
Stupid Mode = 1
Auto Reconnect = on

```

Below is the output of lsusb.  Nothing out of place.
```

darren@alpha:/etc$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 002 Device 003: ID 046d:0807 Logitech, Inc. Webcam B500
Bus 004 Device 003: ID 19d2:0031 ZTE WCDMA Technologies MSM MF110/MF627/MF636


```

Below is most of the verbose output.
```

darren@alpha:/etc$lsusb -s 004:003 -v
Bus 004 Device 003: ID 19d2:0031 ZTE WCDMA Technologies MSM MF110/MF627/MF636
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0
  bDeviceProtocol         0
  bMaxPacketSize0        64
  idVendor           0x19d2 ZTE WCDMA Technologies MSM
  idProduct          0x0031 MF110/MF627/MF636
  bcdDevice            0.00
  iManufacturer           2
  iProduct                1
  iSerial                 3
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          256
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
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  05 24 15 00 01
      ** UNRECOGNIZED:  05 24 06 00 00
      ** UNRECOGNIZED:  15 24 12 20 01 98 b0 6a 49 b0 9e 48 96 94 46 d9 9a 28 ca
 4e 5d
      ** UNRECOGNIZED:  06 24 13 00 01 10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  05 24 15 00 01
      ** UNRECOGNIZED:  05 24 06 01 01
      ** UNRECOGNIZED:  15 24 12 20 01 98 b0 6a 49 b0 9e 48 96 94 46 d9 9a 28 ca
 4e 5d
      ** UNRECOGNIZED:  06 24 13 00 01 10
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           2
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x02  EP 2 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        2
      bAlternateSetting       0
      bNumEndpoints           2
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      6 SCSI
      bInterfaceProtocol     80 Bulk-Only
      iInterface              0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
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
      bNumEndpoints           3
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              0
      ** UNRECOGNIZED:  05 24 00 10 01
      ** UNRECOGNIZED:  04 24 02 02
      ** UNRECOGNIZED:  05 24 01 03 03
      ** UNRECOGNIZED:  05 24 06 03 03
      ** UNRECOGNIZED:  15 24 12 20 01 98 b0 6a 49 b0 9e 48 96 94 46 d9 9a 28 ca
 4e 5d
      ** UNRECOGNIZED:  06 24 13 00 01 10
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x85  EP 5 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval              32

```

---

### Post by dazz100 on 2013-09-01
Hi
I haven't figured out how or why I can't restart wvdial after a dropout.  I have written a script that will try to restart wvdial and confirm a network connection by attempting to ping a number of high reliability servers.  If all of the ping attempts fail, then the server will be rebooted as a last resort attempt to reopen comms.  The script is run once an hour.

---

