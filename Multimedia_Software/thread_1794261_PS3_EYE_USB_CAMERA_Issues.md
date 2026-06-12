---
title: "PS3 EYE USB CAMERA Issues"
date: 2011-06-30
forum: Multimedia Software
---

### Post by amacmil on 2011-06-30
I feel this is a very stupid question but I am struggling to get a solution.

I am running Ubuntu 11.04, fresh install (32bit) on a Toshiba Satellite pro laptop and I am unable to get Ubuntu to recognize the camera is plugged in.

When I ran 10.10 it was a simple plug and play approach and I have searched the forums for some guidance with no success.

If anyone can give me a steer or point me in the right direction I would be grateful.

Thanks for reading
A

---

### Post by dyem1 on 2011-06-30
Post the output of ```
lsusb
``` on terminal, to see if your computer recognises it.
 You checked that you are trying to use that webcam, not the integrated webcam?

---

### Post by amacmil on 2011-07-01
Hi sorry should have thought about that before. Here it is:

Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 002: ID 1415:4000 Nam Tai E&E Products Ltd. or OmniVision Technologies, Inc. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The system seem to pick up the usb cam is there, however I am not able to select it in cheese or in vlc.

I have also looked at the log grabber and managed to pull this info out.

Satellite-Pro-L450D kernel: [ 2298.236100] usb 1-3: new high speed USB device using ehci_hcd and address 3
Satellite-Pro-L450D kernel: [ 2298.373945] hub 1-3:1.0: USB hub found
Satellite-Pro-L450D kernel: [ 2298.374533] hub 1-3:1.0: 1 port detected

I am a little lost on what to do next, thank you again for any advise.

---

### Post by amacmil on 2011-07-01
Darn should have said the Chicony Electronics input is the built in webcam on the laptop, however I don't want to use it in this situation.

Also I have stumbled across this forum post regarding ehci_hcd

[http://ubuntuforums.org/showthread.php?t=89266](http://ubuntuforums.org/showthread.php?t=89266)

however when i try to do a modeprobe -r I get a return of:

FATAL: Module ehci_hcd is builtin

will keep looking.

I have then just found this which sounds promising but no solution clearly defined as yet.

[http://ubuntuforums.org/showthread.php?t=1110609](http://ubuntuforums.org/showthread.php?t=1110609)

---

### Post by no2498 on 2011-07-02
you may try setting it to the com you wish to use in gstreamer-properties
in a terminal type gstreamer-properties click enter
click video set it to the cam you like

also this may find the cam 
in a terminal type dmesg click enter

---

### Post by amacmil on 2011-07-03
unfortunately neither approach worked. as far as i can tell the system recognises the device as i plug them in but no action is taken to assign/mount the device.

---

### Post by no2498 on 2011-07-04
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

hope you find a fix

---

### Post by amacmil on 2011-07-12
Thank you with a bit more reading i got it to work.

---

