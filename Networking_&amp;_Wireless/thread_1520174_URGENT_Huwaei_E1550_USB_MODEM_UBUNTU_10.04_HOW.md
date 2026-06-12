---
title: "URGENT: Huwaei E1550 USB MODEM UBUNTU 10.04 HOW"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by e1550usbmodem on 2010-06-29
I NEED URGENT HELP. I used to use a previous version of Huwaei modem which offered kind of plug and play functionality. Now I bought a Huwaei E1550 modem. I couldnt get it to detect as a modem, it detected as a USB Storage device. But now after some tweaking with usb_modeswitch / usb-modeswitch and udev/modem-modeswticher it doesnt even detect it as a Mass storage device. Here are a few diagnostics:

Every time I input the modem, i quickly use lsusb in the terminal and i see the mass storage device. But if i use lsusb one second later, it disappears and doesnt reappear.
I also went in to /var/logs/messages and here is the change in the file after I plugged in the modem:

> Jun 29 15:41:54 comp-desktop kernel: [ 2367.932133] usb 1-8: USB disconnect, address 90
Jun 29 15:42:10 comp-desktop kernel: [ 2384.608020] usb 5-1: new low speed USB device using uhci_hcd and address 121
Jun 29 15:42:11 comp-desktop kernel: [ 2385.172050] usb 5-1: new low speed USB device using uhci_hcd and address 122
Jun 29 15:42:11 comp-desktop kernel: [ 2385.732066] usb 5-1: new low speed USB device using uhci_hcd and address 123
Jun 29 15:42:12 comp-desktop kernel: [ 2386.252031] usb 5-1: new low speed USB device using uhci_hcd and address 124
Jun 29 15:42:12 comp-desktop kernel: [ 2386.900045] usb 5-2: new full speed USB device using uhci_hcd and address 125
Jun 29 15:42:13 comp-desktop kernel: [ 2387.115949] usb 5-2: configuration #1 chosen from 2 choices
Jun 29 15:42:13 comp-desktop kernel: [ 2387.256421] cdc_acm 5-2:1.0: ttyACM0: USB ACM device
Jun 29 15:42:13 comp-desktop kernel: [ 2387.263141] usbcore: registered new interface driver cdc_acm
Jun 29 15:42:13 comp-desktop kernel: [ 2387.263602] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
Jun 29 15:42:20 comp-desktop pppd[5281]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Jun 29 15:42:20 comp-desktop pppd[5281]: pppd 2.4.5 started by root, uid 0
Jun 29 15:42:20 comp-desktop pppd[5281]: Using interface ppp0
Jun 29 15:42:20 comp-desktop pppd[5281]: Connect: ppp0 <--> /dev/ttyACM0
Jun 29 15:42:20 comp-desktop pppd[5281]: PAP authentication succeeded
Jun 29 15:42:20 comp-desktop kernel: [ 2394.577355] PPP BSD Compression module registered
Jun 29 15:42:20 comp-desktop kernel: [ 2394.601685] PPP Deflate Compression module registered
Jun 29 15:42:23 comp-desktop pppd[5281]: local  IP address 10.130.93.52
Jun 29 15:42:23 comp-desktop pppd[5281]: remote IP address 192.168.100.101
Jun 29 15:42:23 comp-desktop pppd[5281]: primary   DNS address 202.56.4.120
Jun 29 15:42:23 comp-desktop pppd[5281]: secondary DNS address 202.56.4.121
Jun 29 15:45:15 comp-desktop kernel: [ 2569.688061] usb 5-1: new low speed USB device using uhci_hcd and address 126
Jun 29 15:45:16 comp-desktop kernel: [ 2570.248056] usb 5-1: new low speed USB device using uhci_hcd and address 127
Jun 29 15:45:17 comp-desktop kernel: [ 2571.176064] usb 5-1: new low speed USB device using uhci_hcd and address 2
Jun 29 15:45:17 comp-desktop kernel: [ 2571.736055] usb 5-1: new low speed USB device using uhci_hcd and address 3
Jun 29 15:45:18 comp-desktop kernel: [ 2572.296095] usb 5-1: new low speed USB device using uhci_hcd and address 4
Jun 29 15:45:18 comp-desktop kernel: [ 2572.820043] usb 5-1: new low speed USB device using uhci_hcd and address 5
Jun 29 15:47:18 comp-desktop kernel: [ 2692.696069] usb 5-1: new low speed USB device using uhci_hcd and address 7
Jun 29 15:47:19 comp-desktop kernel: [ 2693.440064] usb 5-1: new low speed USB device using uhci_hcd and address 8
Jun 29 15:47:21 comp-desktop kernel: [ 2695.176068] usb 5-1: new low speed USB device using uhci_hcd and address 10
Jun 29 15:47:21 comp-desktop kernel: [ 2695.736074] usb 5-1: new low speed USB device using uhci_hcd and address 11
Jun 29 15:47:22 comp-desktop kernel: [ 2696.300073] usb 5-1: new low speed USB device using uhci_hcd and address 12
Jun 29 15:47:22 comp-desktop kernel: [ 2696.820058] usb 5-1: new low speed USB device using uhci_hcd and address 13
Jun 29 15:48:20 comp-desktop kernel: [ 2754.680095] usb 5-1: new low speed USB device using uhci_hcd and address 14
Jun 29 15:48:21 comp-desktop kernel: [ 2755.244110] usb 5-1: new low speed USB device using uhci_hcd and address 15
Jun 29 15:48:21 comp-desktop kernel: [ 2755.808049] usb 5-1: new low speed USB device using uhci_hcd and address 16
Jun 29 15:48:22 comp-desktop kernel: [ 2756.328067] usb 5-1: new low speed USB device using uhci_hcd and address 17
Jun 29 15:52:27 comp-desktop kernel: [ 3001.704077] usb 5-1: new low speed USB device using uhci_hcd and address 18
Jun 29 15:52:28 comp-desktop kernel: [ 3002.264092] usb 5-1: new low speed USB device using uhci_hcd and address 19
Jun 29 15:52:28 comp-desktop kernel: [ 3002.828068] usb 5-1: new low speed USB device using uhci_hcd and address 20
Jun 29 15:52:29 comp-desktop kernel: [ 3003.352064] usb 5-1: new low speed USB device using uhci_hcd and address 21
Jun 29 15:54:34 comp-desktop kernel: [ 3127.936075] usb 5-1: new low speed USB device using uhci_hcd and address 22
Jun 29 15:54:34 comp-desktop kernel: [ 3128.496034] usb 5-1: new low speed USB device using uhci_hcd and address 23
Jun 29 15:54:35 comp-desktop kernel: [ 3129.056047] usb 5-1: new low speed USB device using uhci_hcd and address 24
Jun 29 15:54:35 comp-desktop kernel: [ 3129.576283] usb 5-1: new low speed USB device using uhci_hcd and address 25
Jun 29 16:03:36 comp-desktop kernel: [ 3670.064030] usb 5-1: new low speed USB device using uhci_hcd and address 26
Jun 29 16:03:36 comp-desktop kernel: [ 3670.624049] usb 5-1: new low speed USB device using uhci_hcd and address 27
Jun 29 16:03:37 comp-desktop kernel: [ 3671.184047] usb 5-1: new low speed USB device using uhci_hcd and address 28
Jun 29 16:03:37 comp-desktop kernel: [ 3671.704058] usb 5-1: new low speed USB device using uhci_hcd and address 29
Jun 29 16:04:49 comp-desktop kernel: [ 3743.224049] usb 5-1: new low speed USB device using uhci_hcd and address 30
Jun 29 16:04:49 comp-desktop kernel: [ 3743.784062] usb 5-1: new low speed USB device using uhci_hcd and address 31
Jun 29 16:04:50 comp-desktop kernel: [ 3744.352028] usb 5-1: new low speed USB device using uhci_hcd and address 32
Jun 29 16:04:50 comp-desktop kernel: [ 3744.872052] usb 5-1: new low speed USB device using uhci_hcd and address 33
Jun 29 16:05:20 comp-desktop kernel: [ 3774.720051] usb 5-1: new low speed USB device using uhci_hcd and address 34
Jun 29 16:05:21 comp-desktop kernel: [ 3775.288048] usb 5-1: new low speed USB device using uhci_hcd and address 35
Jun 29 16:05:21 comp-desktop kernel: [ 3775.856050] usb 5-1: new low speed USB device using uhci_hcd and address 36
Jun 29 16:05:22 comp-desktop kernel: [ 3776.376048] usb 5-1: new low speed USB device using uhci_hcd and address 37
Jun 29 16:05:32 comp-desktop kernel: [ 3786.872049] usb 5-1: new low speed USB device using uhci_hcd and address 38
Jun 29 16:05:33 comp-desktop kernel: [ 3787.432029] usb 5-1: new low speed USB device using uhci_hcd and address 39
Jun 29 16:05:34 comp-desktop kernel: [ 3787.992052] usb 5-1: new low speed USB device using uhci_hcd and address 40
Jun 29 16:05:34 comp-desktop kernel: [ 3788.512048] usb 5-1: new low speed USB device using uhci_hcd and address 41
Jun 29 16:06:49 comp-desktop kernel: [ 3863.504049] usb 5-1: new low speed USB device using uhci_hcd and address 42
Jun 29 16:06:50 comp-desktop kernel: [ 3864.064050] usb 5-1: new low speed USB device using uhci_hcd and address 43
Jun 29 16:06:50 comp-desktop kernel: [ 3864.624026] usb 5-1: new low speed USB device using uhci_hcd and address 44
Jun 29 16:06:51 comp-desktop kernel: [ 3865.144047] usb 5-1: new low speed USB device using uhci_hcd and address 45
Jun 29 16:07:17 comp-desktop kernel: [ 3891.344049] usb 5-1: new low speed USB device using uhci_hcd and address 46
Jun 29 16:07:18 comp-desktop kernel: [ 3891.904043] usb 5-1: new low speed USB device using uhci_hcd and address 47
Jun 29 16:07:18 comp-desktop kernel: [ 3892.472027] usb 5-1: new low speed USB device using uhci_hcd and address 48
Jun 29 16:07:19 comp-desktop kernel: [ 3892.992063] usb 5-1: new low speed USB device using uhci_hcd and address 49
Jun 29 16:07:31 comp-desktop kernel: [ 3905.168061] usb 5-1: new low speed USB device using uhci_hcd and address 50
Jun 29 16:07:31 comp-desktop kernel: [ 3905.728194] usb 5-1: new low speed USB device using uhci_hcd and address 51
Jun 29 16:07:32 comp-desktop kernel: [ 3906.288075] usb 5-1: new low speed USB device using uhci_hcd and address 52
Jun 29 16:07:32 comp-desktop kernel: [ 3906.808051] usb 5-1: new low speed USB device using uhci_hcd and address 53
Jun 29 16:07:33 comp-desktop kernel: [ 3907.896046] usb 5-1: new low speed USB device using uhci_hcd and address 55
Jun 29 16:07:34 comp-desktop kernel: [ 3908.460052] usb 5-1: new low speed USB device using uhci_hcd and address 56
Jun 29 16:07:35 comp-desktop kernel: [ 3909.020040] usb 5-1: new low speed USB device using uhci_hcd and address 57
Jun 29 16:07:35 comp-desktop kernel: [ 3909.540044] usb 5-1: new low speed USB device using uhci_hcd and address 58
Jun 29 16:07:39 comp-desktop kernel: [ 3913.600064] usb 5-1: new low speed USB device using uhci_hcd and address 59
Jun 29 16:07:40 comp-desktop kernel: [ 3914.160053] usb 5-1: new low speed USB device using uhci_hcd and address 60
Jun 29 16:07:40 comp-desktop kernel: [ 3914.720029] usb 5-1: new low speed USB device using uhci_hcd and address 61
Jun 29 16:07:41 comp-desktop kernel: [ 3915.240027] usb 5-1: new low speed USB device using uhci_hcd and address 62
Jun 29 16:07:48 comp-desktop kernel: [ 3922.280048] usb 5-1: new low speed USB device using uhci_hcd and address 63
Jun 29 16:07:48 comp-desktop kernel: [ 3922.840046] usb 5-1: new low speed USB device using uhci_hcd and address 64
Jun 29 16:07:49 comp-desktop kernel: [ 3923.404051] usb 5-1: new low speed USB device using uhci_hcd and address 65
Jun 29 16:07:50 comp-desktop kernel: [ 3923.928050] usb 5-1: new low speed USB device using uhci_hcd and address 66
Jun 29 16:07:57 comp-desktop kernel: [ 3930.960043] usb 5-1: new low speed USB device using uhci_hcd and address 67
Jun 29 16:07:57 comp-desktop kernel: [ 3931.528067] usb 5-1: new low speed USB device using uhci_hcd and address 68
Jun 29 16:07:58 comp-desktop kernel: [ 3932.088067] usb 5-1: new low speed USB device using uhci_hcd and address 69
Jun 29 16:07:58 comp-desktop kernel: [ 3932.608045] usb 5-1: new low speed USB device using uhci_hcd and address 70
Jun 29 16:08:05 comp-desktop kernel: [ 3939.392028] usb 5-1: new low speed USB device using uhci_hcd and address 72
Jun 29 16:08:06 comp-desktop kernel: [ 3939.952046] usb 5-1: new low speed USB device using uhci_hcd and address 73
Jun 29 16:08:06 comp-desktop kernel: [ 3940.512052] usb 5-1: new low speed USB device using uhci_hcd and address 74
Jun 29 16:08:07 comp-desktop kernel: [ 3941.032054] usb 5-1: new low speed USB device using uhci_hcd and address 75
Jun 29 16:08:36 comp-desktop kernel: [ 3970.888049] usb 5-1: new low speed USB device using uhci_hcd and address 76
Jun 29 16:08:37 comp-desktop kernel: [ 3971.448057] usb 5-1: new low speed USB device using uhci_hcd and address 77
Jun 29 16:08:38 comp-desktop kernel: [ 3972.008065] usb 5-1: new low speed USB device using uhci_hcd and address 78
Jun 29 16:08:38 comp-desktop kernel: [ 3972.528051] usb 5-1: new low speed USB device using uhci_hcd and address 79
Jun 29 16:08:40 comp-desktop kernel: [ 3974.856048] usb 5-1: new low speed USB device using uhci_hcd and address 80
Jun 29 16:08:41 comp-desktop kernel: [ 3975.892058] usb 5-1: new low speed USB device using uhci_hcd and address 82
Jun 29 16:08:42 comp-desktop kernel: [ 3976.592049] usb 5-1: new low speed USB device using uhci_hcd and address 83
Jun 29 16:08:43 comp-desktop kernel: [ 3977.584052] usb 5-1: new low speed USB device using uhci_hcd and address 84
Jun 29 16:08:44 comp-desktop kernel: [ 3978.152027] usb 5-1: new low speed USB device using uhci_hcd and address 85
Jun 29 16:08:44 comp-desktop kernel: [ 3978.716051] usb 5-1: new low speed USB device using uhci_hcd and address 86
Jun 29 16:08:45 comp-desktop kernel: [ 3979.236049] usb 5-1: new low speed USB device using uhci_hcd and address 87
Jun 29 16:09:34 comp-desktop kernel: [ 4028.400048] usb 5-1: new low speed USB device using uhci_hcd and address 88
Jun 29 16:09:35 comp-desktop kernel: [ 4028.960038] usb 5-1: new low speed USB device using uhci_hcd and address 89
Jun 29 16:09:35 comp-desktop kernel: [ 4029.520051] usb 5-1: new low speed USB device using uhci_hcd and address 90
Jun 29 16:09:36 comp-desktop kernel: [ 4030.040065] usb 5-1: new low speed USB device using uhci_hcd and address 91
Jun 29 16:09:40 comp-desktop kernel: [ 4034.128052] usb 5-1: new low speed USB device using uhci_hcd and address 92
Jun 29 16:09:40 comp-desktop kernel: [ 4034.688028] usb 5-1: new low speed USB device using uhci_hcd and address 93
Jun 29 16:09:41 comp-desktop kernel: [ 4035.248050] usb 5-1: new low speed USB device using uhci_hcd and address 94
Jun 29 16:09:41 comp-desktop kernel: [ 4035.768050] usb 5-1: new low speed USB device using uhci_hcd and address 95
Jun 29 16:10:19 comp-desktop pppd[5281]: Modem hangup
Jun 29 16:10:19 comp-desktop kernel: [ 4073.568497] usb 5-2: USB disconnect, address 125
Jun 29 16:10:19 comp-desktop pppd[5281]: Connect time 28.0 minutes.
Jun 29 16:10:19 comp-desktop pppd[5281]: Sent 856679 bytes, received 3313257 bytes.
Jun 29 16:10:19 comp-desktop pppd[5281]: Connection terminated.
Jun 29 16:10:20 comp-desktop pppd[5281]: Exit.
Jun 29 16:10:37 comp-desktop kernel: [ 4091.068050] usb 1-8: new high speed USB device using ehci_hcd and address 108
Jun 29 16:10:37 comp-desktop kernel: [ 4091.248312] usb 1-8: configuration #1 chosen from 1 choice
Jun 29 16:10:37 comp-desktop kernel: [ 4091.257178] scsi296 : SCSI emulation for USB Mass Storage devices
Jun 29 16:10:37 comp-desktop kernel: [ 4091.257962] scsi297 : SCSI emulation for USB Mass Storage devices
Jun 29 16:10:37 comp-desktop kernel: [ 4091.408033] usb 5-1: new low speed USB device using uhci_hcd and address 96
Jun 29 16:10:38 comp-desktop kernel: [ 4091.976031] usb 5-1: new low speed USB device using uhci_hcd and address 97
Jun 29 16:10:38 comp-desktop kernel: [ 4092.536058] usb 5-1: new low speed USB device using uhci_hcd and address 98
Jun 29 16:10:39 comp-desktop kernel: [ 4093.056029] usb 5-1: new low speed USB device using uhci_hcd and address 99
Jun 29 16:10:40 comp-desktop kernel: [ 4094.467589] usb 1-8: usbfs: process 5535 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:41 comp-desktop kernel: [ 4095.494895] usb 1-8: usbfs: process 5537 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:41 comp-desktop kernel: [ 4095.501254] usb 1-8: usbfs: process 5539 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:42 comp-desktop kernel: [ 4096.388053] usb 1-8: reset high speed USB device using ehci_hcd and address 108
Jun 29 16:10:42 comp-desktop kernel: [ 4096.530896] scsi298 : SCSI emulation for USB Mass Storage devices
Jun 29 16:10:42 comp-desktop kernel: [ 4096.534771] usb 1-8: usbfs: process 5541 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:42 comp-desktop kernel: [ 4096.652045] usb 1-8: reset high speed USB device using ehci_hcd and address 108
Jun 29 16:10:43 comp-desktop kernel: [ 4096.924049] usb 1-8: reset high speed USB device using ehci_hcd and address 108
Jun 29 16:10:43 comp-desktop kernel: [ 4097.220051] usb 1-8: reset high speed USB device using ehci_hcd and address 108
Jun 29 16:10:43 comp-desktop kernel: [ 4097.406656] scsi299 : SCSI emulation for USB Mass Storage devices
Jun 29 16:10:43 comp-desktop kernel: [ 4097.532055] usb 1-8: reset high speed USB device using ehci_hcd and address 108
Jun 29 16:10:43 comp-desktop kernel: [ 4097.673897] scsi300 : SCSI emulation for USB Mass Storage devices
Jun 29 16:10:44 comp-desktop kernel: [ 4098.087371] usb 1-8: usbfs: process 5546 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:44 comp-desktop kernel: [ 4098.090777] usb 1-8: usbfs: process 5547 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:44 comp-desktop kernel: [ 4098.416486] usb 1-8: usbfs: process 5552 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:44 comp-desktop kernel: [ 4098.683605] usb 1-8: usbfs: process 5557 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:45 comp-desktop kernel: [ 4099.104992] usb 1-8: usbfs: process 5559 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:45 comp-desktop kernel: [ 4099.106976] usb 1-8: usbfs: process 5558 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:45 comp-desktop kernel: [ 4099.425979] usb 1-8: usbfs: process 5560 (modem-modeswitc) did not claim interface 0 before use
Jun 29 16:10:45 comp-desktop kernel: [ 4099.477526] usb 1-8: USB disconnect, address 108
Jun 29 16:10:51 comp-desktop kernel: [ 4105.860052] usb 1-8: new high speed USB device using ehci_hcd and address 109
Jun 29 16:10:52 comp-desktop kernel: [ 4106.051884] usb 1-8: configuration #1 chosen from 1 choice
Jun 29 16:10:52 comp-desktop kernel: [ 4106.078727] option 1-8:1.0: GSM modem (1-port) converter detected
Jun 29 16:10:52 comp-desktop kernel: [ 4106.078985] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
Jun 29 16:10:52 comp-desktop kernel: [ 4106.079516] option 1-8:1.1: GSM modem (1-port) converter detected
Jun 29 16:10:52 comp-desktop kernel: [ 4106.079763] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
Jun 29 16:10:52 comp-desktop kernel: [ 4106.081467] option 1-8:1.2: GSM modem (1-port) converter detected
Jun 29 16:10:52 comp-desktop kernel: [ 4106.081713] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
Jun 29 16:10:52 comp-desktop kernel: [ 4106.082257] option 1-8:1.3: GSM modem (1-port) converter detected
Jun 29 16:10:52 comp-desktop kernel: [ 4106.082486] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB3
Jun 29 16:10:52 comp-desktop kernel: [ 4106.083938] scsi305 : SCSI emulation for USB Mass Storage devices
Jun 29 16:10:52 comp-desktop kernel: [ 4106.086562] scsi306 : SCSI emulation for USB Mass Storage devices
Jun 29 16:10:52 comp-desktop kernel: [ 4106.212057] usb 5-1: new low speed USB device using uhci_hcd and address 100
Jun 29 16:10:52 comp-desktop kernel: [ 4106.772049] usb 5-1: new low speed USB device using uhci_hcd and address 101
Jun 29 16:10:53 comp-desktop kernel: [ 4107.332050] usb 5-1: new low speed USB device using uhci_hcd and address 102
Jun 29 16:10:53 comp-desktop kernel: [ 4107.852051] usb 5-1: new low speed USB device using uhci_hcd and address 103
Jun 29 16:10:57 comp-desktop kernel: [ 4111.095458] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jun 29 16:10:57 comp-desktop kernel: [ 4111.095497] option 1-8:1.0: device disconnected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.095779] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jun 29 16:10:57 comp-desktop kernel: [ 4111.095830] option 1-8:1.1: device disconnected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.102148] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jun 29 16:10:57 comp-desktop kernel: [ 4111.102383] option 1-8:1.2: device disconnected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.104234] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
Jun 29 16:10:57 comp-desktop kernel: [ 4111.104465] option 1-8:1.3: device disconnected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.105150] scsi 306:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
Jun 29 16:10:57 comp-desktop kernel: [ 4111.216051] usb 1-8: reset high speed USB device using ehci_hcd and address 109
Jun 29 16:10:57 comp-desktop kernel: [ 4111.417143] option 1-8:1.3: GSM modem (1-port) converter detected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.417379] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
Jun 29 16:10:57 comp-desktop kernel: [ 4111.421195] option 1-8:1.2: GSM modem (1-port) converter detected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.421440] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
Jun 29 16:10:57 comp-desktop kernel: [ 4111.424824] option 1-8:1.1: GSM modem (1-port) converter detected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.425103] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
Jun 29 16:10:57 comp-desktop kernel: [ 4111.427246] option 1-8:1.0: GSM modem (1-port) converter detected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.427531] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB3
Jun 29 16:10:57 comp-desktop kernel: [ 4111.435154] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
Jun 29 16:10:57 comp-desktop kernel: [ 4111.435212] option 1-8:1.0: device disconnected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.435449] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jun 29 16:10:57 comp-desktop kernel: [ 4111.435497] option 1-8:1.1: device disconnected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.435639] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jun 29 16:10:57 comp-desktop kernel: [ 4111.435682] option 1-8:1.2: device disconnected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.435822] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jun 29 16:10:57 comp-desktop kernel: [ 4111.435866] option 1-8:1.3: device disconnected
Jun 29 16:10:57 comp-desktop kernel: [ 4111.504055] usb 5-1: new low speed USB device using uhci_hcd and address 104
Jun 29 16:10:58 comp-desktop kernel: [ 4112.068062] usb 5-1: new low speed USB device using uhci_hcd and address 105
Jun 29 16:10:58 comp-desktop kernel: [ 4112.628180] usb 5-1: new low speed USB device using uhci_hcd and address 106
Jun 29 16:10:59 comp-desktop kernel: [ 4113.148049] usb 5-1: new low speed USB device using uhci_hcd and address 107
Jun 29 16:10:59 comp-desktop kernel: [ 4113.668047] usb 1-8: reset high speed USB device using ehci_hcd and address 109
Jun 29 16:10:59 comp-desktop kernel: [ 4113.840643] option 1-8:1.3: GSM modem (1-port) converter detected
Jun 29 16:10:59 comp-desktop kernel: [ 4113.840886] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
Jun 29 16:10:59 comp-desktop kernel: [ 4113.841355] option 1-8:1.2: GSM modem (1-port) converter detected
Jun 29 16:10:59 comp-desktop kernel: [ 4113.841585] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
Jun 29 16:10:59 comp-desktop kernel: [ 4113.841981] option 1-8:1.1: GSM modem (1-port) converter detected
Jun 29 16:10:59 comp-desktop kernel: [ 4113.842245] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
Jun 29 16:10:59 comp-desktop kernel: [ 4113.842647] option 1-8:1.0: GSM modem (1-port) converter detected
Jun 29 16:10:59 comp-desktop kernel: [ 4113.842901] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB3
Jun 29 16:10:59 comp-desktop kernel: [ 4113.867441] scsi 305:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Jun 29 16:11:00 comp-desktop kernel: [ 4113.940222] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
Jun 29 16:11:00 comp-desktop kernel: [ 4113.940275] option 1-8:1.0: device disconnected
Jun 29 16:11:00 comp-desktop kernel: [ 4113.940559] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jun 29 16:11:00 comp-desktop kernel: [ 4113.940602] option 1-8:1.1: device disconnected
Jun 29 16:11:00 comp-desktop kernel: [ 4113.940772] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jun 29 16:11:00 comp-desktop kernel: [ 4113.940813] option 1-8:1.2: device disconnected
Jun 29 16:11:00 comp-desktop kernel: [ 4113.940979] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jun 29 16:11:00 comp-desktop kernel: [ 4113.941018] option 1-8:1.3: device disconnected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.052068] usb 1-8: reset high speed USB device using ehci_hcd and address 109
Jun 29 16:11:00 comp-desktop kernel: [ 4114.195779] option 1-8:1.3: GSM modem (1-port) converter detected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.195994] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB0
Jun 29 16:11:00 comp-desktop kernel: [ 4114.197276] option 1-8:1.2: GSM modem (1-port) converter detected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.197489] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB1
Jun 29 16:11:00 comp-desktop kernel: [ 4114.197913] option 1-8:1.1: GSM modem (1-port) converter detected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.198147] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB2
Jun 29 16:11:00 comp-desktop kernel: [ 4114.198551] option 1-8:1.0: GSM modem (1-port) converter detected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.198790] usb 1-8: GSM modem (1-port) converter now attached to ttyUSB3
Jun 29 16:11:00 comp-desktop kernel: [ 4114.225006] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
Jun 29 16:11:00 comp-desktop kernel: [ 4114.225195] option 1-8:1.0: device disconnected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.225649] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Jun 29 16:11:00 comp-desktop kernel: [ 4114.225818] option 1-8:1.1: device disconnected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.226192] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Jun 29 16:11:00 comp-desktop kernel: [ 4114.226361] option 1-8:1.2: device disconnected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.226777] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Jun 29 16:11:00 comp-desktop kernel: [ 4114.226962] option 1-8:1.3: device disconnected
Jun 29 16:11:00 comp-desktop kernel: [ 4114.336175] usb 1-8: USB disconnect, address 109
Jun 29 16:11:00 comp-desktop kernel: [ 4114.337145] sr2: scsi3-mmc drive: 0x/0x caddy
Jun 29 16:11:00 comp-desktop kernel: [ 4114.337613] sr 305:0:0:0: Attached scsi generic sg3 type 5
Jun 29 16:11:00 comp-desktop kernel: [ 4114.338138] sd 306:0:0:0: Attached scsi generic sg4 type 0
Jun 29 16:11:00 comp-desktop kernel: [ 4114.361797] sd 306:0:0:0: [sdb] READ CAPACITY failed
Jun 29 16:11:00 comp-desktop kernel: [ 4114.361805] sd 306:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun 29 16:11:00 comp-desktop kernel: [ 4114.361811] sd 306:0:0:0: [sdb] Sense not available.
Jun 29 16:11:00 comp-desktop kernel: [ 4114.361843] sd 306:0:0:0: [sdb] Write Protect is off
Jun 29 16:11:00 comp-desktop kernel: [ 4114.363033] sd 306:0:0:0: [sdb] READ CAPACITY failed
Jun 29 16:11:00 comp-desktop kernel: [ 4114.363041] sd 306:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Jun 29 16:11:00 comp-desktop kernel: [ 4114.363047] sd 306:0:0:0: [sdb] Sense not available.
Jun 29 16:11:00 comp-desktop kernel: [ 4114.363086] sd 306:0:0:0: [sdb] Attached SCSI removable disk
Jun 29 16:11:12 comp-desktop kernel: [ 4126.136060] usb 5-1: new low speed USB device using uhci_hcd and address 108
Jun 29 16:11:12 comp-desktop kernel: [ 4126.856059] usb 5-1: new low speed USB device using uhci_hcd and address 109
Jun 29 16:11:13 comp-desktop kernel: [ 4127.416047] usb 5-1: new low speed USB device using uhci_hcd and address 110
Jun 29 16:11:14 comp-desktop kernel: [ 4127.976099] usb 5-1: new low speed USB device using uhci_hcd and address 111
Jun 29 16:11:14 comp-desktop kernel: [ 4128.496044] usb 5-1: new low speed USB device using uhci_hcd and address 112
Jun 29 16:11:26 comp-desktop kernel: [ 4140.520061] usb 5-1: new low speed USB device using uhci_hcd and address 113
Jun 29 16:11:27 comp-desktop kernel: [ 4141.084065] usb 5-1: new low speed USB device using uhci_hcd and address 114
Jun 29 16:11:27 comp-desktop kernel: [ 4141.644091] usb 5-1: new low speed USB device using uhci_hcd and address 115
Jun 29 16:11:28 comp-desktop kernel: [ 4142.164141] usb 5-1: new low speed USB device using uhci_hcd and address 116
Jun 29 16:11:43 comp-desktop kernel: [ 4157.576057] usb 5-1: new low speed USB device using uhci_hcd and address 117
Jun 29 16:11:44 comp-desktop kernel: [ 4158.144038] usb 5-1: new low speed USB device using uhci_hcd and address 118
Jun 29 16:11:44 comp-desktop kernel: [ 4158.712049] usb 5-1: new low speed USB device using uhci_hcd and address 119
Jun 29 16:11:45 comp-desktop kernel: [ 4159.232068] usb 5-1: new low speed USB device using uhci_hcd and address 120

