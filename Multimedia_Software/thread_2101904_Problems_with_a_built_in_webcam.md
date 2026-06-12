---
title: "Problems with a built in webcam"
date: 2013-01-05
forum: Multimedia Software
---

### Post by xap1234 on 2013-01-05
Hi, I have a Dell Inspiron n7110 with a Integrated 1280x720 native HD Webcam.  I run unbuntu version Ubuntu 12.04   My built in webcam is not working I have tried installing cheese and camorama and it still is not working.  I have no idea why and can not find any threads or helps that can solve my problem.  Can anyone help me?

Thanks Xap1234

---

### Post by Bucky Ball on 2013-01-05
*Thread moved to **Multimedia & Video***

You might have more luck here.

---

### Post by xc3RnbFO8P on 2013-01-05
> **xap1234 said:**
> Hi, I have a Dell Inspiron n7110 with a Integrated 1280x720 native HD Webcam.  I run unbuntu version Ubuntu 12.04   My built in webcam is not working I have tried installing cheese and camorama and it still is not working.  I have no idea why and can not find any threads or helps that can solve my problem.  Can anyone help me?

Thanks Xap1234

Start by showing the output of:
> lsusb

---

### Post by xap1234 on 2013-01-05
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 8086:0189 Intel Corp.

---

### Post by xap1234 on 2013-01-05
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video***

You might have more luck here.
  Thank you! :)

---

### Post by xc3RnbFO8P on 2013-01-05
> **xap1234 said:**
> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 8086:0189 Intel Corp.

Nothing there.

Next step:
> sudo apt-get install hwinfo
and then show the output of:
> hwinfo --usb

---

### Post by xap1234 on 2013-01-06
> hal.1: read hal dataprocess 3082: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
03: USB 00.0: 10a00 Hub                                         
  [Created at usb.122]
  Unique ID: k4bc.FHd55n4xKo7
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 3.2.0-35-generic-pae ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.2.0-35-generic-pae ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "3.02"
  Serial ID: "0000:00:1a.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

04: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: pBe4.oLWCeziExdF
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
  SysFS BusID: 2-0:1.0
  Hardware Class: hub
  Model: "Linux 3.2.0-35-generic-pae ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.2.0-35-generic-pae ehci_hcd"
  Device: usb 0x0002 "EHCI Host Controller"
  Revision: "3.02"
  Serial ID: "0000:00:1d.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0302dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

05: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: uIhY.tisqRJYDXEC
  SysFS ID: /devices/pci0000:00/0000:00:1c.2/0000:02:00.0/usb3/3-0:1.0
  SysFS BusID: 3-0:1.0
  Hardware Class: hub
  Model: "Linux 3.2.0-35-generic-pae xhci_hcd xHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.2.0-35-generic-pae xhci_hcd"
  Device: usb 0x0002 "xHCI Host Controller"
  Revision: "3.02"
  Serial ID: "0000:02:00.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v1D6Bp0002d0302dc09dsc00dp01ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

06: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: zPk0.m2+1uGKvSS5
  SysFS ID: /devices/pci0000:00/0000:00:1c.2/0000:02:00.0/usb4/4-0:1.0
  SysFS BusID: 4-0:1.0
  Hardware Class: hub
  Model: "Linux 3.2.0-35-generic-pae xhci_hcd xHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.2.0-35-generic-pae xhci_hcd"
  Device: usb 0x0003 "xHCI Host Controller"
  Revision: "3.02"
  Serial ID: "0000:02:00.0"
  Driver: "hub"
  Driver Modules: "usbcore"
  Module Alias: "usb:v1D6Bp0003d0302dc09dsc00dp03ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

07: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: ADDn.4Nx_qoDfSd7
  Parent ID: k4bc.FHd55n4xKo7
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
  SysFS BusID: 1-1:1.0
  Hardware Class: hub
  Model: "Hub"
  Hotplug: USB
  Vendor: usb 0x8087 
  Device: usb 0x0024 
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #3 (Hub)

08: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: FKGF.4Nx_qoDfSd7
  Parent ID: pBe4.oLWCeziExdF
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  SysFS BusID: 2-1:1.0
  Hardware Class: hub
  Model: "Hub"
  Hotplug: USB
  Vendor: usb 0x8087 
  Device: usb 0x0024 
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v8087p0024d0000dc09dsc00dp01ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #4 (Hub)

09: USB 00.0: 11500 Bluetooth Device
  [Created at usb.122]
  Unique ID: Bgjr.y16PMT12uLE
  Parent ID: FKGF.4Nx_qoDfSd7
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0
  SysFS BusID: 2-1.5:1.0
  Hardware Class: bluetooth
  Model: "Intel Bluetooth Device"
  Hotplug: USB
  Vendor: usb 0x8086 "Intel Corp."
  Device: usb 0x0189 
  Revision: "69.19"
  Driver: "btusb"
  Driver Modules: "btusb"
  Speed: 12 Mbps
  Module Alias: "usb:v8086p0189d6919dcE0dsc01dp01icE0isc01ip01"
  Driver Info #0:
    Driver Status: btusb is active
    Driver Activation Cmd: "modprobe btusb"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #8 (Hub)

---

### Post by xc3RnbFO8P on 2013-01-06
And
> dmesg | grep video

---

### Post by xap1234 on 2013-01-06
[    0.710752] pci 0000:00:02.0: Boot video device

---

### Post by xc3RnbFO8P on 2013-01-06
Well this is a certified computer for Ubuntu and almost nothing works,
maybe you need to report a bug.

[http://www.ubuntu.com/certification/hardware/201101-6983/]("http://www.ubuntu.com/certification/hardware/201101-6983/")

---

### Post by xap1234 on 2013-01-06
Well #$%@  Okay maybe someone else can help me or maybe I am just $%^#ed! <G>

---

### Post by xap1234 on 2013-01-06
Well I will report the bug but in hopes of a miracle, is there anyone else out there who might have incite into my problem?  Not holding my breath the last person who tried to help knew what he was doing, but it is worth a shot! <G>

---

### Post by dewdrop_world on 2013-01-08
Something to try -- is there a key combination on your laptop to enable/disable the webcam?

I had the same problem last night and posted in this thread. That post was moved to its own thread. Overnight I remembered that there's a Fn+F# (F# = one of the numbered function keys) combination for the webcam. So this morning, I tried it and now the webcam is fine.

[http://ubuntuforums.org/showpost.php?p=12445933&postcount=3](http://ubuntuforums.org/showpost.php?p=12445933&postcount=3)

Of course I can't guarantee that this will solve your problem, but the symptom on my machine was exactly the same. And, it stands to reason that if the camera is disabled at the hardware level, obviously Linux won't be able to talk to it (and this is a plausible explanation why it isn't found in lsusb, hwinfo or dmesg).

hjh

---

### Post by xap1234 on 2013-01-09
Yes I checked that unfortunately there is no webcam button on m computer :(

---

