---
title: "problem installation ubuntu 8.04 and hauppauge nova-t stick"
date: 2008-10-10
forum: Multimedia Software
---

### Post by davidtuti on 2008-10-10
Hi,

I'm newbie with myhtTV and I try to install hauppauge nova-t stick win ubuntu 8.04.

I've created a card:
DVB DTV capture card (v.3.x)
Db device number : 0
Fronted ID: DIBcom 700MA/MB....
Signal:500
Tuning: 3000

But when I clik on channel don't appears any channel.

Could you help me? Many thanks and sorry for my english

---

### Post by xc3RnbFO8P on 2008-10-10
In Terminal **lsusb** , show the output.

---

### Post by davidtuti on 2008-10-10
> **Ringi said:**
> In Terminal **lsusb** , show the output.

david@david-desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 2040:7050 Hauppauge Hauppauge Nova-T Stick
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 046d:c51b Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  
david@david-desktop:~$ dmesg | grep -i hau
[   36.981119] dvb-usb: found a 'Hauppauge Nova-T Stick' in warm state.
[   36.981305] DVB: registering new adapter (Hauppauge Nova-T Stick)
[   38.330815] dvb-usb: Hauppauge Nova-T Stick successfully initialized and connected.
david@david-desktop:~$

---

### Post by xc3RnbFO8P on 2008-10-10
If do **dmesg** , do you see **dvb-usb-dib0700-1.10.fw** loaded

---

