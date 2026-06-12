---
title: "Twinhan AD-SE200 driver"
date: 2009-05-14
forum: Multimedia Software
---

### Post by gewitty on 2009-05-14
I have a Twinhan AD-SE200 satellite card installed on a new PC running 64 bit Jaunty.

I'm looking for a driver, so that I can use the card with VLC or Mplayer. On the Twinhan site, they only have a Linux driver for the AD-SP200 and I'm not sure if this will work with the AD-SE200.

Can anyone tell me if this driver is appropriate, or if not, where I can find one which will work?

---

### Post by megacrypto on 2009-08-31
i got the same card, did you have any luck?

---

### Post by gewitty on 2009-09-01
> **megacrypto said:**
> i got the same card, did you have any luck?

Not yet. I sent a couple of emails to the manufacturer, but they didn't reply and I've had no other responses from various forums.

Not sure what to try next :(

---

### Post by megacrypto on 2009-09-01
I found a few things but no luck yet in getting it working:
1. the drivers page on Twinhan's website, at the bottom they have linux drivers. I tried to follow the setup steps but they do not work ([http://www.twinhan.com/download_driver&software.asp](http://www.twinhan.com/download_driver&software.asp))

2. this here is someone who compiled the kernel with a patched driver and got it to work ([http://www.gnulab.org/node/63](http://www.gnulab.org/node/63))

I must say that the twinhan drivers atleast made my ubuntu see the recognize the card:
```

mylin@homeserver:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP78S [GeForce 8200] High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:09.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:09.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:09.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)


```

---

