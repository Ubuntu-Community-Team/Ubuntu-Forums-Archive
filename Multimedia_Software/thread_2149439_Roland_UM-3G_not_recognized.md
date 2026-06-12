---
title: "Roland UM-3G not recognized"
date: 2013-05-28
forum: Multimedia Software
---

### Post by nsfx on 2013-05-28
The Roland UM-3G is a USB midi interface. I have this device working on other machines running earlier versions of the kernel. Getting it working on those machines required applying [this patch]("https://kernel.googlesource.com/pub/scm/linux/kernel/git/pjt/linsched/+/927c9423dd5f2d1c0b93d5e694ab84b4a5559713%5E%21/#F0") to the kernel. Now I'm trying to get it working with another machine running Raring. I notice the Raring's kernel ships with this patch already applied so I was expecting for it to work out of the box, however I'm getting errors:

```
May 28 18:31:37 as1xc kernel: [138442.979830] usb 1-1.2: USB disconnect, device number 18
May 28 18:31:37 as1xc kernel: [138442.979845] usb 1-1.2.1: USB disconnect, device number 19
May 28 18:31:40 as1xc kernel: [138446.249710] usb 1-1.2: new full-speed USB device number 20 using ehci-pci
May 28 18:31:40 as1xc kernel: [138446.342994] usb 1-1.2: New USB device found, idVendor=0451, idProduct=2036
May 28 18:31:40 as1xc kernel: [138446.343009] usb 1-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
May 28 18:31:40 as1xc kernel: [138446.343018] usb 1-1.2: Product: General Purpose USB Hub
May 28 18:31:40 as1xc kernel: [138446.344707] hub 1-1.2:1.0: USB hub found
May 28 18:31:40 as1xc kernel: [138446.345115] hub 1-1.2:1.0: 3 ports detected
May 28 18:31:41 as1xc kernel: [138446.617623] usb 1-1.2.1: new full-speed USB device number 21 using ehci-pci
May 28 18:31:41 as1xc kernel: [138446.712280] usb 1-1.2.1: New USB device found, idVendor=0582, idProduct=0108
May 28 18:31:41 as1xc kernel: [138446.712295] usb 1-1.2.1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 28 18:31:41 as1xc kernel: [138446.712304] usb 1-1.2.1: Product: UM-3G
May 28 18:31:41 as1xc kernel: [138446.712311] usb 1-1.2.1: Manufacturer: Roland
May 28 18:31:41 as1xc kernel: [138446.713755] MIDIStreaming interface descriptor not found
May 28 18:31:41 as1xc kernel: [138446.714036] init_device failed: MIDI 1-0: seq-midi
May 28 18:31:41 as1xc mtp-probe: checking bus 1, device 21: "/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2.1"
May 28 18:31:41 as1xc mtp-probe: bus: 1, device: 21 was not an MTP device
May 28 18:31:41 as1xc pulseaudio[2140]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
May 28 18:31:41 as1xc pulseaudio[2140]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="usb-Roland_UM-3G-00-UM3G" card_name="alsa_card.usb-Roland_UM-3G-00-UM3G" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```


Any tips? Thanks.

---

