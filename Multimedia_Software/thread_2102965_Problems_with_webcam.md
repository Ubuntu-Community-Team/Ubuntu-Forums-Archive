---
title: "Problems with webcam"
date: 2013-01-08
forum: Multimedia Software
---

### Post by dewdrop_world on 2013-01-08
Now I am having the same problem, except that my MSI A6200's built-in webcam used to work perfectly. I know, because I used it in Skype over the summer (after upgrading to 12.04 -- so the culprit is not an Ubuntu version upgrade). Then I got an android tablet and started using that for Skype instead, and I didn't touch my laptop's camera for about six months.

Now, there is no /dev/video* anything. Cheese says "no device found," and I have a Pure Data patch that used to be able to access the video camera that says it can't access /dev/video0.

The most logical conclusion is that some package was updated in the last six months that broke webcam support. Again, I'm completely certain that it was fine back in July 2012.

The only other thing I can try (tomorrow, getting late here) is to boot into older kernels and see if one of them still works.

xap1234, after you've logged the bug, can you post the link here? I want to add myself to the report. (Unfortunately, it looks like we're both hosed.)

hjh


uname -a
Linux dlm-A6200 3.2.0-35-lowlatency #34-Ubuntu SMP PREEMPT Tue Dec 18 18:12:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

PS I want to use the webcam for control of interactive music software (in SuperCollider and Pure Data), and this requires the lowlatency kernel. So "use the generic kernel" is valid as a troubleshooting step in my case, but not a solution.


lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 05a4:9734 Ortek Technology, Inc. 
Bus 002 Device 004: ID 0763:2012 Midiman M-Audio Fast Track Pro
Bus 002 Device 005: ID 05a4:9734 Ortek Technology, Inc. 
Bus 002 Device 006: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 007: ID 0488:0010 Cirque Corp. 


hwinfo --usb
> hal.1: read hal dataprocess 2753: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
03: USB 00.0: 10a00 Hub                                         
  [Created at usb.122]
  Unique ID: k4bc.FHd55n4xKo7
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-0:1.0
  SysFS BusID: 1-0:1.0
  Hardware Class: hub
  Model: "Linux 3.2.0-35-lowlatency ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.2.0-35-lowlatency ehci_hcd"
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
  Model: "Linux 3.2.0-35-lowlatency ehci_hcd EHCI Host Controller"
  Hotplug: USB
  Vendor: usb 0x1d6b "Linux 3.2.0-35-lowlatency ehci_hcd"
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
  Unique ID: ADDn.0j9+vWlqL56
  Parent ID: k4bc.FHd55n4xKo7
  SysFS ID: /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1:1.0
  SysFS BusID: 1-1:1.0
  Hardware Class: hub
  Model: "Hub"
  Hotplug: USB
  Vendor: usb 0x8087 
  Device: usb 0x0020 
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #3 (Hub)

06: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: FKGF.0j9+vWlqL56
  Parent ID: pBe4.oLWCeziExdF
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
  SysFS BusID: 2-1:1.0
  Hardware Class: hub
  Model: "Hub"
  Hotplug: USB
  Vendor: usb 0x8087 
  Device: usb 0x0020 
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 480 Mbps
  Module Alias: "usb:v8087p0020d0000dc09dsc00dp01ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #4 (Hub)

07: USB 00.0: 10a00 Hub
  [Created at usb.122]
  Unique ID: Bgjr.D3cPvvGdtc3
  Parent ID: FKGF.0j9+vWlqL56
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0
  SysFS BusID: 2-1.5:1.0
  Hardware Class: hub
  Model: "Ortek ORTEK KH12 USB Hub"
  Hotplug: USB
  Vendor: usb 0x05a4 "Ortek Technology, Inc."
  Device: usb 0x9734 "ORTEK KH12 USB Hub"
  Revision: "1.10"
  Driver: "hub"
  Driver Modules: "usbcore"
  Speed: 12 Mbps
  Module Alias: "usb:v05A4p9734d0110dc09dsc00dp00ic09isc00ip00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #6 (Hub)

08: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  Unique ID: U7rr.QkYv4c0j9L9
  Parent ID: FKGF.0j9+vWlqL56
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:2.0
  SysFS BusID: 2-1.6:2.0
  Hardware Class: unknown
  Model: "Midiman FastTrack Pro"
  Hotplug: USB
  Vendor: usb 0x0763 "Midiman"
  Device: usb 0x2012 "FastTrack Pro"
  Revision: "1.00"
  Driver: "snd-usb-audio"
  Driver Modules: "snd_usb_audio"
  Speed: 12 Mbps
  Module Alias: "usb:v0763p2012d0100dc00dsc00dp00ic01isc01ip00"
  Driver Info #0:
    Driver Status: snd_usb_audio is active
    Driver Activation Cmd: "modprobe snd_usb_audio"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #6 (Hub)

