---
title: "Actiontec 802AIN USB Wireless thumb/dongle"
date: 2012-04-24
forum: Networking &amp; Wireless
---

### Post by mizifih on 2012-04-24
**Hi everyone!**

I have this USB thumb/dongle for N Wireless network but can't make it work on Ubuntu (linux in general).

_It says_:

[LIST]
[*]Model: 802AIN
[*]FCC ID: LNQ802AIN
[/LIST]
[CENTER][IMG]http://ubuntuforums.org/images/editor/insertimage.gif[/IMG] [http://i45.tinypic.com/j0d1rt.jpg](http://i45.tinypic.com/j0d1rt.jpg) [IMG]http://ubuntuforums.org/images/editor/insertimage.gif[/IMG]
thumb/dongle picture
[/CENTER]
[LEFT]
Product Page: [http://www.actiontec.com/support/product_details.php?pid=196&typ=doc](http://www.actiontec.com/support/product_details.php?pid=196&typ=doc)

Ubuntu doesn't recognizes it just by plugging it or after a full restart (plugged then restarted computer).

Can anyone help me, I can't believe I'll need to buy another one.

If so, what model you guys recommend that will for sure work with major Linux Distributions (mostly, but not only Ubuntu, also freeBSD, RedHat...) just out of the box?

**Thanks for this awesome community support forum!**
[/LEFT]

---

### Post by nothingspecial on 2012-04-25
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2012-04-25
Please remove the device from the USB slot. Open a terminal and run: ```
sudo tail -f /var/log/syslog
```Insert the device. Watch the terminal to see what the system says when it's inserted. We suspect, but hope it is not seen as a storage device. Get out of tail with Ctrl+c. Now run and post:```
lsusb
```Thanks.

---

### Post by mizifih on 2012-04-25
> **chili555 said:**
> Please remove the device from the USB slot. Open a terminal and run: ```
sudo tail -f /var/log/syslog
```Insert the device. Watch the terminal to see what the system says when it's inserted. We suspect, but hope it is not seen as a storage device. Get out of tail with Ctrl+c. Now run and post:```
lsusb
```Thanks.

[CENTER][SIZE=2][COLOR=Black]_**Thank you very much for you reply!**_
[/COLOR][/SIZE][/CENTER]
 
About it being recognized as a storage device, that actually worried me a little. When I plug it on a Windows 7 machine, it kinda emulates a CD/DVD drive and the Win drivers are on it. Or it, at lease, has a storage part somehow. Don't know how to explain that.

**Here is tail output:** ```
Apr 25 12:21:08 Buttman-ubuntu kernel: [79326.489675] usb 1-2: Ejecting virtual installer media...
Apr 25 12:21:08 Buttman-ubuntu kernel: [79326.490661] usb 1-2: USB disconnect, device number 41
Apr 25 12:21:09 Buttman-ubuntu kernel: [79327.320085] usb 1-2: new high speed USB device number 42 using ehci_hcd
Apr 25 12:21:09 Buttman-ubuntu mtp-probe: checking bus 1, device 42: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:21:09 Buttman-ubuntu kernel: [79327.534179] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:21:10 Buttman-ubuntu kernel: [79328.532075] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:21:10 Buttman-ubuntu kernel: [79328.532090] Failed to initialize the device
Apr 25 12:21:10 Buttman-ubuntu kernel: [79328.541353] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:21:10 Buttman-ubuntu mtp-probe: bus: 1, device: 42 was not an MTP device
Apr 25 12:21:10 Buttman-ubuntu kernel: [79328.596526] usb 1-2: USB disconnect, device number 42
_**Apr 25 12:22:59 Buttman-ubuntu kernel: [79437.380176] usb 1-2: new high speed USB device number 43 using ehci_hcd**_
Apr 25 12:22:59 Buttman-ubuntu kernel: [79437.513571] usb-storage 1-2:1.0: device ignored
Apr 25 12:22:59 Buttman-ubuntu kernel: [79437.513631] usb 1-2: Ejecting virtual installer media...
Apr 25 12:22:59 Buttman-ubuntu kernel: [79437.514647] usb 1-2: USB disconnect, device number 43
Apr 25 12:22:59 Buttman-ubuntu mtp-probe: checking bus 1, device 43: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:22:59 Buttman-ubuntu mtp-probe: bus: 1, device: 43 was not an MTP device
Apr 25 12:23:00 Buttman-ubuntu kernel: [79438.344075] usb 1-2: new high speed USB device number 44 using ehci_hcd
Apr 25 12:23:00 Buttman-ubuntu mtp-probe: checking bus 1, device 44: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:00 Buttman-ubuntu kernel: [79438.558922] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:01 Buttman-ubuntu kernel: [79439.556102] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:01 Buttman-ubuntu kernel: [79439.556121] Failed to initialize the device
Apr 25 12:23:01 Buttman-ubuntu kernel: [79439.565340] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:01 Buttman-ubuntu kernel: [79439.676117] usb 1-2: reset high speed USB device number 44 using ehci_hcd
Apr 25 12:23:01 Buttman-ubuntu kernel: [79439.808336] usb 1-2: device firmware changed
Apr 25 12:23:01 Buttman-ubuntu kernel: [79439.808547] usb 1-2: USB disconnect, device number 44
Apr 25 12:23:02 Buttman-ubuntu kernel: [79439.924120] usb 1-2: new high speed USB device number 45 using ehci_hcd
Apr 25 12:23:02 Buttman-ubuntu mtp-probe: bus: 1, device: 44 was not an MTP device
Apr 25 12:23:02 Buttman-ubuntu kernel: [79440.057723] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:02 Buttman-ubuntu kernel: [79440.057781] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:02 Buttman-ubuntu kernel: [79440.058711] usb 1-2: USB disconnect, device number 45
Apr 25 12:23:02 Buttman-ubuntu mtp-probe: checking bus 1, device 45: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:02 Buttman-ubuntu mtp-probe: bus: 1, device: 45 was not an MTP device
Apr 25 12:23:02 Buttman-ubuntu kernel: [79440.888119] usb 1-2: new high speed USB device number 46 using ehci_hcd
Apr 25 12:23:03 Buttman-ubuntu mtp-probe: checking bus 1, device 46: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:03 Buttman-ubuntu kernel: [79441.102371] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.100046] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.100063] Failed to initialize the device
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.109419] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.220095] usb 1-2: reset high speed USB device number 46 using ehci_hcd
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.352316] usb 1-2: device firmware changed
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.352515] usb 1-2: USB disconnect, device number 46
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.468149] usb 1-2: new high speed USB device number 47 using ehci_hcd
Apr 25 12:23:04 Buttman-ubuntu mtp-probe: bus: 1, device: 46 was not an MTP device
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.601716] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.601787] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:04 Buttman-ubuntu kernel: [79442.602814] usb 1-2: USB disconnect, device number 47
Apr 25 12:23:05 Buttman-ubuntu kernel: [79443.432136] usb 1-2: new high speed USB device number 48 using ehci_hcd
Apr 25 12:23:05 Buttman-ubuntu mtp-probe: checking bus 1, device 48: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:05 Buttman-ubuntu kernel: [79443.645920] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:06 Buttman-ubuntu kernel: [79444.644043] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:06 Buttman-ubuntu kernel: [79444.644059] Failed to initialize the device
Apr 25 12:23:06 Buttman-ubuntu kernel: [79444.653252] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:06 Buttman-ubuntu kernel: [79444.764101] usb 1-2: reset high speed USB device number 48 using ehci_hcd
Apr 25 12:23:06 Buttman-ubuntu kernel: [79444.896224] usb 1-2: device firmware changed
Apr 25 12:23:06 Buttman-ubuntu kernel: [79444.896515] usb 1-2: USB disconnect, device number 48
Apr 25 12:23:07 Buttman-ubuntu kernel: [79445.012098] usb 1-2: new high speed USB device number 49 using ehci_hcd
Apr 25 12:23:07 Buttman-ubuntu mtp-probe: bus: 1, device: 48 was not an MTP device
Apr 25 12:23:07 Buttman-ubuntu kernel: [79445.145701] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:07 Buttman-ubuntu kernel: [79445.145775] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:07 Buttman-ubuntu kernel: [79445.146765] usb 1-2: USB disconnect, device number 49
Apr 25 12:23:08 Buttman-ubuntu kernel: [79445.976084] usb 1-2: new high speed USB device number 50 using ehci_hcd
Apr 25 12:23:08 Buttman-ubuntu mtp-probe: checking bus 1, device 50: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:08 Buttman-ubuntu kernel: [79446.190770] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.188081] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.188098] Failed to initialize the device
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.197075] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.308126] usb 1-2: reset high speed USB device number 50 using ehci_hcd
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.440216] usb 1-2: device firmware changed
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.440520] usb 1-2: USB disconnect, device number 50
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.556097] usb 1-2: new high speed USB device number 51 using ehci_hcd
Apr 25 12:23:09 Buttman-ubuntu mtp-probe: bus: 1, device: 50 was not an MTP device
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.689492] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.689543] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:09 Buttman-ubuntu kernel: [79447.690741] usb 1-2: USB disconnect, device number 51
Apr 25 12:23:10 Buttman-ubuntu kernel: [79448.520086] usb 1-2: new high speed USB device number 52 using ehci_hcd
Apr 25 12:23:10 Buttman-ubuntu mtp-probe: checking bus 1, device 52: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:10 Buttman-ubuntu kernel: [79448.734471] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:11 Buttman-ubuntu kernel: [79449.732058] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:11 Buttman-ubuntu kernel: [79449.732075] Failed to initialize the device
Apr 25 12:23:11 Buttman-ubuntu kernel: [79449.741676] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:11 Buttman-ubuntu kernel: [79449.852121] usb 1-2: reset high speed USB device number 52 using ehci_hcd
Apr 25 12:23:12 Buttman-ubuntu kernel: [79449.984275] usb 1-2: device firmware changed
Apr 25 12:23:12 Buttman-ubuntu kernel: [79449.984475] usb 1-2: USB disconnect, device number 52
Apr 25 12:23:12 Buttman-ubuntu kernel: [79450.100089] usb 1-2: new high speed USB device number 53 using ehci_hcd
Apr 25 12:23:12 Buttman-ubuntu mtp-probe: bus: 1, device: 52 was not an MTP device
Apr 25 12:23:12 Buttman-ubuntu kernel: [79450.233568] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:12 Buttman-ubuntu kernel: [79450.233642] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:12 Buttman-ubuntu kernel: [79450.234735] usb 1-2: USB disconnect, device number 53
Apr 25 12:23:13 Buttman-ubuntu kernel: [79451.064073] usb 1-2: new high speed USB device number 54 using ehci_hcd
Apr 25 12:23:13 Buttman-ubuntu mtp-probe: checking bus 1, device 54: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:13 Buttman-ubuntu kernel: [79451.277960] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.276095] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.276115] Failed to initialize the device
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.285253] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.396079] usb 1-2: reset high speed USB device number 54 using ehci_hcd
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.528270] usb 1-2: device firmware changed
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.528493] usb 1-2: USB disconnect, device number 54
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.644080] usb 1-2: new high speed USB device number 55 using ehci_hcd
Apr 25 12:23:14 Buttman-ubuntu mtp-probe: bus: 1, device: 54 was not an MTP device
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.777615] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.777660] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:14 Buttman-ubuntu kernel: [79452.778636] usb 1-2: USB disconnect, device number 55
Apr 25 12:23:15 Buttman-ubuntu kernel: [79453.608074] usb 1-2: new high speed USB device number 56 using ehci_hcd
Apr 25 12:23:15 Buttman-ubuntu mtp-probe: checking bus 1, device 56: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:15 Buttman-ubuntu kernel: [79453.823402] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:16 Buttman-ubuntu kernel: [79454.820107] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:16 Buttman-ubuntu kernel: [79454.820128] Failed to initialize the device
Apr 25 12:23:16 Buttman-ubuntu kernel: [79454.829329] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:17 Buttman-ubuntu kernel: [79454.940072] usb 1-2: reset high speed USB device number 56 using ehci_hcd
Apr 25 12:23:17 Buttman-ubuntu kernel: [79455.072311] usb 1-2: device firmware changed
Apr 25 12:23:17 Buttman-ubuntu kernel: [79455.072489] usb 1-2: USB disconnect, device number 56
Apr 25 12:23:17 Buttman-ubuntu kernel: [79455.188054] usb 1-2: new high speed USB device number 57 using ehci_hcd
Apr 25 12:23:17 Buttman-ubuntu mtp-probe: bus: 1, device: 56 was not an MTP device
Apr 25 12:23:17 Buttman-ubuntu kernel: [79455.321441] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:17 Buttman-ubuntu kernel: [79455.321472] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:17 Buttman-ubuntu kernel: [79455.322554] usb 1-2: USB disconnect, device number 57
Apr 25 12:23:18 Buttman-ubuntu kernel: [79456.152062] usb 1-2: new high speed USB device number 58 using ehci_hcd
Apr 25 12:23:18 Buttman-ubuntu mtp-probe: checking bus 1, device 58: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:18 Buttman-ubuntu kernel: [79456.365589] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.364062] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.364079] Failed to initialize the device
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.373424] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.484118] usb 1-2: reset high speed USB device number 58 using ehci_hcd
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.616276] usb 1-2: device firmware changed
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.616492] usb 1-2: USB disconnect, device number 58
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.732090] usb 1-2: new high speed USB device number 59 using ehci_hcd
Apr 25 12:23:19 Buttman-ubuntu mtp-probe: bus: 1, device: 58 was not an MTP device
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.865553] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.865590] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:19 Buttman-ubuntu kernel: [79457.866579] usb 1-2: USB disconnect, device number 59
Apr 25 12:23:19 Buttman-ubuntu mtp-probe: checking bus 1, device 59: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:20 Buttman-ubuntu mtp-probe: bus: 1, device: 59 was not an MTP device
Apr 25 12:23:20 Buttman-ubuntu kernel: [79458.696077] usb 1-2: new high speed USB device number 60 using ehci_hcd
Apr 25 12:23:20 Buttman-ubuntu mtp-probe: checking bus 1, device 60: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:20 Buttman-ubuntu kernel: [79458.911078] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:21 Buttman-ubuntu kernel: [79459.908079] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:21 Buttman-ubuntu kernel: [79459.908099] Failed to initialize the device
Apr 25 12:23:22 Buttman-ubuntu kernel: [79459.917123] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:22 Buttman-ubuntu kernel: [79460.028071] usb 1-2: reset high speed USB device number 60 using ehci_hcd
Apr 25 12:23:22 Buttman-ubuntu kernel: [79460.160227] usb 1-2: device firmware changed
Apr 25 12:23:22 Buttman-ubuntu kernel: [79460.160432] usb 1-2: USB disconnect, device number 60
Apr 25 12:23:22 Buttman-ubuntu kernel: [79460.276079] usb 1-2: new high speed USB device number 61 using ehci_hcd
Apr 25 12:23:22 Buttman-ubuntu mtp-probe: bus: 1, device: 60 was not an MTP device
Apr 25 12:23:22 Buttman-ubuntu kernel: [79460.409534] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:22 Buttman-ubuntu kernel: [79460.409579] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:22 Buttman-ubuntu kernel: [79460.410597] usb 1-2: USB disconnect, device number 61
Apr 25 12:23:23 Buttman-ubuntu kernel: [79461.240068] usb 1-2: new high speed USB device number 62 using ehci_hcd
Apr 25 12:23:23 Buttman-ubuntu mtp-probe: checking bus 1, device 62: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:23 Buttman-ubuntu kernel: [79461.455765] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:24 Buttman-ubuntu kernel: [79462.456049] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:24 Buttman-ubuntu kernel: [79462.456067] Failed to initialize the device
Apr 25 12:23:24 Buttman-ubuntu kernel: [79462.465460] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:24 Buttman-ubuntu kernel: [79462.576152] usb 1-2: reset high speed USB device number 62 using ehci_hcd
Apr 25 12:23:24 Buttman-ubuntu kernel: [79462.708339] usb 1-2: device firmware changed
Apr 25 12:23:24 Buttman-ubuntu kernel: [79462.708579] usb 1-2: USB disconnect, device number 62
Apr 25 12:23:24 Buttman-ubuntu kernel: [79462.824111] usb 1-2: new high speed USB device number 63 using ehci_hcd
Apr 25 12:23:25 Buttman-ubuntu mtp-probe: bus: 1, device: 62 was not an MTP device
Apr 25 12:23:25 Buttman-ubuntu kernel: [79462.957616] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:25 Buttman-ubuntu kernel: [79462.957707] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:25 Buttman-ubuntu kernel: [79462.958719] usb 1-2: USB disconnect, device number 63
Apr 25 12:23:25 Buttman-ubuntu kernel: [79463.788087] usb 1-2: new high speed USB device number 64 using ehci_hcd
Apr 25 12:23:26 Buttman-ubuntu mtp-probe: checking bus 1, device 64: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:26 Buttman-ubuntu kernel: [79464.002463] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.000043] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.000059] Failed to initialize the device
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.009166] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.120076] usb 1-2: reset high speed USB device number 64 using ehci_hcd
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.252286] usb 1-2: device firmware changed
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.252486] usb 1-2: USB disconnect, device number 64
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.368039] usb 1-2: new high speed USB device number 65 using ehci_hcd
Apr 25 12:23:27 Buttman-ubuntu mtp-probe: bus: 1, device: 64 was not an MTP device
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.501776] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.501866] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:27 Buttman-ubuntu kernel: [79465.502914] usb 1-2: USB disconnect, device number 65
Apr 25 12:23:28 Buttman-ubuntu kernel: [79466.332068] usb 1-2: new high speed USB device number 66 using ehci_hcd
Apr 25 12:23:28 Buttman-ubuntu mtp-probe: checking bus 1, device 66: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:28 Buttman-ubuntu kernel: [79466.546201] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:29 Buttman-ubuntu kernel: [79467.544091] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:29 Buttman-ubuntu kernel: [79467.544111] Failed to initialize the device
Apr 25 12:23:29 Buttman-ubuntu kernel: [79467.553120] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:29 Buttman-ubuntu kernel: [79467.664082] usb 1-2: reset high speed USB device number 66 using ehci_hcd
Apr 25 12:23:29 Buttman-ubuntu kernel: [79467.796239] usb 1-2: device firmware changed
Apr 25 12:23:29 Buttman-ubuntu kernel: [79467.796444] usb 1-2: USB disconnect, device number 66
Apr 25 12:23:30 Buttman-ubuntu kernel: [79467.912073] usb 1-2: new high speed USB device number 67 using ehci_hcd
Apr 25 12:23:30 Buttman-ubuntu mtp-probe: bus: 1, device: 66 was not an MTP device
Apr 25 12:23:30 Buttman-ubuntu kernel: [79468.045893] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:30 Buttman-ubuntu kernel: [79468.045983] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:30 Buttman-ubuntu kernel: [79468.047067] usb 1-2: USB disconnect, device number 67
Apr 25 12:23:30 Buttman-ubuntu kernel: [79468.876093] usb 1-2: new high speed USB device number 68 using ehci_hcd
Apr 25 12:23:31 Buttman-ubuntu mtp-probe: checking bus 1, device 68: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:31 Buttman-ubuntu kernel: [79469.090899] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.088108] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.088127] Failed to initialize the device
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.097456] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.208166] usb 1-2: reset high speed USB device number 68 using ehci_hcd
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.340346] usb 1-2: device firmware changed
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.340556] usb 1-2: USB disconnect, device number 68
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.456144] usb 1-2: new high speed USB device number 69 using ehci_hcd
Apr 25 12:23:32 Buttman-ubuntu mtp-probe: bus: 1, device: 68 was not an MTP device
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.589729] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.589817] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:32 Buttman-ubuntu kernel: [79470.590896] usb 1-2: USB disconnect, device number 69
Apr 25 12:23:33 Buttman-ubuntu kernel: [79471.420081] usb 1-2: new high speed USB device number 70 using ehci_hcd
Apr 25 12:23:33 Buttman-ubuntu mtp-probe: checking bus 1, device 70: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:33 Buttman-ubuntu kernel: [79471.634103] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:34 Buttman-ubuntu kernel: [79472.632102] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:34 Buttman-ubuntu kernel: [79472.632122] Failed to initialize the device
Apr 25 12:23:34 Buttman-ubuntu kernel: [79472.641410] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:34 Buttman-ubuntu kernel: [79472.752109] usb 1-2: reset high speed USB device number 70 using ehci_hcd
Apr 25 12:23:34 Buttman-ubuntu kernel: [79472.884304] usb 1-2: device firmware changed
Apr 25 12:23:34 Buttman-ubuntu kernel: [79472.884537] usb 1-2: USB disconnect, device number 70
Apr 25 12:23:35 Buttman-ubuntu kernel: [79473.000095] usb 1-2: new high speed USB device number 71 using ehci_hcd
Apr 25 12:23:35 Buttman-ubuntu mtp-probe: bus: 1, device: 70 was not an MTP device
Apr 25 12:23:35 Buttman-ubuntu kernel: [79473.133648] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:35 Buttman-ubuntu kernel: [79473.133726] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:35 Buttman-ubuntu kernel: [79473.134681] usb 1-2: USB disconnect, device number 71
Apr 25 12:23:36 Buttman-ubuntu kernel: [79473.964071] usb 1-2: new high speed USB device number 72 using ehci_hcd
Apr 25 12:23:36 Buttman-ubuntu mtp-probe: checking bus 1, device 72: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:36 Buttman-ubuntu kernel: [79474.178579] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.176112] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.176131] Failed to initialize the device
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.185243] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.296125] usb 1-2: reset high speed USB device number 72 using ehci_hcd
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.428253] usb 1-2: device firmware changed
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.428470] usb 1-2: USB disconnect, device number 72
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.544135] usb 1-2: new high speed USB device number 73 using ehci_hcd
Apr 25 12:23:37 Buttman-ubuntu mtp-probe: bus: 1, device: 72 was not an MTP device
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.677548] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.677637] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:37 Buttman-ubuntu kernel: [79475.678638] usb 1-2: USB disconnect, device number 73
Apr 25 12:23:38 Buttman-ubuntu kernel: [79476.508085] usb 1-2: new high speed USB device number 74 using ehci_hcd
Apr 25 12:23:38 Buttman-ubuntu mtp-probe: checking bus 1, device 74: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:38 Buttman-ubuntu kernel: [79476.721909] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:39 Buttman-ubuntu kernel: [79477.720102] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:39 Buttman-ubuntu kernel: [79477.720121] Failed to initialize the device
Apr 25 12:23:39 Buttman-ubuntu kernel: [79477.729325] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:39 Buttman-ubuntu kernel: [79477.840091] usb 1-2: reset high speed USB device number 74 using ehci_hcd
Apr 25 12:23:40 Buttman-ubuntu kernel: [79477.972185] usb 1-2: device firmware changed
Apr 25 12:23:40 Buttman-ubuntu kernel: [79477.972381] usb 1-2: USB disconnect, device number 74
Apr 25 12:23:40 Buttman-ubuntu kernel: [79478.088068] usb 1-2: new high speed USB device number 75 using ehci_hcd
Apr 25 12:23:40 Buttman-ubuntu mtp-probe: bus: 1, device: 74 was not an MTP device
Apr 25 12:23:40 Buttman-ubuntu kernel: [79478.221437] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:40 Buttman-ubuntu kernel: [79478.221480] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:40 Buttman-ubuntu kernel: [79478.223191] usb 1-2: USB disconnect, device number 75
Apr 25 12:23:41 Buttman-ubuntu kernel: [79479.052095] usb 1-2: new high speed USB device number 76 using ehci_hcd
Apr 25 12:23:41 Buttman-ubuntu mtp-probe: checking bus 1, device 76: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:41 Buttman-ubuntu kernel: [79479.266853] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.264073] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.264091] Failed to initialize the device
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.273413] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.384123] usb 1-2: reset high speed USB device number 76 using ehci_hcd
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.516310] usb 1-2: device firmware changed
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.516529] usb 1-2: USB disconnect, device number 76
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.632118] usb 1-2: new high speed USB device number 77 using ehci_hcd
Apr 25 12:23:42 Buttman-ubuntu mtp-probe: bus: 1, device: 76 was not an MTP device
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.765757] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.765834] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:42 Buttman-ubuntu kernel: [79480.766995] usb 1-2: USB disconnect, device number 77
Apr 25 12:23:43 Buttman-ubuntu kernel: [79481.596127] usb 1-2: new high speed USB device number 78 using ehci_hcd
Apr 25 12:23:43 Buttman-ubuntu mtp-probe: checking bus 1, device 78: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:43 Buttman-ubuntu kernel: [79481.810050] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:44 Buttman-ubuntu kernel: [79482.808044] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:44 Buttman-ubuntu kernel: [79482.808057] Failed to initialize the device
Apr 25 12:23:44 Buttman-ubuntu kernel: [79482.818225] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:45 Buttman-ubuntu kernel: [79482.928128] usb 1-2: reset high speed USB device number 78 using ehci_hcd
Apr 25 12:23:45 Buttman-ubuntu kernel: [79483.060260] usb 1-2: device firmware changed
Apr 25 12:23:45 Buttman-ubuntu kernel: [79483.060465] usb 1-2: USB disconnect, device number 78
Apr 25 12:23:45 Buttman-ubuntu kernel: [79483.176144] usb 1-2: new high speed USB device number 79 using ehci_hcd
Apr 25 12:23:45 Buttman-ubuntu mtp-probe: bus: 1, device: 78 was not an MTP device
Apr 25 12:23:45 Buttman-ubuntu kernel: [79483.309604] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:45 Buttman-ubuntu kernel: [79483.309692] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:45 Buttman-ubuntu kernel: [79483.310837] usb 1-2: USB disconnect, device number 79
Apr 25 12:23:46 Buttman-ubuntu kernel: [79484.140079] usb 1-2: new high speed USB device number 80 using ehci_hcd
Apr 25 12:23:46 Buttman-ubuntu mtp-probe: checking bus 1, device 80: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:46 Buttman-ubuntu kernel: [79484.352647] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.352075] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.352095] Failed to initialize the device
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.361328] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.472084] usb 1-2: reset high speed USB device number 80 using ehci_hcd
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.604187] usb 1-2: device firmware changed
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.604410] usb 1-2: USB disconnect, device number 80
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.720135] usb 1-2: new high speed USB device number 81 using ehci_hcd
Apr 25 12:23:47 Buttman-ubuntu mtp-probe: bus: 1, device: 80 was not an MTP device
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.853786] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.853865] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:47 Buttman-ubuntu kernel: [79485.854877] usb 1-2: USB disconnect, device number 81
Apr 25 12:23:48 Buttman-ubuntu kernel: [79486.684125] usb 1-2: new high speed USB device number 82 using ehci_hcd
Apr 25 12:23:48 Buttman-ubuntu mtp-probe: checking bus 1, device 82: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2"
Apr 25 12:23:48 Buttman-ubuntu kernel: [79486.899868] usb 1-2: ath9k_htc: Transferred FW: htc_7010.fw, size: 72992
Apr 25 12:23:49 Buttman-ubuntu kernel: [79487.901075] ath9k_htc 1-2:1.0: ath9k_htc: Target is unresponsive
Apr 25 12:23:49 Buttman-ubuntu kernel: [79487.901089] Failed to initialize the device
Apr 25 12:23:49 Buttman-ubuntu kernel: [79487.910268] ath9k_htc: probe of 1-2:1.0 failed with error -22
Apr 25 12:23:50 Buttman-ubuntu kernel: [79488.020068] usb 1-2: reset high speed USB device number 82 using ehci_hcd
Apr 25 12:23:50 Buttman-ubuntu kernel: [79488.152360] usb 1-2: device firmware changed
Apr 25 12:23:50 Buttman-ubuntu kernel: [79488.152555] usb 1-2: USB disconnect, device number 82
Apr 25 12:23:50 Buttman-ubuntu kernel: [79488.268146] usb 1-2: new high speed USB device number 83 using ehci_hcd
Apr 25 12:23:50 Buttman-ubuntu mtp-probe: bus: 1, device: 82 was not an MTP device
Apr 25 12:23:50 Buttman-ubuntu kernel: [79488.401636] usb-storage 1-2:1.0: device ignored
Apr 25 12:23:50 Buttman-ubuntu kernel: [79488.401704] usb 1-2: Ejecting virtual installer media...
Apr 25 12:23:50 Buttman-ubuntu kernel: [79488.402850] usb 1-2: USB disconnect, device number 83
```It got into a *loop*, apparently. The last line says I disconnected, but I didn't, it's just coincidence, I just pressed Ctrl+C during that step of the *loop*, on that very second.[B]

Here is lsusb output:[/B] ```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 005: ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870]
Bus 003 Device 002: ID 1c4f:0002 SiGma Micro 
Bus 005 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
_**Bus 001 Device 000: ID 1668:1200 Actiontec Electronics, Inc. [hex] 802AIN Wireless N Network Adapter [Atheros AR9001U]**_
```To be honest, it was not even getting listed before, now I can see it with lsusb. I used -l (L) before tho.

---

### Post by chili555 on 2012-04-25
I am on my way out the door. Please see here: [http://wiki.debian.org/ar9170usb](http://wiki.debian.org/ar9170usb)> Use of the Qwest/Actiontec 802AIN device (USB ID 1668:1200) requires the usb-modeswitch package to be installed.2usb-modeswitch is a bit complex; you might install it and try again.

The loop is because it's trying to jump over the storage part, where the Windows drivers are installed, to the wireless device part. That's what usb-modeswitch facilitates.

You might also search this forum for one of many threads about working USB devices. I will be glad to help you in either case.

Off to lunch!

---

### Post by mizifih on 2012-04-25
[chili555]("http://ubuntuforums.org/member.php?u=35909"),

Can I use that Debian repository? Couldn't find firmware-atheros for Ubuntu. For a reason, I'm guessing.

usb-modeswitch was already installed on the system.

---

### Post by chili555 on 2012-04-25
Let's check here:```
$ modinfo ath9k_htc
filename:       /lib/modules/3.2.0-23-generic-pae/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       [COLOR="Red"]htc_9271.fw[/COLOR]
firmware:       [COLOR="Red"]htc_7010.fw[/COLOR]
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     9B885B82530A1FF8F15C062
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p017Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]1668[/COLOR]p[COLOR="Red"]1200[/COLOR]d*dc*dsc*dp*ic*isc*ip*
<snip>

