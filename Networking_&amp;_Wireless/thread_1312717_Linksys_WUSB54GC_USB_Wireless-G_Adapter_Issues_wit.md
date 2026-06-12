---
title: "Linksys WUSB54GC USB Wireless-G Adapter Issues with 9.10 Upgrade"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by tuckerh on 2009-11-03
Hi,

I am using a Linksys WUSB54GC USB adapter on 64bit Ubuntu and have had some issues after upgrading to Karmic.  I had setup the adapter via the instructions here: [http://ubuntuforums.org/showthread.php?t=1155941](http://ubuntuforums.org/showthread.php?t=1155941) for 9.04 and it was working fine.

After upgrading to 9.10 the device was automatically detected as wlan0 instead of ra0.  However I have to issues.

1) When I try to view wireless networks, either with wifi-radar or with the network controller menubar item the network SSIDs are garbled non-latin characters.

2) When I attempt to associate with an ad-hoc network (the primary use of this device for me) the ESSID fails to stay set and thus I am unable to connect to the network.

lsusb -v output for the device:

```

sudo lsusb -v -s 002:003

Bus 002 Device 003: ID 1737:0077 Linksys 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1737 Linksys
  idProduct          0x0077 
  bcdDevice            1.01
  iManufacturer           1 Ralink
  iProduct                2 802.11 g WLAN
  iSerial                 3 1.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           67
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              450mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           7
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              5 1.0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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
        bEndpointAddress     0x03  EP 3 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x04  EP 4 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
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

```

---

### Post by elfratysa on 2009-11-05
Compile it from step 6 for the new kernel and it should work

---

### Post by vanjan on 2009-11-06
hi,

I'm running fresh installation of Ubuntu 9.10 32bit.
I'm getting this error on step 6:
```

root@ubuntu:/home/jan/Desktop/rtlin# make && make install
make -C tools
make[1]: Entering directory `/home/jan/Desktop/rtlin/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jan/Desktop/rtlin/tools'
/home/jan/Desktop/rtlin/tools/bin2h
cp -f os/linux/Makefile.6 /home/jan/Desktop/rtlin/os/linux/Makefile
make  -C  /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/jan/Desktop/rtlin/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/md5.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/mlme.o
/home/jan/Desktop/rtlin/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/jan/Desktop/rtlin/os/linux/../../common/mlme.c:4259: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/action.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/cmm_data.o
/home/jan/Desktop/rtlin/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/jan/Desktop/rtlin/os/linux/../../common/cmm_data.c:713: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/rtmp_init.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/cmm_sync.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/eeprom.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/cmm_info.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/cmm_wpa.o
/home/jan/Desktop/rtlin/os/linux/../../common/cmm_wpa.c: In function ‘AES_GTK_KEY_WRAP’:
/home/jan/Desktop/rtlin/os/linux/../../common/cmm_wpa.c:836: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/dfs.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../common/spectrum.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/assoc.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/aironet.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/auth.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/sync.o
/home/jan/Desktop/rtlin/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/jan/Desktop/rtlin/os/linux/../../sta/sync.c:1393: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/jan/Desktop/rtlin/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/jan/Desktop/rtlin/os/linux/../../sta/sync.c:934: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/jan/Desktop/rtlin/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/jan/Desktop/rtlin/os/linux/../../sta/sync.c:675: warning: the frame size of 1256 bytes is larger than 1024 bytes
/home/jan/Desktop/rtlin/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/jan/Desktop/rtlin/os/linux/../../sta/sync.c:533: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/sanity.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/connect.o
/home/jan/Desktop/rtlin/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/jan/Desktop/rtlin/os/linux/../../sta/connect.c:351: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../sta/wpa.o
/home/jan/Desktop/rtlin/os/linux/../../sta/wpa.c: In function ‘CCKMPRF’:
/home/jan/Desktop/rtlin/os/linux/../../sta/wpa.c:1848: warning: the frame size of 1044 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_linux.o
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_linux.c:1043: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.o
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/jan/Desktop/rtlin/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/jan/Desktop/rtlin/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [LINUX] Error 2

```

---

### Post by theluddite on 2010-01-23
Me too.  Anyone have any suggestions?

---

### Post by tinksmartbstupid on 2010-02-16
Me three! Any ideas?

---

### Post by b k on 2010-02-17
Hi, if you are able to uninstall what you previously tried, you may perhaps like to take a look at post #68 and #69 of this link [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446889) and see if you want to give the 'solution' there a try.
 
You may also like to take a look here [http://ubuntuforums.org/showthread.php?t=1353044](http://ubuntuforums.org/showthread.php?t=1353044) .
 
Your feedback would be must helpful.
 
Good luck.

---

