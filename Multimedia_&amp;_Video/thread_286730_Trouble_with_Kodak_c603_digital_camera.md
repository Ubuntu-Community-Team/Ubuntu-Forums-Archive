---
title: "Trouble with Kodak c603 digital camera"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by weiersc on 2006-10-28
Hi 

When I plug in my Kodak C603 camera and switch it on I immediately get a "Camera detected" dialogue box asking if I want to import photos.

The camera seems to be identified as a PTP/IP Camera.

But as it tries to download the pictures it gives me the following error:

('Could not claim the USB device'): Could not claim interce 0 (Operation not permitted). Make sure the program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you ahve read/write access to the device.

How would I get access to the camera?


(I use Ubuntu Edgy)

Thanks

Weiers

---

### Post by DktrKranz on 2006-10-28
First, make sure you are member of plugdev group by typing *id* command on a terminal. If you have Edgy, it should already be.

After that, plug your camera in and type the following command:
```
for dev in `ls /sys/bus/usb/devices`; do udevinfo -ap /sys/bus/usb/devices/$dev; done
```
Search through the information until you find your camera details. You have to write down *idVendor* and *idProduct* codes.

Once you find these, you have to open */etc/udev/rules.d/45-libgphoto2.rules* (name may change) and write the following line at the bottom of the file, just before *LABEL="libgphoto2_rules_end"*:
```
SYSFS{idVendor}=="your_idVendor", SYSFS{idProduct}=="your_idProduct", MODE="0660", GROUP="plugdev"
```
Now restart udev (*/etc/init.d/udev restart*) and you should be able to access your digital camera.

---

### Post by weiersc on 2006-10-28
Thank you very much, that worked.

---

### Post by bihe on 2006-10-29
Just came along this post - perfect solution; now everything works.
Where have you found the solution for this?

---

### Post by DktrKranz on 2006-10-29
> **bihe said:**
> Where have you found the solution for this?

I read libgphoto2 README files and did some deeper investigations, but you can call it a lucky strike :D

---

### Post by raintheory on 2006-10-30
> **DktrKranz said:**
> ...
After that, plug your camera in and type the following command:
```
for dev in `ls /sys/bus/usb/devices`; do udevinfo -ap /sys/bus/usb/devices/$dev; done
```
Search through the information until you find your camera details. You have to write down *idVendor* and *idProduct* codes.
...


What steps need to be taken if the camera details are *not* shown in the list?

The camera is plugged in, and detected (but I receive the error), and this is the output of the command:

