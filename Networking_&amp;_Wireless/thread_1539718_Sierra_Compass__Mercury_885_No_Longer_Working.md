---
title: "Sierra Compass / Mercury 885 No Longer Working"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by juddco on 2010-07-26
First post by an Ubuntu newbie.  If I can get this working, I might remove the Windows dual boot from my machine.  :-)  

Ubuntu 10.04, Dell Latitude e6410 laptop.  

I have a Sierra Compass 885 (AKA Mercury) 3g USB Connect modem.  I downloaded and installed the driver from Sierra's site before I figured out that it had kernel support.  That might be my problem, but I had it working for a while.

The other night, I plugged the modem into a different USB port so I could plug a mouse up to that port.  Not sure if that matters, but that was the first time it didn't work.  I tried re-installing the driver, removing and adding the connection, and a whole bunch of other stuff that's probably made the problem worse and not better.  I've read every thread I can find about this device, and no one else seems to have my problem with Lynx.  

Here is the output of lsusb:  

  	 	 	 	 	```
Bus 002 Device 014: ID 1199:6880 Sierra Wireless, Inc.  
 Bus 002 Device 012: ID 03f0:3207 Hewlett-Packard  
 Bus 002 Device 004: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor 
 Bus 002 Device 003: ID 413c:8187 Dell Computer Corp. DW375 Bluetooth Module 
 Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 001 Device 003: ID 05ca:1814 Ricoh Co., Ltd HD Webcam 
 Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

```

Here is the output of dmesg:
```

  	 	 	 	 	<!-- 		@page { margin: 0.79in } 		P { margin-bottom: 0.08in } 	--> 	  [ 4541.813373] usb 2-1.3: new high speed USB device using ehci_hcd and address 15 
 [ 4541.918571] usb 2-1.3: configuration #1 chosen from 1 choice 
 [ 4541.929169] usb-storage: probe of 2-1.3:1.0 failed with error -5 
 [ 4541.929596] usb 2-1.3: USB disconnect, address 15 
 [ 4542.128428] usb 2-1.3: new high speed USB device using ehci_hcd and address 16 
 [ 4542.241862] usb 2-1.3: configuration #1 chosen from 1 choice 
 [ 4542.284131] sierra 2-1.3:1.0: Sierra USB modem converter detected 
 [ 4542.291329] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4542.291426] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB0 
 [ 4542.292738] sierra 2-1.3:1.1: Sierra USB modem converter detected 
 [ 4542.297850] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4542.297933] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB1 
 [ 4542.300116] sierra 2-1.3:1.2: Sierra USB modem converter detected 
 [ 4542.306202] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4542.306281] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB2 
 [ 4542.307378] sierra 2-1.3:1.3: Sierra USB modem converter detected 
 [ 4542.312583] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4542.312785] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB3 
 [ 4542.313889] sierra 2-1.3:1.4: Sierra USB modem converter detected 
 [ 4542.318943] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4542.319119] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB4 
 [ 4542.320233] sierra 2-1.3:1.5: Sierra USB modem converter detected 
 [ 4542.325071] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4542.325266] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB5 
 [ 4542.326357] sierra 2-1.3:1.6: Sierra USB modem converter detected 
 [ 4542.331678] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4542.331857] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB6 
 [ 4542.332150] scsi16 : SCSI emulation for USB Mass Storage devices 
 [ 4542.332511] usb-storage: device found at 16 
 [ 4542.332515] usb-storage: waiting for device to settle before scanning 
 [ 4547.331065] usb-storage: device scan complete 
 [ 4547.335279] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0 
 [ 4547.335302] sierra 2-1.3:1.0: device disconnected 
 [ 4547.335403] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1 
 [ 4547.335421] sierra 2-1.3:1.1: device disconnected 
 [ 4547.335504] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2 
 [ 4547.335522] sierra 2-1.3:1.2: device disconnected 
 [ 4547.335609] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3 
 [ 4547.335626] sierra 2-1.3:1.3: device disconnected 
 [ 4547.335710] sierra ttyUSB4: Sierra USB modem converter now disconnected from ttyUSB4 
 [ 4547.335727] sierra 2-1.3:1.4: device disconnected 
 [ 4547.335807] sierra ttyUSB5: Sierra USB modem converter now disconnected from ttyUSB5 
 [ 4547.335824] sierra 2-1.3:1.5: device disconnected 
 [ 4547.335904] sierra ttyUSB6: Sierra USB modem converter now disconnected from ttyUSB6 
 [ 4547.335921] sierra 2-1.3:1.6: device disconnected 
 [ 4547.408658] usb 2-1.3: reset high speed USB device using ehci_hcd and address 16 
 [ 4547.516388] sierra 2-1.3:1.6: Sierra USB modem converter detected 
 [ 4547.522689] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4547.522816] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB0 
 [ 4547.526887] sierra 2-1.3:1.5: Sierra USB modem converter detected 
 [ 4547.534873] usb 2-1.3: APM supported, enabling autosuspend. 
 [ 4547.534980] usb 2-1.3: Sierra USB modem converter now attached to ttyUSB1 

[...]

```