can anyone PLEASE help me and tell me whats wrong? I will be really grateful. For starters, I think there is some problem with the usb-modeswitch scripts involved. Please tell me what should I do.

---

### Post by dineshs on 2010-06-29
I think your device is detected as a modem.Pl try any of the methods described in
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
to connect / disconnect
This is a guide by alexfish
[http://ubuntuforums.org/showthread.php?t=1466490](http://ubuntuforums.org/showthread.php?t=1466490)

---

### Post by alexfish on 2010-06-29
hi

are you booting the computer with the device connected, if so then it looks as if the device drivers and pppd are loading on boot . When this happens the device will not be recognised by the network manager. So it would be reasonable to plug the device in after boot or kill the pppd from the terminal

Code:

Killall pppd


another question to ask is , does the device work without the usb modeswitch

regards

alexfish

PS you have started another Thread here to loop back to this thread

[http://ubuntuforums.org/showthread.php?t=1520177](http://ubuntuforums.org/showthread.php?t=1520177)

---

### Post by Knutsch on 2010-07-02
hi

A few days ago I ordered a UMTS USB-stick from Fonic and I received a Huawei model E1550. Win and Mac install files are on the stick, but nothing for Linux. I found for the USB Modeswitch "drivers" at [www.draisberghof.de/usb_modeswitsch/]("http://www.draisberghof.de/usb_modeswitsch/") but, (nothing about the program source on the producers web page - strange)  the install gave me a lot of errors, and after a while, I decide to find another "approach".

I think you might find this useful. This is my approach for Ubuntu 10.4 LTS.

Open your terminal and type:

 #  sudo apt-get install udev-extras

and add a new udev rule:
#   gksu gedit /etc/udev/rules.d/15-huawei-e1550.rules

In the pop-up window make the rule like this:

SUBSYSTEM=="usb",
SYSFS{idProduct}=="1446",
SYSFS{idVendor}=="12d1",
RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

save and close, and if the mobile broadband connection is already set, and the device plugged, it will connect after a few seconds.


;) have fun
greets

---

### Post by Ophidion on 2010-11-28
Updated file to the previous post is:

SUBSYSTEM=="usb",
ATTR{idVendor}=="12d1",
ATTR{idProduct}=="1446",
RUN+="/lib/udev/modem-modeswitch -v 0x%s{idVendor} -p 0x%s{idProduct} -t option-zerocd"

the other file in the previous post will cause a warning or an error message. whatever!
the modem also will hang the computer completely on heavy work, or may be on plugging another usb drive.

I updated my file to the new one i have just written.

then you must edit the file usb_modeswitch.conf or create it with these contents:

# Configuration for the usb_modeswitch package, a mode switching tool for
# USB devices providing multiple states or modes
#
# This file is evaluated by the wrapper script "usb_modeswitch_dispatcher"
# in /usr/sbin
# To enable an option, set it to "1", "yes" or "true" (case doesn't matter)
# Everything else counts as "disable"


# Disable automatic mode switching globally (e.g. to access the original
# install storage)

DisableSwitching=0


# Enable logging (results in a extensive report file in /var/log, named
# "usb_modeswitch_<interface-name>"

EnableLogging=0

DefaultVendor=  0x12d1;
DefaultProduct= 0x1446
# choose one of these:
;DetachStorageOnly=1
HuaweiMode=1

that will be more correct.
if anything new appeared i will be back here
hope this is better.

---

### Post by Ophidion on 2010-11-29
I am back
I found out that the last line in the file (15-huawei-e1550.rules) caused the system not to mount or even see USB disks.
so I came back with this file contents in (15-huawei-e1550.rules):

SUBSYSTEM=="usb",
ATTR{idVendor}=="12d1",
ATTR{idProduct}=="1446",
RUN+="/lib/udev/modem-modeswitch --vendor 0x12d1 --product 0x1446 --type option-zerocd"

The file (usb_modeswitch.conf) is not important at all to be edited unless your modem is continuously disconnect then I will be later here to verify its contents as I found many to be written to it, but I consider my previous post about that file convenient for now or even don't create or edit the file (usb_modeswitch.conf) unless you have problems.

watching

---

