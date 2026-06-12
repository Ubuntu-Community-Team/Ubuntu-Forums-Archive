---
title: "Blueman - Palm Error: PPP Timeout"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by -DarkAceZ- on 2011-06-24
Connecting Palm 72 to internet Via Bluetooth.
PALM:
*Connect*
Initializing...
Error: Serial: timeout. Could be bad cable or faulty modem. 

So I do on PC:
```
dund --listen --persist --msdun call dun
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables -A FORWARD -i ppp0 -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
```

PALM:
*Connect*
Initializing...
Signing on...
Error: PPP timout (0x1231)

Now what do I do?

PC:
USB Dongle - ISSCEDRBTA
BlueZ installed - (Did bluetoothd --version to get this) Version 4.94
/ect/ppp/peers/dun already edited.
/var/log/messages (I don't think this is needed, but JIC)

```
Jun 24 14:18:25 janet-desktop kernel: [   18.168745] scsi4 : SCSI emulation for USB Mass Storage devices
Jun 24 14:18:25 janet-desktop kernel: [   18.172550] usbcore: registered new interface driver usb-storage
Jun 24 14:18:25 janet-desktop kernel: [   18.172554] USB Mass Storage support registered.
Jun 24 14:18:25 janet-desktop kernel: [   18.177200] usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4511
Jun 24 14:18:25 janet-desktop kernel: [   18.177227] usbcore: registered new interface driver usblp
Jun 24 14:18:25 janet-desktop kernel: [   18.224417] Console: switching to colour frame buffer device 80x30
Jun 24 14:18:25 janet-desktop kernel: [   18.339159] Bluetooth: L2CAP ver 2.14
Jun 24 14:18:25 janet-desktop kernel: [   18.339163] Bluetooth: L2CAP socket layer initialized
Jun 24 14:18:25 janet-desktop kernel: [   18.372876] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jun 24 14:18:25 janet-desktop kernel: [   18.372879] Bluetooth: BNEP filters: protocol multicast
Jun 24 14:18:25 janet-desktop kernel: [   18.377307] Bluetooth: SCO (Voice Link) ver 0.6
Jun 24 14:18:25 janet-desktop kernel: [   18.377311] Bluetooth: SCO socket layer initialized
Jun 24 14:18:26 janet-desktop kernel: [   18.503340] Bluetooth: RFCOMM TTY layer initialized
Jun 24 14:18:26 janet-desktop kernel: [   18.503347] Bluetooth: RFCOMM socket layer initialized
Jun 24 14:18:26 janet-desktop kernel: [   18.503349] Bluetooth: RFCOMM ver 1.11
Jun 24 14:18:27 janet-desktop kernel: [   19.530099] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
Jun 24 14:18:27 janet-desktop kernel: [   19.625423] usb 2-7: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
Jun 24 14:18:27 janet-desktop kernel: [   19.912179] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
Jun 24 14:18:27 janet-desktop kernel: [   19.912190] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Jun 24 14:18:27 janet-desktop kernel: [   19.912192]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Jun 24 14:18:27 janet-desktop kernel: [   19.912193]  (Note that use of the override may cause unknown side effects.)
Jun 24 14:18:27 janet-desktop kernel: [   19.912208] amd64_edac: probe of 0000:00:18.2 failed with error -22
Jun 24 14:18:27 janet-desktop kernel: [   19.916306] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 22
Jun 24 14:18:27 janet-desktop kernel: [   19.916316] nvidia 0000:00:0d.0: PCI INT A -> Link[LMC9] -> GSI 22 (level, low) -> IRQ 22
Jun 24 14:18:27 janet-desktop kernel: [   19.916610] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.22  Wed Nov 11 05:08:25 PST 2009
Jun 24 14:18:30 janet-desktop kernel: [   23.177059] scsi 4:0:0:0: Direct-Access     HP       Photosmart 2610x 1.00 PQ: 0 ANSI: 2
Jun 24 14:18:30 janet-desktop kernel: [   23.178750] sd 4:0:0:0: Attached scsi generic sg2 type 0
Jun 24 14:18:30 janet-desktop kernel: [   23.185092] sd 4:0:0:0: [sdc] 62720 512-byte logical blocks: (32.1 MB/30.6 MiB)
Jun 24 14:18:30 janet-desktop kernel: [   23.189045] sd 4:0:0:0: [sdc] Write Protect is off
Jun 24 14:18:30 janet-desktop kernel: [   23.207043]  sdc: sdc1
Jun 24 14:18:30 janet-desktop kernel: [   23.237051] sd 4:0:0:0: [sdc] Attached SCSI removable disk
Jun 24 14:28:22 janet-desktop kernel: [  615.470363] __ratelimit: 18 callbacks suppressed
```

PALM:
Prefs/Network
Service: ISSCEDBTA, 
Username: Linux SU, 
Password: Assigned, 
Connection: ISSCEDBTA

Prefs/Network/Details
Connection type: PPP
Idle timout: 3 Minutes
Query DNS UNCHECKED = Primary DNS entered - Secondary DNS blank
IP Address: Automatic UNCHECKED = 192.168.168.50 (I gave the Palm its own IP Adress)

Prefs/Network/Details/Script
Send CR
Delay 1
Send CLIENT
Wait For CLIENTSERVER
End

Prefs/Network/Options/View Log:
Connect Log


S: ^M
S: CLIENT
R: CLIENTSERVER
LCP->CfgReq
LCP->CfgReq
LCP->CfgReq
LCP->CfgReq
LCP->CfgReq
LCP->CfgReq
LCP->CfgReq
LCP->CfgReq
LCP Timeout

Service name:		
Local IP address:	127.0.0.1
Gateway address:	0.0.0.0
DNS addresses:

				192.168.254.254




----------------------------------------------
Any idea what I should do? (Besides to not give so much unneeded information... :) )

---

### Post by -DarkAceZ- on 2011-06-25
I think it might have something to do with the script.

---

### Post by -DarkAceZ- on 2011-06-28
So no one has a solution?

---