```
    SYSFS{bmAttributes}=="a0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb3':
    ID=="usb3"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.1"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.1':
    ID=="0000:00:1d.1"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024D4sv00001179sd0000FF00bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="209"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24d4"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0':
    KERNEL=="3-1:1.0"
    SUBSYSTEM=="usb"
    SYSFS{modalias}=="usb:v045Ep0053d0300dc00dsc00dp00ic03isc01ip02"
    SYSFS{bInterfaceProtocol}=="02"
    SYSFS{bInterfaceSubClass}=="01"
    SYSFS{bInterfaceClass}=="03"
    SYSFS{bNumEndpoints}=="01"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceNumber}=="00"

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb3/3-1':
    ID=="3-1"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{product}=="Microsoft 3-Button Mouse with IntelliEye_TM_"
    SYSFS{manufacturer}=="Microsoft"
    SYSFS{maxchild}=="0"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="2"
    SYSFS{speed}=="1.5"
    SYSFS{bMaxPacketSize0}=="8"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="00"
    SYSFS{bcdDevice}=="0300"
    SYSFS{idProduct}=="0053"
    SYSFS{idVendor}=="045e"
    SYSFS{bMaxPower}=="100mA"
    SYSFS{bmAttributes}=="a0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb3':
    ID=="usb3"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.1"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.1':
    ID=="0000:00:1d.1"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024D4sv00001179sd0000FF00bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="209"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24d4"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0':
    KERNEL=="4-0:1.0"
    SUBSYSTEM=="usb"
    SYSFS{modalias}=="usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00"
    SYSFS{bInterfaceProtocol}=="00"
    SYSFS{bInterfaceSubClass}=="00"
    SYSFS{bInterfaceClass}=="09"
    SYSFS{bNumEndpoints}=="01"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceNumber}=="00"

  looking at device '/devices/pci0000:00/0000:00:1d.2/usb4':
    ID=="usb4"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.2"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.2':
    ID=="0000:00:1d.2"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024D7sv00001179sd0000FF00bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="193"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24d7"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0':
    KERNEL=="5-0:1.0"
    SUBSYSTEM=="usb"
    SYSFS{modalias}=="usb:v0000p0000d0206dc09dsc00dp00ic09isc00ip00"
    SYSFS{bInterfaceProtocol}=="00"
    SYSFS{bInterfaceSubClass}=="00"
    SYSFS{bInterfaceClass}=="09"
    SYSFS{bNumEndpoints}=="01"
    SYSFS{bAlternateSetting}==" 0"
    SYSFS{bInterfaceNumber}=="00"

  looking at device '/devices/pci0000:00/0000:00:1d.3/usb5':
    ID=="usb5"
    BUS=="usb"
    DRIVER=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.3"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.3':
    ID=="0000:00:1d.3"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024DEsv00001179sd0000FF00bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="177"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24de"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb1':
    KERNEL=="usb1"
    SUBSYSTEM=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.7"
    SYSFS{product}=="EHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic ehci_hcd"
    SYSFS{maxchild}=="8"
    SYSFS{version}==" 2.00"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="480"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="01"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.7':
    ID=="0000:00:1d.7"
    BUS=="pci"
    DRIVER=="ehci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024DDsv00001179sd0000FF00bc0Csc03i20"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="201"
    SYSFS{class}=="0x0c0320"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24dd"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:1d.0/usb2':
    KERNEL=="usb2"
    SUBSYSTEM=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.0"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.0':
    ID=="0000:00:1d.0"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024D2sv00001179sd0000FF00bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="177"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24d2"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:1d.1/usb3':
    KERNEL=="usb3"
    SUBSYSTEM=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.1"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.1':
    ID=="0000:00:1d.1"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024D4sv00001179sd0000FF00bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="209"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24d4"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:1d.2/usb4':
    KERNEL=="usb4"
    SUBSYSTEM=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.2"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.2':
    ID=="0000:00:1d.2"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024D7sv00001179sd0000FF00bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="193"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24d7"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""


udevinfo starts with the device the node belongs to and then walks up the
device chain, to print for every device found, all possibly useful attributes
in the udev key format.
Only attributes within one device section may be used together in one rule,
to match the device for which the node will be created.

  looking at device '/devices/pci0000:00/0000:00:1d.3/usb5':
    KERNEL=="usb5"
    SUBSYSTEM=="usb"
    SYSFS{configuration}==""
    SYSFS{serial}=="0000:00:1d.3"
    SYSFS{product}=="UHCI Host Controller"
    SYSFS{manufacturer}=="Linux 2.6.17-10-generic uhci_hcd"
    SYSFS{maxchild}=="2"
    SYSFS{version}==" 1.10"
    SYSFS{devnum}=="1"
    SYSFS{speed}=="12"
    SYSFS{bMaxPacketSize0}=="64"
    SYSFS{bNumConfigurations}=="1"
    SYSFS{bDeviceProtocol}=="00"
    SYSFS{bDeviceSubClass}=="00"
    SYSFS{bDeviceClass}=="09"
    SYSFS{bcdDevice}=="0206"
    SYSFS{idProduct}=="0000"
    SYSFS{idVendor}=="0000"
    SYSFS{bMaxPower}=="  0mA"
    SYSFS{bmAttributes}=="e0"
    SYSFS{bConfigurationValue}=="1"
    SYSFS{bNumInterfaces}==" 1"

  looking at device '/devices/pci0000:00/0000:00:1d.3':
    ID=="0000:00:1d.3"
    BUS=="pci"
    DRIVER=="uhci_hcd"
    SYSFS{modalias}=="pci:v00008086d000024DEsv00001179sd0000FF00bc0Csc03i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="177"
    SYSFS{class}=="0x0c0300"
    SYSFS{subsystem_device}=="0xff00"
    SYSFS{subsystem_vendor}=="0x1179"
    SYSFS{device}=="0x24de"
    SYSFS{vendor}=="0x8086"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""

raintheory@edgy-laptop:~$ 

```

---

### Post by DktrKranz on 2006-10-30
You should attach dmesg output after plugging the camera in.

---

### Post by ai4sf on 2006-10-31
I tried everything listed so far and have gotten nowhere.  The device info only lists KERNEL=="devices"
           SUBSYSTEM==""

I can get into the 45-libgphot2.rules, but then what?

Ver. 6.06 worked flawlessly with my camera 6.06 has so far been problematic with my digital camera (Kodak P850).  It keeps giving the Cannot claim USB...sdc2xx,stv680, spca50x ... error.

---

### Post by ericcmi on 2006-11-01
This worked like a charm for my Kodac EasyShare CD33.

It works great under dapper, but had to apply this fix under edgy.

Now 100% working.

Thanks a million.

---

### Post by Ubuntu Joe on 2006-11-10
Dude!!  You Rock!!!

---

### Post by fpruter on 2006-11-24
WOW!  This was much more painless than I thought.  It worked with my new C743.  Thank you :-)  Now I'm off to make other things work.

---

