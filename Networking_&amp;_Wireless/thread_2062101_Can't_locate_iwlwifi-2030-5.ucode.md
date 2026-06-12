---
title: "Can't locate iwlwifi-2030-5.ucode"
date: 2012-09-24
forum: Networking &amp; Wireless
---

### Post by caeso on 2012-09-24
I can't get my wireless card to load.. it's driving me nuts!

Below is a 'dmesg | grep iw'

```
[    3.774675] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    3.774681] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    3.774767] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.774782] iwlagn 0000:02:00.0: setting latency timer to 64
[    3.774829] iwlagn 0000:02:00.0: Detected 2000 Series 2x2 BGN/BT, REV=0xC8
[    3.793232] iwlagn 0000:02:00.0: device EEPROM VER=0x81c, CALIB=0x6
[    3.793239] iwlagn 0000:02:00.0: Device SKU: 0X9
[    3.793244] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[    3.794259] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    3.796580] iwlagn 0000:02:00.0: irq 44 for MSI/MSI-X
[    4.002762] iwlagn 0000:02:00.0: request for firmware file 'iwlwifi-2030-5.ucode' failed.
[    4.002770] iwlagn 0000:02:00.0: no suitable firmware found!
[    4.002899] iwlagn 0000:02:00.0: PCI INT A disabled

```

For some reason I can't get this to work at all. It looks like it's loaded, then tries to load the firmware file again and can't find it? I don't understand. 

Nothing shows up when I do iwconfig obviously. The lspci is:

```
02:00.0 Network controller: Intel Corporation Device 0887 (rev c4)
	Subsystem: Intel Corporation Device 4062
	Flags: fast devsel, IRQ 17
	Memory at c0500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel modules: iwlagn

```

I am on kernel 3.0.0-12-generic 64bit.

This is crucial and driving me nuts!

Any help would be appreciated!

(Did I say nuts?)

---

### Post by okanagansage on 2013-01-14
You asked about this almost 4 months ago, but for what it's worth...

If you use 
```
lspci -nn
```
you'll get a list of your pci-connected hardware (with both the textual and numerical ID's). 
If you use ```
lspci -nn | grep -i Audio
``` it'll just show you the info for your audio device instead of the whole list. You may or may not have to capitalize the first letter of the work audio in that command.
In your case the numerical ID is 8086:0887 .

From the output you gave for the 'dmesg | grep iw' command, it says > 62] iwlagn 0000:02:00.0: request for firmware file 'iwlwifi-2030-5.ucode' failed
Unfortunately, I can't tell you where to find iwlwifi-2030-5.ucode . 
A similar piece of firmware, iwlwifi-2030-6.ucode can be extracted from the folder iwlwifi-2030-ucode-18.168.6.1.tgz which can be found at
[http://wireless.kernel.org/en/users/Drivers/iwlwifi?n=downloads]("http://wireless.kernel.org/en/users/Drivers/iwlwifi?n=downloads")
but since that is not the same firmware it probably wouldn't work (I'm guessing). 
If you do find the one you want, copy it into the system folder /lib/firmware. If your using the terminal you could navigate to the folder where you've extracted iwlwifi-2030-5.ucode and use the command ```
sudo cp /lib/firmware
``` Then reboot. I've read this worked for others. I did it in a different (ubuntu-based) distribution and then I could see available hardware with the iwconfig command (wlan0 was showing info). I also had to open WICD  and in the wireless interface field (the space in the gui to enter info) I had to put wlan0 . That would connect my wifi but it would drop out once in a while. I could reconnect it each time but it was a pain.

Actually, I'm looking for iwlwifi-2030-5.ucode as well. If you find it please post here where to get it.

---

### Post by okanagansage on 2013-01-14
[http://tthtlc.wordpress.com/2012/09/15/how-i-found-my-missing-network-wifi-drivers/]("http://tthtlc.wordpress.com/2012/09/15/how-i-found-my-missing-network-wifi-drivers/")
At the above link the person says that they were getting the request for iwlwifi-2030-5.ucode, then (s)he says they found the "2030 ucode", reloaded the iwlwifi kernel module (presumably with modprobe iwlwifi)
> and doing a “ifconfig” wlan got detected by the router and setup hence:
wlan0 Link encap:Ethernet HWaddr 68:5d:43:02:11:bf
inet addr:10.10.1.160 Bcast:10.10.1.255 Mask:255.255.255.0
inet6 addr: fe80::6a5d:43ff:fe02:11bf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:3041 errors:0 dropped:0 overruns:0 frame:0
TX packets:1932 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2525361 (2.5 MB) TX bytes:391475 (391.4 KB)
It doesn't specifically say if the -5 or -6 firmware was used. I posted a question on their blog to find out. If I get an answer I'll post it here.

---

