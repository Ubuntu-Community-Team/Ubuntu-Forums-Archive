---
title: "Custom Audio Channel Routing"
date: 2011-01-28
forum: Multimedia Software
---

### Post by linuxyogi on 2011-01-28
Hi, 

The front panel headphone jack (female) got damaged recently when I accidentally tripped over my headphone cord while it was connected to the front panel jack.

So, I was thinking is there a way to tweak pulse in such way that it outputs the L & R channels simultaneously through 

rear line out & rear line in  

or

rear line out & rear mic in

If possible I will just connect my headphone using any one of them.

Muting of the line out jack upon jack insertion is no issue, I will just disconnects the AC adapter of my 2.1.

OS: Maverick 64
Audio Hardware: ```
hwinfo --sound
> hal.1: read hal dataprocess 3213: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
17: PCI 07.0: 0403 Audio device                                 
  [Created at pci.318]
  Unique ID: M71A.uqJCkV9DszA
  SysFS ID: /devices/pci0000:00/0000:00:07.0
  SysFS BusID: 0000:00:07.0
  Hardware Class: sound
  Model: "nVidia MCP67 High Definition Audio"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x055c "MCP67 High Definition Audio"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x8290 
  Revision: 0xa1
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xdbff8000-0xdbffbfff (rw,non-prefetchable)
  IRQ: 21 (588 events)
  Module Alias: "pci:v000010DEd0000055Csv00001043sd00008290bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

``````
cat /etc/modprobe.d/alsa-base.conf | grep intel
options snd-intel8x0m index=-
``````
dpkg -l | grep "alsa"
ii  alsa-base                             1.0.23+dfsg-1ubuntu4                              ALSA driver configuration files
ii  alsa-utils                            1.0.23-2ubuntu3.4                                 Utilities for configuring and using ALSA
ii  bluez-alsa                            4.69-0ubuntu2                                     Bluetooth audio support
ii  gstreamer0.10-alsa                    0.10.30-2                                         GStreamer plugin for ALSA

```

---

