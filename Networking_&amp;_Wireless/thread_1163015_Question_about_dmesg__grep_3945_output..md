---
title: "Question about dmesg | grep 3945 output."
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by bwolf1 on 2009-05-18
I have an issue where my wireless cuts every time my bandwidth usage gets anywhere above bare minimum. Below are the results of me running "dmesg | grep 3945" twice, once when the wireless is working fine, and another after it has cut out (and before I reconnect it via the network manager). There are some obvious differences between the two, but I don't understand exactly what the information means, or how it might help me solve my problem.

Thanks in advance for the help!

First, the output of dmesg | grep 3945 when the wireless is working:

```

[    9.632281] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    9.632283] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    9.632380] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.632394] iwl3945 0000:0b:00.0: setting latency timer to 64
[    9.632471] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    9.638969] iwl3945 0000:0b:00.0: irq 2297 for MSI/MSI-X
[    9.697472] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.698077] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.083533] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   71.775543] iwl3945: Radio Frequency Kill Switch is On:
[   76.092635] iwl3945: MAC is in deep sleep!
[   76.092737] iwl3945: MAC is in deep sleep!
[   76.092826] iwl3945: MAC is in deep sleep!

```Now the output of dmesg | grep 3945 after I recreate the problem by simply clicking on a YouTube video or two, to increase bandwidth usage:

```

[    9.632281] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[    9.632283] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[    9.632380] iwl3945 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.632394] iwl3945 0000:0b:00.0: setting latency timer to 64
[    9.632471] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[    9.638969] iwl3945 0000:0b:00.0: irq 2297 for MSI/MSI-X
[    9.697472] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[    9.698077] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   20.083533] iwl3945 0000:0b:00.0: firmware: requesting iwlwifi-3945-1.ucode
[   71.775543] iwl3945: Radio Frequency Kill Switch is On:
[   76.092635] iwl3945: MAC is in deep sleep!
[   76.092737] iwl3945: MAC is in deep sleep!
[   76.092826] iwl3945: MAC is in deep sleep!
[ 9160.108462] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[ 9160.108478] iwl3945: Error Reply type 0x00000005 cmd REPLY_TX (0x1C) seq 0x0276 ser 0x0000004B
[ 9160.112133] iwl3945: Can't stop Rx DMA.

```I'm running:

```

lsb_release -d

Description:    Ubuntu 9.04

``````

uname -mr

2.6.28-11-generic i686

```More information can be found about my system and my wireless problem in [this thread]("http://ubuntuforums.org/showthread.php?t=1161153"), if you are curious.

---

### Post by chili555 on 2009-05-18
I am shocked that it works at all!> iwl3945: Radio Frequency Kill Switch is On:Please open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open and manipulate the wireless switch or key combination and see if you can get the kernel to recognize that the kill switch is off. Then I'd suggest you repeat your YouTube test.

This is actually a bit amazing.

---

### Post by bwolf1 on 2009-05-18
Thanks for the reply. 

Here's the log tail of me toggling the switch off and on a couple times then, hitting YouTube to increase bandwidth and recreate the problem, then hitting iGoogle just to verify that it is still broken at that point even with a lower bandwidth connection.

