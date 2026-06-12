---
title: "How To Setup VLC to Use ADS Instant VCD usb?"
date: 2008-06-27
forum: Multimedia Software
---

### Post by bme on 2008-06-27
I use 8.04. This is the output of lsusb:

Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 06e1:a190 ADS Technologies, Inc. Instand VCD Usb Capture
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

How can I setup vlc to use the usb capture to capture video?

---

### Post by llelectronics on 2008-06-27
If your device gets listed in /dev as either video0 or any other videoX device than you might have a chance to get it to work in VLC. 
Just type in the specific /dev/video Devices in the open dialog box of the vlc gui

---

### Post by bme on 2008-06-27
> **llelectronics said:**
> If your device gets listed in /dev as either video0 or any other videoX device than you might have a chance to get it to work in VLC. 
Just type in the specific /dev/video Devices in the open dialog box of the vlc gui

okay /dev/video0 did it....but no sound although the audio dropdown states "track 1".
Now how do I RECORD the video?

---

