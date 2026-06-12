---
title: "Webcam detected but not working"
date: 2010-10-04
forum: Multimedia Software
---

### Post by Israphel on 2010-10-04
```

kaworu@ENE:~$ lsusb
Bus 002 Device 008: ID 0c45:60fc Microdia PC Camera with Mic (SN9C105)
Bus 002 Device 002: ID 0458:0076 KYE Systems Corp. (Mouse Systems) 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


kaworu@ENE:~$ dmesg
[  677.580060] usb 2-8: new full speed USB device using ohci_hcd and address 7
[  677.812069] usb 2-8: SN9C105 PC Camera Controller detected (vid:pid 0x0C45:0x60FC)
[  677.896067] usb 2-8: HV7131R image sensor detected
[  678.862065] usb 2-8: Initialization succeeded
[  678.862242] usb 2-8: V4L2 device registered as video0
[  678.862247] usb 2-8: Optional device control through 'sysfs' interface disabled
[  678.871963] usb 2-8: usb_submit_urb() failed, error -28
[  678.896164] ohci_hcd 0000:00:0b.0: leak ed ffff880037759370 (#81) state 2
[  678.896193] usb 2-8: usb_submit_urb() failed, error -28


kaworu@ENE:~$ guvcview -d /dev/video0
guvcview 1.4.1
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
video device: /dev/video0 
ERROR opening V4L interface for /dev/video0
unable to detect video devices on your system (0)
ERROR opening V4L interface: No space left on device
Init video returned -1
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.

```

Kubuntu Maverick RC 64 Bits.

The camera works on Ubuntu Lucid 32 Bits.

Edit: I was an USB problem. I can't use the frontal connector.

---

