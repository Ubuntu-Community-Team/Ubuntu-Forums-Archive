---
title: "Help assign USB webcam with udev"
date: 2008-04-04
forum: Multimedia &amp; Video
---

### Post by jdogzilla on 2008-04-04
Hello all, I am trying to setup a rule in udev to assign my USB webcam with a specific device name.  I have a PVR-500 card which generally occupies /dev/video0 and /dev/video1.  When I plug in my webcam, it will take up /dev/video2.  However, if I reboot with the webcam attached, it takes up /dev/video0 which messes up my Mythtv setup.  



Here is the rule I have in /etc/udev/rules.d/10-local.rules  << THIS IS NOT WORKING!

SUBSYSTEMS=="usb",ATTRS{manufacturer}=="Sonix Technology Co., Ltd.",ATTRS{idProduct}=="62c0",ATTRS{idVendor}=="0c45",NAME="vi
deo2"




udev info for the camera is as follows:

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/class/video4linux/video2':
    KERNEL=="video2"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="USB 2.0 Camera"
    ATTR{dev}=="81:2"

  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1/1-2/1-2:1.0':
    KERNELS=="1-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="uvcvideo"
    ATTRS{interface}=="USB 2.0 Camera"
    ATTRS{modalias}=="usb:v0C45p62C0d0100dcEFdsc02dp01ic0Eisc01ip00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceClass}=="0e"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1/1-2':
    KERNELS=="1-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{product}=="USB 2.0 Camera"
    ATTRS{manufacturer}=="Sonix Technology Co., Ltd."
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="18"
    ATTRS{busnum}=="1"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bDeviceClass}=="ef"
    ATTRS{bcdDevice}=="0100"
    ATTRS{idProduct}=="62c0"
    ATTRS{idVendor}=="0c45"
    ATTRS{bMaxPower}==" 98mA"
    ATTRS{bmAttributes}=="80"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:17"

  looking at parent device '/devices/pci0000:00/0000:00:0b.1/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:0b.1"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.22-14-generic ehci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="8"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="1"
    ATTRS{speed}=="480"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:0"

  looking at parent device '/devices/pci0000:00/0000:00:0b.1':
    KERNELS=="0000:00:0b.1"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{modalias}=="pci:v000010DEd0000026Esv00001043sd000081BCbc0Csc03i20"
    ATTRS{local_cpus}=="ff"
    ATTRS{irq}=="18"
    ATTRS{class}=="0x0c0320"
    ATTRS{subsystem_device}=="0x81bc"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{device}=="0x026e"
    ATTRS{vendor}=="0x10de"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""

Can someone please help me with the right rule for udev?  I am running Gutsy.

---

### Post by jdogzilla on 2008-04-07
Anybody?  Anybody?

---