Note that it repeats this sequence (starting with "usb 2-13: reset high speed USB device...") four times.

My modem is plugged in, the 'ready to connect' light is flashing, but NetworkManager never picks it up.  Just for kicks, I booted back to Windows and it works like a champ.  

Any ideas?  Thanks in advance!

J

---

### Post by pdc on 2010-07-27
so you have tried RIGHT-CLICK on network manager?

Mobile broadband; Add

country/network

accept; close

LEFT-CLICK on network manager: is your selection showing?

---

### Post by juddco on 2010-07-27
Yes, I've added the mobile broadband connection for ATT Data Connect using the default settings.

No, the connection doesn't show up when I left-click on the wifi fan.

---

### Post by alexfish on 2010-07-27
Boot the computer without the device then connect the device { allow approx 30sec for the device to settle }

open up a terminal and enter this code and post the results

code:
ls -al /dev/serial/by-id/usb*

---

### Post by juddco on 2010-07-27
```
judd@Voyager2Ubuntu:~$ ls -al /dev/serial/by-id/usb*
lrwxrwxrwx 1 root root 13 2010-07-27 16:25 /dev/serial/by-id/usb-Sierra_Wireless__Incorporated_HSPA_Modem_1234567890ABCDEF-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2010-07-27 16:25 /dev/serial/by-id/usb-Sierra_Wireless__Incorporated_HSPA_Modem_1234567890ABCDEF-if01-port0 -> ../../ttyUSB1
lrwxrwxrwx 1 root root 13 2010-07-27 16:25 /dev/serial/by-id/usb-Sierra_Wireless__Incorporated_HSPA_Modem_1234567890ABCDEF-if02-port0 -> ../../ttyUSB2
lrwxrwxrwx 1 root root 13 2010-07-27 16:25 /dev/serial/by-id/usb-Sierra_Wireless__Incorporated_HSPA_Modem_1234567890ABCDEF-if03-port0 -> ../../ttyUSB3
lrwxrwxrwx 1 root root 13 2010-07-27 16:25 /dev/serial/by-id/usb-Sierra_Wireless__Incorporated_HSPA_Modem_1234567890ABCDEF-if04-port0 -> ../../ttyUSB4
lrwxrwxrwx 1 root root 13 2010-07-27 16:25 /dev/serial/by-id/usb-Sierra_Wireless__Incorporated_HSPA_Modem_1234567890ABCDEF-if05-port0 -> ../../ttyUSB5
lrwxrwxrwx 1 root root 13 2010-07-27 16:25 /dev/serial/by-id/usb-Sierra_Wireless__Incorporated_HSPA_Modem_1234567890ABCDEF-if06-port0 -> ../../ttyUSB6
```

---

### Post by juddco on 2010-07-27
OK, weird but good...

I ran the command you gave me, and then I plugged in the network cable to provide the response.  When I reached to unplug the cable, I noticed that the solid blue (connected) light was lit on the modem.  

I unplug the cable and it connects to AT&T via the modem.  

I would prefer to know what happened, but I'm not going to complain!  

Thanks for the help!  

Judd

---

### Post by alexfish on 2010-07-27
hi

sometimes connecting the device after boot helps

the device working after code entered is probably coincidental 

but I feel there is still something amiss / keep monitoring 

send PM if you get further problems

regards

alexfish

---

### Post by juddco on 2010-07-27
Thanks a bunch, I'll write back if it craps out again.

---

