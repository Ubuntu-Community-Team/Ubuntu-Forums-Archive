---
title: "Creative WebCam NX"
date: 2009-01-20
forum: Multimedia Software
---

### Post by blcorp on 2009-01-20
Hello!
I have a Creative WebCam NX which work in ubuntu 5.10 - 8.04 with gspca driver in all programs. But after upgrade to 8.10 my webcam work only with cheese, and not work with skype,camorama,vlc... The device /dev/video0 exist. In skype (and flash sites such mebeam.com) I have a green noise. anybody can help me to start work my camera in skype/vlc?

```
$ lsusb 
Bus 004 Device 002: ID 041e:401c Creative Technology, Ltd WebCam NX [PD1110]

```

```
$ udevinfo --query=all --name=/dev/video0 --attribute-walk

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:10.2/usb4/4-2/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="gspca main driver"
    ATTR{index}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:10.2/usb4/4-2/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:10.2/usb4/4-2':
    KERNELS=="4-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}==" 80mA"
    ATTRS{urbnum}=="654"
    ATTRS{idVendor}=="041e"
    ATTRS{idProduct}=="401c"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="ff"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:10.2/usb4':
    KERNELS=="usb4"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="27"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="4"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.27-11-generic uhci_hcd"
    ATTRS{product}=="UHCI Host Controller"
    ATTRS{serial}=="0000:00:10.2"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:10.2':
    KERNELS=="0000:00:10.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="uhci_hcd"
    ATTRS{vendor}=="0x1106"
    ATTRS{device}=="0x3038"
    ATTRS{subsystem_vendor}=="0x1106"
    ATTRS{subsystem_device}=="0x3038"
    ATTRS{class}=="0x0c0300"
    ATTRS{irq}=="21"
    ATTRS{local_cpus}=="ffffffff,ffffffff"
    ATTRS{local_cpulist}=="0-63"
    ATTRS{modalias}=="pci:v00001106d00003038sv00001106sd00003038bc0Csc03i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

