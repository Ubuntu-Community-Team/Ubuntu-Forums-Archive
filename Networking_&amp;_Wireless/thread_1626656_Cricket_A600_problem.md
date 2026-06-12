---
title: "Cricket A600 problem"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by bvtest on 2010-11-20
Hi there3,I seem to be having trouble with my cricket A600 modem I have downloaded the required software to fix it but when I execute ''flipflop.sh'' I get the following error:
> usb_modeswitch: tool for controlling "flip flop" mode USB devices
* Version 0.9.7 (C) Josua Dietze 2009
* Works with libusb 0.1.12 and probably other versions
Looking for target devices ...
Found devices in target mode or class (1)
Looking for default devices ...
Found default devices (1)
Found a default device NOT in target class mode
Prepare switching, accessing device 000 on bus 003 ...
Looking for active driver ...
No driver found. Either detached before or never attached
Setting up communication with interface 0 ...
Could not claim interface (error -1). Skipping message sending
-> Run lsusb to note any changes. Bye
Oh and before you ask my device is plugged in.

---

### Post by uncaspi on 2010-11-20
It says no driver found.

---

### Post by bvtest on 2010-11-21
I know that,however the driver appears on ubuntu.

---

### Post by bvtest on 2010-11-23
Hello?
I'd like a answer please.

---

### Post by alexfish on 2010-11-23
Hi

can you have a look through this thread

[http://ubuntuforums.org/showthread.php?t=343989](http://ubuntuforums.org/showthread.php?t=343989)

if your still stuck

post back here , post info about the device + ubuntu version

alexfish

---

### Post by bvtest on 2010-11-29
Alright. 
My ubuntu version is 10.4 ''lucid lynx''
My cricket modem is a EVDO A600 modem.

---

### Post by alexfish on 2010-11-30
Hi

can post details of these commands from the terminal

Code:

[COLOR=Blue]usb-devices[/COLOR]

Code:

[COLOR=Blue]ls -al /dev/serial/by-id/*[/COLOR]


alexfish

---

### Post by desnaike on 2010-11-30
In ubuntu 10.04 did you install usb-modeswitch-data through synaptic thats all thats really required for it to work.

---

### Post by bvtest on 2010-11-30
> **desnaike said:**
> In ubuntu 10.04 did you install usb-modeswitch-data through synaptic thats all thats really required for it to work.
Im not sure?
Anyway I cant download it now I have no internet connection in ubuntu.

---

### Post by orcaman42 on 2011-04-03
I installed 10.10 and while it's seeing the modem it's not keeping the connection. ideas? Nothing seems to be working mentioned thus far.

---