### Post by idn on 2006-11-27
> **DktrKranz said:**
> First, make sure you are member of plugdev group by typing *id* command on a terminal. If you have Edgy, it should already be.

After that, plug your camera in and type the following command:
```
for dev in `ls /sys/bus/usb/devices`; do udevinfo -ap /sys/bus/usb/devices/$dev; done
```
Search through the information until you find your camera details. You have to write down *idVendor* and *idProduct* codes.

Once you find these, you have to open */etc/udev/rules.d/45-libgphoto2.rules* (name may change) and write the following line at the bottom of the file, just before *LABEL="libgphoto2_rules_end"*:
```
SYSFS{idVendor}=="your_idVendor", SYSFS{idProduct}=="your_idProduct", MODE="0660", GROUP="plugdev"
```
Now restart udev (*/etc/init.d/udev restart*) and you should be able to access your digital camera.

This also worked getting my Nikon S6 camera working under edgy - thanks!

---

### Post by chrisost on 2006-11-29
> **DktrKranz said:**
> 
Once you find these, you have to open */etc/udev/rules.d/45-libgphoto2.rules* (name may change) and write the following line at the bottom of the file, just before *LABEL="libgphoto2_rules_end"*:
```
SYSFS{idVendor}=="your_idVendor", SYSFS{idProduct}=="your_idProduct", MODE="0660", GROUP="plugdev"
```
Now restart udev (*/etc/init.d/udev restart*) and you should be able to access your digital camera.

According to [Bug 67532]("https://bugs.launchpad.net/distros/ubuntu/+source/libgphoto2/+bug/67532"), a better solution is to use the rule:
```
ENV{INTERFACE}=="6/1/1", MODE="0660", GROUP="plugdev"
```
This should work for all cameras that use the PTP (Picture Transfer Protocol) interface (most Kodak cameras and many others).

Edit:
I got home and tried this with my machine, and it didn't work as advertised.  According to  [this thread]("http://thread.gmane.org/gmane.linux.hotplug.devel/10711/focus=10712"), this may not actually be the correct way to do this.

---

### Post by Twigman on 2006-12-03
Just a quick note. An easier way to find the vendor/product id is to run lsusb. In my case (Kodak P850) I get:

Bus 003 Device 003: ID 040a:0592 Kodak Co. 

The ID part is in Vendor:Product form... so my camera is fixed by entering this line into the udev rules.d file:

SYSFS{idVendor}=="040a", SYSFS{idProduct}=="0592", MODE="0660", GROUP="plugdev"

---

### Post by dont42panic on 2006-12-19
This thread helped. Thanks to those who contributed!



James

---

### Post by herrma29 on 2006-12-25
I recently tried this for my camera, a kodak c743. I got so far as to add the code to 45-libgphoto2.rules, but when I tried doing the restart thing, I got this:

cp: preserving times for `/dev/net': Operation not permitted
cp: preserving times for `/dev/pts': Operation not permitted
cp: preserving times for `/dev/shm': Operation not permitted

The 45-libgphoto2.rules file is read-only, so I can't save the changes I made. I am extremely new to all of this, so if someone could tell me what I am doing wrong and the steps I need to take to fix it, that would be awesome.

---

### Post by DktrKranz on 2006-12-25
In order to modify such file, you have to open it using root privileges.
Supposing your preferred editor is gedit, you have to launch *sudo gedit /etc/udev/rules.d/45-libgphoto2.rules*.

---

### Post by herrma29 on 2006-12-25
ok, thanks a lot!

---

### Post by benndamann33 on 2006-12-28
you're a genius. By the way, if you get something weird like 0000 as your idvender and product, not necessarily wrong! Thanks again

---

### Post by hextor on 2007-01-06
Just to report that the solutions works also for Kodak EasyShare  C643. Probably works for all cameras with the error. Thanks!

---

### Post by desmoteo on 2007-01-09
It works also for my Canon Powershot G7.

Great!!!

---

### Post by Paerez on 2007-01-09
high five!

works for my Kodak V610.

I knew it was a udev rules thing but my attempt at making rules failed :D

thanks again.

---

### Post by jayatlinux on 2007-01-20
Many thanks, this worked perfectly on my Kodak EasyShare C653.

---

### Post by alenis on 2007-01-20
I had the same problem with a Canon 400d. After changing 45-libgphoto2.rules
the camera is found by the "Import Photo" utility (or whatever its name is in english: in italian it reads "Importa foto") but the utilty says "No image found" when the camera actually has images to download. Any suggestion?
Thanks
Alessandro

---

### Post by lanzen on 2007-02-19
I've found this thread today and it did help me out with my camera (Nikon coolpix 5600) in digikam 0.9.0.

Nice and easy. Thank you so much!   :)

---

### Post by Didjit on 2007-03-14
I originally had the same problem as the poster.  Followed the guide and everything worked fine.  After a recent update, it stopped working again. So I noticed the gphoto rules needed updating (again).  However, after making the same entires, I'm still have authority problems? I even rebooted and re:verified the rules. 

 I can run Digikam as Root and it finds my Camera, so I know its an authority issue. Is there someplace else I should look that needs authority changed? Running Edgy.

Tx

Didjit

---

### Post by DktrKranz on 2007-03-14
I posted a solution on the italian forum. Hope this works for you too.

Create */etc/udev/rules.d/45-cameraname.rules* file and insert the following line:
```
ACTION=="add", SYSFS{idVendor}=="XXXX", SYSFS{idProduct}=="YYYY", MODE="0660", GROUP="plugdev"
```
where XXXX and YYYY are *idVendor* and *idProduct* taken from *lsusb* command (or the longer one stated some posts ago).
Now restart udev and everything should work fine.

---

### Post by DktrKranz on 2007-03-14
Consider to request support for your camera by adding a new feature request: [http://sourceforge.net/tracker/?group_id=8874&atid=358874](http://sourceforge.net/tracker/?group_id=8874&atid=358874).

---

### Post by Milan SPK on 2007-03-14
i read all i could find both on forums and google, but couldnt see what am i doing wrong... i have kodak c533 camera 
```
milan@milan-desktop:~$ lsusb
Bus 001 Device 002: ID 040a:05a2 Kodak Co. 

