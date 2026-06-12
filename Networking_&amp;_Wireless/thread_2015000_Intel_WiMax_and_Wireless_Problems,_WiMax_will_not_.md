---
title: "Intel WiMax and Wireless Problems, WiMax will not activate."
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by tripflex on 2012-07-02
Alright i'm going to try and keep this as short and sweet as possible. Intel Centrino N + WiMax 6250 built into a Dell Latitude E6420, WiFi works, WiMax does not.

Originally I was able to see both wlan0 and wmx0 under rfkill list but even with attempting to rfkill just wlan0 itself and then bring up wmx0 did not work.  I then tried rebuilding the modules using the latest compat-wireless, and then went further and used an even more newer version from [http://git.kernel.org/?p=linux/kernel/git/linville/wireless-testing.git](http://git.kernel.org/?p=linux/kernel/git/linville/wireless-testing.git)

So where i'm at now is i re-installed the entire compat-wireless set of drivers and it's now picking up the WiMax as a USB device and i'm no longer getting it showing up under rfkill list.

Linux bh 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Since it was showing up as USB i went ahead and built a VM using the same exact distro and kernel as the host and then attached it to the VM.  This is the output i got from the syslog:

```

ul  2 17:50:40 bh-dev kernel: [ 1872.679942] usb 1-1: new high-speed USB device number 4 using ehci_hcd
Jul  2 17:50:40 bh-dev mtp-probe: checking bus 1, device 4: "/sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1"
Jul  2 17:50:40 bh-dev kernel: [ 1873.054085] i2400m_usb 1-1:1.0: WiMAX interface wmx0 (00:1d:e1:47:c9:24) ready
Jul  2 17:50:45 bh-dev kernel: [ 1878.002371] i2400m_usb 1-1:1.0: firmware interface version 9.3.2
Jul  2 17:50:45 bh-dev mtp-probe: bus: 1, device: 4 was not an MTP device
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> found WiMAX radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.0/rfkill/rfkill2) (driver i2400m_usb)
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> WiMAX now disabled by radio killswitch
Jul  2 17:50:45 bh-dev NetworkManager[684]: <warn> failed to allocate link cache: (-10) Operation not supported
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> (wmx0): carrier is OFF
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> (wmx0): new Ethernet device (driver: 'i2400m_usb' ifindex: 5)
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> (wmx0): exported as /org/freedesktop/NetworkManager/Devices/3
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> (wmx0): now managed
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> (wmx0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> (wmx0): bringing up device.
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> (wmx0): preparing device.
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> (wmx0): deactivating device (reason 'managed') [2]
Jul  2 17:50:45 bh-dev kernel: [ 1878.049867] ADDRCONF(NETDEV_UP): wmx0: link is not ready
Jul  2 17:50:45 bh-dev kernel: [ 1878.050716] ADDRCONF(NETDEV_UP): wmx0: link is not ready
Jul  2 17:50:45 bh-dev NetworkManager[684]: <info> Added default wired connection 'Wired connection 2' for /sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.0/net/wmx0
Jul  2 17:50:45 bh-dev NetworkManager[684]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.0/net/wmx0, iface: wmx0)
Jul  2 17:50:45 bh-dev NetworkManager[684]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:11.0/0000:02:03.0/usb1/1-1/1-1:1.0/net/wmx0, iface: wmx0): no ifupdown configuration found.
Jul  2 17:51:11 bh-dev kernel: [ 1903.751253] i2400m_usb 1-1:1.0: TX: cannot send URB; retrying. tx_msg @224 64 B [0 sent]: -110

```

It looks like the WiMax is being recognized by the VM and loading the i2400m driver, but NM is showing "carrier is OFF" and just like when i first setup the laptop and the wmx0 was showing up on the host, NM puts the device under a "WIRED CONNECTION".

lspci -v (from host)
```

03:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 5e)
	Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e6600000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number REMOVED
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

```

lshw -C network
```


  *-network
       description: Wireless interface
       product: Centrino Advanced-N + WiMAX 6250
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 5e
       serial: REMOVED
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:e6600000-e6601fff

```

lsusb
```

Bus 002 Device 003: ID 8086:0188 Intel Corp. WiMAX Connection 2400m

```

lsusb -v 
```

Bus 002 Device 003: ID 8086:0188 Intel Corp. WiMAX Connection 2400m
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x8086 Intel Corp.
  idProduct          0x0188 WiMAX Connection 2400m
  bcdDevice            0.00
  iManufacturer           1 Intel(R) Corporation
  iProduct                2 Intel(R) Centrino(R) Advanced-N + WiMAX 6250
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           46
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           4
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass      0 
      bInterfaceProtocol      0 
      iInterface              0 
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
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               5
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

```



So needless to say i'm at the point now where the only thing left to do is bang my head against the wall.  Does anybody have any suggestions or ideas on what I can do to try and get this thing working?  

Either way all the threads i've found were people just having problems with WiFi which is not my issue and most of their problems were solved by installing the correct driver...which most didn't even know how to do.  I've spent many hours trying to figure this out and just don't know where to go from here...

---

### Post by tripflex on 2012-07-03
Thank you for contacting Intel Technical Support.

I understand that you have some questions in regards of Intel WiMAX* adapters and Linux*.

Note that at this moment Linux* is not a supported Operating System for the current line of Intel WiMAX* adapters.

Currently there are no plans to create Linux* support for the current line-up of Intel WiMAX* capable adapters.

We are sorry for the inconvenience.

Regards

Sergio G.

Intel Technical Support

Intel is a registered trademark of Intel Corporation or its subsidiaries in the United States and other countries. *Other names and brands may be claimed as the property of others.

A representative of Intel may subsequently contact you by email in order to obtain your feedback on the quality of the support you received. If you do not wish to participate, simply delete the survey email.



-------------


That's just redonculous.  Yeah i just made that word up.  Guess it's back to Windows as my bare metal for now, already gone over my 5GB limit on my company wireless, I need my WiMax back!  Boo!

---