09: USB 00.0: 10800 Keyboard
  [Created at usb.122]
  Unique ID: ItRS.B5VatMU7+DB
  Parent ID: Bgjr.D3cPvvGdtc3
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.1/2-1.5.1:1.0
  SysFS BusID: 2-1.5.1:1.0
  Hardware Class: keyboard
  Model: "Ortek USB Hub/Keyboard"
  Hotplug: USB
  Vendor: usb 0x05a4 "Ortek Technology, Inc."
  Device: usb 0x9734 "USB Hub/Keyboard"
  Revision: "1.10"
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/event3
  Device Files: /dev/input/event3, /dev/input/by-id/usb-ORTEK_USB_Hub_Keyboard-event-kbd, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1.5.1:1.0-event-kbd
  Device Number: char 13:67
  Speed: 12 Mbps
  Module Alias: "usb:v05A4p9734d0110dc00dsc00dp00ic03isc01ip01"
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #7 (Hub)

10: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: k+3d.sGFjMJXxze9
  Parent ID: Bgjr.D3cPvvGdtc3
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.2/2-1.5.2:1.0
  SysFS BusID: 2-1.5.2:1.0
  Hardware Class: mouse
  Model: "Microsoft Wheel Mouse Optical"
  Hotplug: USB
  Vendor: usb 0x045e "Microsoft Corp."
  Device: usb 0x0040 "Wheel Mouse Optical"
  Revision: "3.00"
  Compatible to: int 0x0210 0x0013
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse0)
  Device Files: /dev/input/mice, /dev/input/mouse0, /dev/input/event4, /dev/input/by-id/usb-Microsoft_Microsoft_3-Button_Mouse_with_IntelliEye_TM_-event-mouse, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1.5.2:1.0-event-mouse, /dev/input/by-id/usb-Microsoft_Microsoft_3-Button_Mouse_with_IntelliEye_TM_-mouse, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1.5.2:1.0-mouse
  Device Number: char 13:63 (char 13:32)
  Speed: 1.5 Mbps
  Module Alias: "usb:v045Ep0040d0300dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    Buttons: 3
    Wheels: 1
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #7 (Hub)

11: USB 00.0: 10503 USB Mouse
  [Created at usb.122]
  Unique ID: cGKy.mo_v_NZH+OE
  Parent ID: Bgjr.D3cPvvGdtc3
  SysFS ID: /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5.4/2-1.5.4:1.0
  SysFS BusID: 2-1.5.4:1.0
  Hardware Class: mouse
  Model: "Cirque USB GlidePoint"
  Hotplug: USB
  Vendor: usb 0x0488 "Cirque Corp."
  Device: usb 0x0010 "USB GlidePoint"
  Revision: "1.30"
  Compatible to: int 0x0210 0x0013
  Driver: "usbhid"
  Driver Modules: "usbhid"
  Device File: /dev/input/mice (/dev/input/mouse1)
  Device Files: /dev/input/mice, /dev/input/mouse1, /dev/input/event5, /dev/input/by-id/usb-Cirque_Corporation_USB_GlidePoint-event-mouse, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1.5.4:1.0-event-mouse, /dev/input/by-id/usb-Cirque_Corporation_USB_GlidePoint-mouse, /dev/input/by-path/pci-0000:00:1d.0-usb-0:1.5.4:1.0-mouse
  Device Number: char 13:63 (char 13:33)
  Speed: 1.5 Mbps
  Module Alias: "usb:v0488p0010d0130dc00dsc00dp00ic03isc01ip02"
  Driver Info #0:
    Buttons: 3
    Wheels: 1
    XFree86 Protocol: explorerps/2
    GPM Protocol: exps2
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #7 (Hub)


dmesg | grep video
[    0.560974] pci 0000:00:02.0: Boot video device

---

### Post by Bucky Ball on 2013-01-08
***Moved to own thread***

---

### Post by dewdrop_world on 2013-01-08
It turns out to be a super-boneheaded mistake on my part.

There's a little blue webcam icon on my laptop's F6 key. After pressing Fn+F6, /dev/video0 magically reappeared and all the software is working with it as well.

I don't remember switching it off. It's possible that I did it and forgot. It's also possible that something glitched during a startup or shutdown sequence and the BIOS or something decided that the camera should be off. I've definitely seen that behavior in the past with WiFi -- cold boot, WiFi isn't working, hit Fn+F8 and then it's fine.

(Since I'm mainly a software person, if there's a problem, I tend to assume it's the software's fault... which is fine most of the time, except when it isn't the software...)

Anyway, it's all working now.

It's also entirely possible that this would solve xap1234's problem (from which this thread was split). I'll post an update in that thread also.

---

### Post by Bucky Ball on 2013-01-09
> **dewdrop_world said:**
> 
It's also entirely possible that this would solve xap1234's problem (from which this thread was split). I'll post an update in that thread also.

Good work. Glad to see it's all sorted and hopefully that will be of help in the other thread. ;)

---