```

i added as sugested a line in /etc/udev/rules.d/45-libgphoto2.rules at the end of list, before LABEL="libgphoto2_rules_end" :
```
SYSFS{idVendor}=="040a", SYSFS{idProduct}=="05a2", MODE="0660", GROUP="plugdev"
```

i restarted udev
```
sudo /etc/init.d/udev restart
```

but still no change. i rebooted the machine to, but nothing. i would really appreciate any help, thanks.

---

### Post by DktrKranz on 2007-03-14
Try to add a new file as I suggested some minutes ago.

---

### Post by marikka on 2007-03-14
> **DktrKranz said:**
> Try to add a new file as I suggested some minutes ago.

For my Canon IXUS 850IS the correct line was already in /etc/udev/rules.d/45-libgphoto2.rules, 
so I added the same line: ```
ACTION=="add", SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="3136", MODE="0660", GROUP="plugdev"
```
into  /etc/udev/rules.d/45-ixus850is.rules and restarted udev (sudo /etc/init.d/udev restart) and that worked!

Thank you so very much!

---

### Post by Didjit on 2007-03-14
> **DktrKranz said:**
> I posted a solution on the italian forum. Hope this works for you too.

Create */etc/udev/rules.d/45-cameraname.rules* file and insert the following line:
```
ACTION=="add", SYSFS{idVendor}=="XXXX", SYSFS{idProduct}=="YYYY", MODE="0660", GROUP="plugdev"
```where XXXX and YYYY are *idVendor* and *idProduct* taken from *lsusb* command (or the longer one stated some posts ago).
Now restart udev and everything should work fine.


Cool, thanks! That worked!!

Didjit

---

### Post by geovino on 2007-03-21
> **DktrKranz said:**
> First, make sure you are member of plugdev group by typing *id* command on a terminal. If you have Edgy, it should already be.

After that, plug your camera in and type the following command:
```
for dev in `ls /sys/bus/usb/devices`; do udevinfo -ap /sys/bus/usb/devices/$dev; done
```
Search through the information until you find your camera details. You have to write down *idVendor* and *idProduct* codes.

Once you find these, you have to open */etc/udev/rules.d/45-libgphoto2.rules* (name may change) and write the following line at the bottom of the file, just before *LABEL="libgphoto2_rules_end"*:
```
SYSFS{idVendor}=="your_idVendor", SYSFS{idProduct}=="your_idProduct", MODE="0660", GROUP="plugdev"
```
Now restart udev (*/etc/init.d/udev restart*) and you should be able to access your digital camera.

I tried that. I don't understand this. can you clarify. I can install my pics on my old pc with ubuntu. What causes this? I have a canon powershot a530.

---

### Post by jouni on 2007-03-25
If adding a line to 45-libgphoto2.rules has no effect, it could be caused by [Bug #91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250"), and you need to edit the beginning of the file as described on the bug page.

---

### Post by upbeat.linux on 2007-03-28
Thanks much jouni, that bug fix did the trick for my powershot A530!!! Rockage!

---

### Post by sween1911 on 2008-01-01
> **jouni said:**
> If adding a line to 45-libgphoto2.rules has no effect, it could be caused by [Bug #91250]("https://launchpad.net/ubuntu/+source/libgphoto2/+bug/91250"), and you need to edit the beginning of the file as described on the bug page.

THANKS! Just got a Nikon COOLPIX for Christmas and that did the trick.

---