```

brian@brian-laptop:~$ sudo tail -f /var/log/messages
May 18 09:30:53 brian-laptop kernel: [10057.654778] usb 7-2.3: new full speed USB device using uhci_hcd and address 21
May 18 09:30:53 brian-laptop kernel: [10057.784132] usb 7-2.3: configuration #1 chosen from 1 choice
May 18 09:30:53 brian-laptop kernel: [10057.793577] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input21
May 18 09:30:54 brian-laptop kernel: [10057.825222] generic-usb 0003:0A5C:4503.000B: input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3/input0
May 18 09:30:55 brian-laptop kernel: [10058.866198] Registered led device: iwl-phy0:radio
May 18 09:30:55 brian-laptop kernel: [10058.866239] Registered led device: iwl-phy0:assoc
May 18 09:30:55 brian-laptop kernel: [10058.866275] Registered led device: iwl-phy0:RX
May 18 09:30:55 brian-laptop kernel: [10058.866310] Registered led device: iwl-phy0:TX
May 18 09:30:55 brian-laptop kernel: [10058.878641] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 18 09:31:00 brian-laptop kernel: [10063.982580] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 18 09:31:18 brian-laptop kernel: [10082.408254] iwl3945: Radio Frequency Kill Switch is On:
May 18 09:31:18 brian-laptop kernel: [10082.408260] Kill switch must be turned off for wireless networking to work.
May 18 09:31:18 brian-laptop kernel: [10082.608277] usb 7-2: USB disconnect, address 18
May 18 09:31:18 brian-laptop kernel: [10082.608284] usb 7-2.1: USB disconnect, address 19
May 18 09:31:19 brian-laptop kernel: [10082.871022] usb 7-2.2: USB disconnect, address 20
May 18 09:31:19 brian-laptop kernel: [10082.897534] usb 7-2.3: USB disconnect, address 21
May 18 09:31:24 brian-laptop kernel: [10088.224104] usb 7-2: new full speed USB device using uhci_hcd and address 22
May 18 09:31:24 brian-laptop kernel: [10088.393188] usb 7-2: configuration #1 chosen from 1 choice
May 18 09:31:24 brian-laptop kernel: [10088.394452] hub 7-2:1.0: USB hub found
May 18 09:31:24 brian-laptop kernel: [10088.396377] hub 7-2:1.0: 3 ports detected
May 18 09:31:24 brian-laptop kernel: [10088.677539] usb 7-2.1: new full speed USB device using uhci_hcd and address 23
May 18 09:31:24 brian-laptop kernel: [10088.801844] usb 7-2.1: configuration #1 chosen from 1 choice
May 18 09:31:25 brian-laptop kernel: [10088.898744] usb 7-2.2: new full speed USB device using uhci_hcd and address 24
May 18 09:31:25 brian-laptop kernel: [10089.049924] usb 7-2.2: configuration #1 chosen from 1 choice
May 18 09:31:25 brian-laptop kernel: [10089.056322] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input22
May 18 09:31:25 brian-laptop kernel: [10089.081767] generic-usb 0003:0A5C:4502.000C: input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2/input0
May 18 09:31:25 brian-laptop kernel: [10089.172051] usb 7-2.3: new full speed USB device using uhci_hcd and address 25
May 18 09:31:25 brian-laptop kernel: [10089.304988] usb 7-2.3: configuration #1 chosen from 1 choice
May 18 09:31:25 brian-laptop kernel: [10089.337607] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input23
May 18 09:31:25 brian-laptop kernel: [10089.360363] generic-usb 0003:0A5C:4503.000D: input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3/input0
May 18 09:31:26 brian-laptop kernel: [10089.867814] Registered led device: iwl-phy0:radio
May 18 09:31:26 brian-laptop kernel: [10089.868333] Registered led device: iwl-phy0:assoc
May 18 09:31:26 brian-laptop kernel: [10089.868791] Registered led device: iwl-phy0:RX
May 18 09:31:26 brian-laptop kernel: [10089.870275] Registered led device: iwl-phy0:TX
May 18 09:31:26 brian-laptop kernel: [10089.886713] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 18 09:31:26 brian-laptop kernel: [10089.916963] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 18 09:31:45 brian-laptop kernel: [10108.845836] iwl3945: Radio Frequency Kill Switch is On:
May 18 09:31:45 brian-laptop kernel: [10108.845842] Kill switch must be turned off for wireless networking to work.
May 18 09:31:45 brian-laptop kernel: [10108.896255] usb 7-2: USB disconnect, address 22
May 18 09:31:45 brian-laptop kernel: [10108.896262] usb 7-2.1: USB disconnect, address 23
May 18 09:31:45 brian-laptop kernel: [10109.151942] usb 7-2.2: USB disconnect, address 24
May 18 09:31:45 brian-laptop kernel: [10109.180644] usb 7-2.3: USB disconnect, address 25
May 18 09:31:51 brian-laptop kernel: [10115.556087] usb 7-2: new full speed USB device using uhci_hcd and address 26
May 18 09:31:51 brian-laptop kernel: [10115.735998] usb 7-2: configuration #1 chosen from 1 choice
May 18 09:31:51 brian-laptop kernel: [10115.738228] hub 7-2:1.0: USB hub found
May 18 09:31:51 brian-laptop kernel: [10115.744416] hub 7-2:1.0: 3 ports detected
May 18 09:31:52 brian-laptop kernel: [10116.038166] usb 7-2.1: new full speed USB device using uhci_hcd and address 27
May 18 09:31:52 brian-laptop kernel: [10116.168318] usb 7-2.1: configuration #1 chosen from 1 choice
May 18 09:31:52 brian-laptop kernel: [10116.257206] usb 7-2.2: new full speed USB device using uhci_hcd and address 28
May 18 09:31:52 brian-laptop kernel: [10116.387386] usb 7-2.2: configuration #1 chosen from 1 choice
May 18 09:31:52 brian-laptop kernel: [10116.400726] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input24
May 18 09:31:52 brian-laptop kernel: [10116.421205] generic-usb 0003:0A5C:4502.000E: input,hidraw1: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2/input0
May 18 09:31:52 brian-laptop kernel: [10116.501317] usb 7-2.3: new full speed USB device using uhci_hcd and address 29
May 18 09:31:52 brian-laptop kernel: [10116.640294] usb 7-2.3: configuration #1 chosen from 1 choice
May 18 09:31:52 brian-laptop kernel: [10116.663423] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input25
May 18 09:31:52 brian-laptop kernel: [10116.668818] generic-usb 0003:0A5C:4503.000F: input,hidraw2: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3/input0
May 18 09:31:57 brian-laptop kernel: [10120.866161] Registered led device: iwl-phy0:radio
May 18 09:31:57 brian-laptop kernel: [10120.866244] Registered led device: iwl-phy0:assoc
May 18 09:31:57 brian-laptop kernel: [10120.866280] Registered led device: iwl-phy0:RX
May 18 09:31:57 brian-laptop kernel: [10120.866315] Registered led device: iwl-phy0:TX
May 18 09:31:57 brian-laptop kernel: [10120.881967] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 18 09:31:57 brian-laptop kernel: [10120.915244] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May 18 09:33:04 brian-laptop kernel: [10188.683535] Registered led device: iwl-phy0:radio
May 18 09:33:04 brian-laptop kernel: [10188.683549] Registered led device: iwl-phy0:assoc
May 18 09:33:04 brian-laptop kernel: [10188.683560] Registered led device: iwl-phy0:RX
May 18 09:33:04 brian-laptop kernel: [10188.683621] Registered led device: iwl-phy0:TX
^C
brian@brian-laptop:~$ 

```

---

### Post by Light-kun on 2012-05-18
Hi.
have similar problem with :
"iwl3945: Intel(R) PRO/Wireless 3945ABG/BG"

rmmod+modprobe did this (the interesting part):
iwl3945 0000:06:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
iwl3945 0000:06:00.0: EEPROM not found, EEPROM_GP=0xffffffff
iwl3945 0000:06:00.0: Unable to init EEPROM
iwl3945 0000:06:00.0: PCI INT A disabled
iwl3945: probe of 0000:06:00.0 failed with error -2

I have  Ubuntu 12.04 with 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux

Should I start another topic?

---