```My install contains the firmware, please check yours:```
ls /lib/firmware | grep htc
htc_7010.fw
htc_9271.fw

```If you don't have it, we'll figure out how to get it, or I'll send a copy of mine.

---

### Post by mizifih on 2012-04-25
I ran the modinfo ath9k_htc command and got this:

```
root@Buttman-ubuntu:/# **modinfo ath9k_htc**
filename:       /lib/modules/3.0.0-17-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     2113477A45D8386547653D7
alias:          usb:v0CF3p20FFd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA704d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p7015d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp8403d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3pB003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v040Dp3801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04CAp4605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3350d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3349d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3348d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3346d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3328d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3327d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3A10d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9030d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p1006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CF3p9271d*dc*dsc*dp*ic*isc*ip*
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
vermagic:       3.0.0-17-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
root@Buttman-ubuntu:/# 

```

**ls /lib/firmware | grep htc**
```
root@Buttman-ubuntu:/# ls /lib/firmware | grep htc
htc_7010.fw
htc_9271.fw
root@Buttman-ubuntu:/# 
```

---

### Post by chili555 on 2012-04-25
So you do have the firmware that's required. Is the loop, that is, with indexing device numbers, present if the device is inserted before a cold boot?```
sudo tail -n25 /var/log/syslog
sudo cat /var/log/syslog | grep -e device -e initialize
```Does usb_modeswitch load automagically on cold boot?```
lsmod | grep modeswitch
```

---

