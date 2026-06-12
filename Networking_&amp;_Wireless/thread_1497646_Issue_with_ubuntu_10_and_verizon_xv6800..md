---
title: "Issue with ubuntu 10 and verizon xv6800."
date: 2010-05-30
forum: Networking &amp; Wireless
---

### Post by tip120 on 2010-05-30
Hi, I'm trying to set up my cell so I can use cellular internet in ubuntu like I do in windows. I'm having an issue.    I've scoured the net, and found multiple guides, unfortunately, the problem I'm having seems to precede any of these. 

I can't follow the guides because I can't get to the first step.  When I plug my phone in via USB, whether I'm using the internet sharing program or not, I see "eth1 connected eth1 disconnected" pop up over and over and over. 

My /var/log/messages reads: 

```
May 30 20:55:21 foxbox kernel: [ 1016.792334] eth1: unregister 'rndis_host' usb-0000:00:1d.0-2, RNDIS device
May 30 20:55:21 foxbox kernel: [ 1017.150089] usb 5-2: new full speed USB device using uhci_hcd and address 51
May 30 20:55:22 foxbox kernel: [ 1017.810267] usb 5-2: new full speed USB device using uhci_hcd and address 52
May 30 20:55:23 foxbox kernel: [ 1018.820096] usb 5-2: new full speed USB device using uhci_hcd and address 54
May 30 20:55:24 foxbox kernel: [ 1019.480105] usb 5-2: new full speed USB device using uhci_hcd and address 55
May 30 20:55:24 foxbox kernel: [ 1020.140085] usb 5-2: new full speed USB device using uhci_hcd and address 56
May 30 20:55:24 foxbox kernel: [ 1020.194428] usb 5-2: configuration #1 chosen from 1 choice
May 30 20:55:25 foxbox kernel: [ 1020.286835] eth1: register 'rndis_host' at usb-0000:00:1d.0-2, RNDIS device, 80:00:60:0f:e8:00
May 30 20:55:25 foxbox kernel: [ 1021.040215] usb 5-2: USB disconnect, address 56
May 30 20:55:25 foxbox kernel: [ 1021.042331] eth1: unregister 'rndis_host' usb-0000:00:1d.0-2, RNDIS device
May 30 20:55:26 foxbox kernel: [ 1021.460086] usb 5-2: new full speed USB device using uhci_hcd and address 57
May 30 20:55:26 foxbox kernel: [ 1022.070097] usb 5-2: new full speed USB device using uhci_hcd and address 58
May 30 20:55:28 foxbox kernel: [ 1023.360088] usb 5-2: new full speed USB device using uhci_hcd and address 59
May 30 20:55:28 foxbox kernel: [ 1023.630144] usb 5-2: new full speed USB device using uhci_hcd and address 60
May 30 20:55:28 foxbox kernel: [ 1023.686431] usb 5-2: configuration #1 chosen from 1 choice
May 30 20:55:28 foxbox kernel: [ 1023.778837] eth1: register 'rndis_host' at usb-0000:00:1d.0-2, RNDIS device, 80:00:60:0f:e8:00
May 30 20:55:29 foxbox kernel: [ 1024.294337] usb 5-2: USB disconnect, address 60
May 30 20:55:29 foxbox kernel: [ 1024.296321] eth1: unregister 'rndis_host' usb-0000:00:1d.0-2, RNDIS device
May 30 20:55:29 foxbox kernel: [ 1024.730086] usb 5-2: new full speed USB device using uhci_hcd and address 61
May 30 20:55:30 foxbox kernel: [ 1025.390087] usb 5-2: new full speed USB device using uhci_hcd and address 62
May 30 20:55:30 foxbox kernel: [ 1025.562423] usb 5-2: configuration #1 chosen from 1 choice
May 30 20:55:30 foxbox kernel: [ 1025.790197] usb 5-2: USB disconnect, address 62
May 30 20:55:30 foxbox kernel: [ 1026.070110] usb 5-2: new full speed USB device using uhci_hcd and address 63
May 30 20:55:31 foxbox kernel: [ 1026.730097] usb 5-2: new full speed USB device using uhci_hcd and address 64
May 30 20:55:32 foxbox kernel: [ 1027.390081] usb 5-2: new full speed USB device using uhci_hcd and address 65
May 30 20:55:32 foxbox kernel: [ 1027.449461] usb 5-2: configuration #1 chosen from 1 choice
May 30 20:55:32 foxbox kernel: [ 1027.541851] eth1: register 'rndis_host' at usb-0000:00:1d.0-2, RNDIS device, 80:00:60:0f:e8:00
May 30 20:55:32 foxbox kernel: [ 1028.040432] usb 5-2: USB disconnect, address 65
May 30 20:55:32 foxbox kernel: [ 1028.042333] eth1: unregister 'rndis_host' usb-0000:00:1d.0-2, RNDIS device
May 30 20:55:33 foxbox kernel: [ 1028.440105] usb 5-2: new full speed USB device using uhci_hcd and address 66
May 30 20:55:33 foxbox kernel: [ 1029.040181] usb 5-2: new full speed USB device using uhci_hcd and address 67
May 30 20:55:34 foxbox kernel: [ 1029.214415] usb 5-2: no configuration chosen from 0 choices
May 30 20:55:34 foxbox kernel: [ 1029.290185] usb 5-2: USB disconnect, address 67
 
```Over and over again.  I have no idea what to do, can anyone help?

---

### Post by tip120 on 2010-05-31
bump? :/

---

