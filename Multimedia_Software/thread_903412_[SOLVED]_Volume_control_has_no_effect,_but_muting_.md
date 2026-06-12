---
title: "[SOLVED] Volume control has no effect, but muting PCM works."
date: 2008-08-28
forum: Multimedia Software
---

### Post by fahadsadah on 2008-08-28
Hello all.

I am using Kubuntu Hardy + KDE4. App specific volume controls work, but kmix doesn't - for any channel. Muting PCM does stop sound, but that's absolutely it.

hwinfo --sound output:```
11: PCI 1f.5: 0401 Multimedia audio controller
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_24d5
  Unique ID: W60f.x8s5HMdIibD
  SysFS ID: /devices/pci0000:00/0000:00:1f.5
  SysFS BusID: 0000:00:1f.5
  Hardware Class: sound
  Model: "ASRock In 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x24d5 "82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller"
  SubVendor: pci 0x1849 "ASRock Incorporation"
  SubDevice: pci 0x9761
  Revision: 0x02
  Driver: "Intel ICH"
  Driver Modules: "snd_intel8x0"
  I/O Ports: 0xd800-0xd8ff (rw)
  I/O Ports: 0xdc00-0xdc3f (rw)
  Memory Range: 0xfebff800-0xfebff9ff (rw,non-prefetchable)
  Memory Range: 0xfebff400-0xfebff4ff (rw,non-prefetchable)
  IRQ: 21 (43905 events)
  Module Alias: "pci:v00008086d000024D5sv00001849sd00009761bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_intel8x0 is active
    Driver Activation Cmd: "modprobe snd_intel8x0"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

In alsamixer, PCM works completely. Master doesn't, but I don't care.

Thank you

---

### Post by fahadsadah on 2008-08-30
Nevermind, I fixed it somehow. I think it was something to do with the motherboard getting too hot (onboard sound).

---

