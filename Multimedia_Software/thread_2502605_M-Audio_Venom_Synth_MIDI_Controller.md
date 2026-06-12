---
title: "M-Audio Venom Synth MIDI Controller"
date: 2024-11-21
forum: Multimedia Software
---

### Post by aaronrohrbacher on 2024-11-21
Ahoy musician geeks! I've grown my nerd beard by an entire inch these last couple days trying to get my (quite) old M-Audio Venom synth to use MIDI on linux. Certainly incompatible or broken hardware is involved, becasue as soon as I power up the synth, my machine bogs way down, and the below logs follow this pattern repeatedly. In fact, sometimes the machine won't boot at all if I have the synth on during boot. BUT, what's weird to me is that Windows still seems to be able to reign 'er in, and it works swimmingly under uncle Billy's watch, when used along with the drivers and software here: [http://www.venom-synth.com/installers/](http://www.venom-synth.com/installers/)  

No luck with Wine or VMs either, not surprisingly. Anybody find a solution? This is probably a good test to see if I'm the last person standing still trying to spin this synth up! I have an old-school MIDI interface to USB coming this afternoon, so who knows, maybe that'll squeeze another year outta this thing!

Ubuntu Studio 24.10, also tried on my Arch box and again on AVLinux (debian stable based I think). Same errors regardless.
2018 i7 (I forget which chip) Razer Blade (but also on some ol' AMD HP).

```

[FONT=monospace][COLOR=#000000]Nov 21 07:00:37 studio kernel: usb 1-11.3.2: new full-speed USB device number 14 using xhci_hcd[/COLOR]
Nov 21 07:00:37 studio kernel: usb 1-11.3.2: New USB device found, idVendor=0763, idProduct=2084, bcdDevice=11
.44
Nov 21 07:00:37 studio kernel: usb 1-11.3.2: New USB device strings: Mfr=2, Product=3, SerialNumber=0
Nov 21 07:00:37 studio kernel: usb 1-11.3.2: Product: Venom
Nov 21 07:00:37 studio kernel: usb 1-11.3.2: Manufacturer: M-Audio
Nov 21 07:00:42 studio kernel: [COLOR=#FF5454]**usb 1-11.3.2: 1:1: cannot get freq at ep 0x2**[/COLOR]
Nov 21 07:01:03 studio kernel: [COLOR=#FF5454]**usb 1-11.3.2: 2:1: cannot set freq 44100 to ep 0x84**[/COLOR]
Nov 21 07:01:08 studio kernel: usb 1-11.3.2: Quirk or no altset; falling back to MIDI 1.0
Nov 21 07:01:37 studio systemd-udevd[569]: [COLOR=#D7D75F]**1-11.3.2: Worker [7968] processing SEQNUM=5082 is taking a long tim**[/COLOR]
e
Nov 21 07:01:54 studio kernel: [COLOR=#D7D75F]**usb 1-11.3.2: 6:0: failed to get current value for ch 0 (-110)**[/COLOR]
Nov 21 07:02:04 studio kernel: [COLOR=#FF5454]**usb 1-11.3.2: 6:0: cannot get min/max values for control 2 (id 6)**[/COLOR]
Nov 21 07:02:09 studio kernel: [COLOR=#D7D75F]**usb 1-11.3.2: 5:0: failed to get current value for ch 0 (-110)**[/COLOR]
Nov 21 07:02:35 studio mtp-probe[7974]: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:14.0/usb1/
1-11/1-11.3/1-11.3.2"
Nov 21 07:02:35 studio mtp-probe[7974]: bus: 1, device: 14 was not an MTP device
Nov 21 07:02:36 studio colord-sane[7987]: [COLOR=#FF5454]**io/hpmud/musb.c 2102: Invalid usb_open: Permission denied**[/COLOR]
Nov 21 07:02:40 studio kernel: [COLOR=#FF5454]**usb 1-11.3.2: 6:0: cannot get min/max values for control 2 (id 6)**[/COLOR]
Nov 21 07:02:45 studio kernel: [COLOR=#FF5454]**usb 1-11.3.2: 6:0: cannot get min/max values for control 2 (id 6)**[/COLOR]

[/FONT]
```

---

