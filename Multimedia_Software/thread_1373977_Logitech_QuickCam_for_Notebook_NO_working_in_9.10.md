---
title: "Logitech QuickCam for Notebook NO working in 9.10"
date: 2010-01-06
forum: Multimedia Software
---

### Post by sgf0591 on 2010-01-06
I am having issues with my WebCams and Ubuntu 9.10. I have Logitech Quickcam for Laptop Pro (V-UAR38) and LifeCam vx-700 (vx-500) neither of them works on Ubuntu 9.10(U910). Actually, after I installed U910 my Logitech webcam did not work. I tried most or may be all the forum suggestions without success. They I when and bought a cheap webcam (Lifecam vx-700 {label in the box} or vx-500 {label in the usb cable} and also is not working. The investement is not significant at all, but is getting is my nerves if every time I upgrade Ubuntu I need to buy a compatible webcam; nevertheless, putting a side my child attitude, I would like to know if any of you have any other suggestions or solutions about this problem.

I listed the /dev directory and there is none 'video0'. I used 'lsusb' and the output is as follows:

Bus 001 Device 003: ID 046d:08c3 Logitech, Inc. Camera (Notebooks Pro)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I used skype and cheese and both withe the message 'No camera found'.

I also tried to install 'easycam' without success. confused:

Please help.

---

### Post by sgf0591 on 2010-01-06
I ran 'dmesg' from terminal before and after I connected my usb qickcam and the differences is listed below:

[10373.841081] usb 1-6: new high speed USB device using ehci_hcd and address 4
[10374.150425] usb 1-6: configuration #1 chosen from 1 choice
[10374.155349] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c3)

[10375.155450] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.

[10376.152193] uvcvideo: Failed to query (129) UVC probe control : -110 (exp. 26).
[10376.152207] uvcvideo: Failed to initialize the device (-5).

---

