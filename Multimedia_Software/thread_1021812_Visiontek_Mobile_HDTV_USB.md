---
title: "Visiontek Mobile HDTV USB"
date: 2008-12-25
forum: Multimedia Software
---

### Post by Zachs Kappler on 2008-12-25
I got a Visiontek Mobile HDTV USB stick and enjoy using it on my computers that run Windows. My problem is I want to use it on my Ubuntu 8.10 laptop since it's the one I needed it for. Any programs or tricks to make Ubuntu see it?

---

### Post by Tea4all on 2008-12-28
I have the same problem. Any help?

---

### Post by xc3RnbFO8P on 2008-12-28
In Terminal show the output of **lsusb**

---

### Post by Zachs Kappler on 2008-12-28
> **Ringi said:**
> In Terminal show the output of **lsusb**

Bus 004 Device 012: ID 413c:5106 Dell Computer Corp. 
Bus 004 Device 011: ID 413c:5105 Dell Computer Corp. AIO Printer A920
Bus 004 Device 010: ID 057b:0000 Y-E Data, Inc. FlashBuster-U Floppy
Bus 004 Device 009: ID 05e1:0400 Syntek Semiconductor Co., Ltd 
Bus 004 Device 008: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 004 Device 006: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 004: ID 056a:0017 Wacom Co., Ltd 
Bus 004 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:00e3 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I have the following connected up at this point...

Two USB ports on my machine
|-Microsoft Wireless Comfort keyboad and Wireless Optical Mouse 2.0
|-GigaWare hub (7 port model)
| |-Dell AIO printer
| |-USB Floppy drive
| |-The TV tuner in question
| |-Cooling base
| |-Wacom Bamboo Fun Tablet

Now when I remove it...

Bus 004 Device 012: ID 413c:5106 Dell Computer Corp. 
Bus 004 Device 011: ID 413c:5105 Dell Computer Corp. AIO Printer A920
Bus 004 Device 010: ID 057b:0000 Y-E Data, Inc. FlashBuster-U Floppy
Bus 004 Device 008: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 004 Device 006: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 004: ID 056a:0017 Wacom Co., Ltd 
Bus 004 Device 003: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 045e:00e3 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

That "Syntek Semiconductor, Inc." entry must be it...

---

### Post by xc3RnbFO8P on 2008-12-28
Show output of **dmesg** just the TV part.

I just adding the information that I have found:
> AnyTV AUTV002 USB Tuner Stick from DealExtreme

auvitek 
au0828 driver
[http://marc.info/?l=linux-dvb&m=122472907625204&w=2](http://marc.info/?l=linux-dvb&m=122472907625204&w=2)
Bus 001 Device 011: ID 05e1:0400 Syntek Semiconductor Co., Ltd
[http://www.linuxtv.org/pipermail/linux-dvb/2008-November/030537.html](http://www.linuxtv.org/pipermail/linux-dvb/2008-November/030537.html)

---

### Post by Zachs Kappler on 2008-12-28
> **Ringi said:**
> Show output of **dmesg** just the TV part.

Is there a way to single out certain messages in dmesg? Or should I include messages that mention usb? (I haven't used dmesg much and lack knowledge about its switches.)

---

