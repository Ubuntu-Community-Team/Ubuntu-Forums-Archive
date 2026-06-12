---
title: "Bluetooth suddenly won't turn on Blueman or Gnome BT Man"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by keevill on 2011-02-05
Suddenly on my Sony Vaio running Ubuntu 10.04 32 bit , Bluetooth fails to start/work. 
Here are the details.
Blueman ver1.21 installed but icon shows a red x.
On Mouse hover it shows 'Bluetooth disabled '. 
When I try to start it from the system try icon I get "failed to set bluetooth power". 
I've done all the updates. Uninstalled and re-installed all the Bluetooth service progs I can find in the synaptics package manager inclueding gnome bluetooth manager , pulse audio BT modules.
(I have another issue with a missing network-manager applet but I don't think it's related since BT was working even with that problem and anywat I've posted a request for help for that issue on another forum."

lsusb shows
Bus 005 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 044e:3012 Alps Electric Co., Ltd 
Bus 001 Device 012: ID 044e:3013 Alps Electric Co., Ltd 
Bus 001 Device 011: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 001 Device 010: ID 044e:3011 Alps Electric Co., Ltd 
Bus 001 Device 009: ID 1410:2120 Novatel Wireless 
Bus 001 Device 008: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 001 Device 007: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 006: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 054c:02d5 Sony Corp. 
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Do I need to re-install Ubuntu ?
-keevill-

---

### Post by keevill on 2011-02-07
> **keevill said:**
> Suddenly on my Sony Vaio running Ubuntu 10.04 32 bit , Bluetooth fails to start/work. 
Here are the details.
Blueman ver1.21 installed but icon shows a red x.
On Mouse hover it shows 'Bluetooth disabled '. 
When I try to start it from the system try icon I get "failed to set bluetooth power". 
I've done all the updates. Uninstalled and re-installed all the Bluetooth service progs I can find in the synaptics package manager inclueding gnome bluetooth manager , pulse audio BT modules.
(I have another issue with a missing network-manager applet but I don't think it's related since BT was working even with that problem and anywat I've posted a request for help for that issue on another forum."

lsusb shows
Bus 005 Device 002: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 044e:3012 Alps Electric Co., Ltd 
Bus 001 Device 012: ID 044e:3013 Alps Electric Co., Ltd 
Bus 001 Device 011: ID 044e:3010 Alps Electric Co., Ltd Bluetooth Adapter
Bus 001 Device 010: ID 044e:3011 Alps Electric Co., Ltd 
Bus 001 Device 009: ID 1410:2120 Novatel Wireless 
Bus 001 Device 008: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 001 Device 007: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 006: ID 05ca:183a Ricoh Co., Ltd Visual Communication Camera VGP-VCC7 [R5U870]
Bus 001 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 054c:02d5 Sony Corp. 
Bus 001 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Do I need to re-install Ubuntu ?
-keevill-

I have gone a bit further with this now. I uninstalled ALL bluetooth apps I could find in the synaptics package manager, rebooted twice and started to load them up again.
I can now connect successfully to both of my BT headphones but nothing plays out of them.
It seems that the choice to select the Ad2p profile in the sound preferences is no longer there. I am using Blueman with Pulseaudio and even after selecting the sink option and also the Ad2p option when pairing, this does not appear for selection.
Please can someone help. It was working fine until... well until ....it wasn't !
-keevill-

---

