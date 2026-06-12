---
title: "Huawei E173 mobile broadband installation"
date: 2011-05-30
forum: Networking &amp; Wireless
---

### Post by D4CH on 2011-05-30
Hello. First off let me say I'm a noob at this. But I try.

I just purchased a mobile broadband connection from 3 in Denmark.

I spent three hours following guides about usb-modeswitch and such. I just couldn't get it to work.

Now, finally, I've come THIS far, but yet no internet.

```
daniel@daniel-laptop:~$ sudo usb_modeswitch

Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
 Found default devices (1)
Accessing device 004 on bus 001 ...
Using endpoints 0x0f (out) and 0x8f (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: HUAWEI  
   Model String: Mass Storage    
Revision String: 2.31
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Setting up communication with interface 0 ...
Trying to send the message to endpoint 0x0f ...
 OK, message successfully sent
 Device is gone, skipping any further commands

Checking for mode switch (max. 20 times, once per second) ...
 Original device is gone already, not checking
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 No new devices in target mode or class found

Mode switch has failed. Bye.
```

I am completely confused on what to do now.

I'm sorry if this is not enough information, please, ask for more.

---

### Post by Lars Noodén on 2011-05-30
I have similar issues with the same model of modem.  It's worked four times, apparently by accident each time.

---

### Post by Matbro on 2011-06-29
Is this solved ?
/Mats

---

### Post by Lars Noodén on 2011-06-29
It's still an issue on my machine, but I have no new data.

---

