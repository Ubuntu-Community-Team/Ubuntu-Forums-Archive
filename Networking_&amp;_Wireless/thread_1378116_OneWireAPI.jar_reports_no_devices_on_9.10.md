---
title: "OneWireAPI.jar reports no devices on 9.10"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by mikeklein on 2010-01-11
I have an older DS9097 serial adapter (tried via usb and direct serial) and OneWireAPI.jar when run shows no devices under adapter.

I am running 9.10 64-bit on a quadcore.

All onewire utils report the adapter but nothing connected to it.

All other serial devices (cid modem, lcd/keypad serial) are working via rxtx with either usb or direct serial...just not onewire.

I really don't want to use OWFS as I merely need to read simple values and have no need for httpd support, etc.

I will start basic triage by trying adapter on another system, on windows laptop, etc.

Just wondering if anybody has hit this issue with onewire on linux.


thanks in advance,

mike

---

### Post by millersc451 on 2010-01-20
I'm also running 9.10 64-bit and having problems.  What RXTX are you using?  If you're not using librxtx from the repositories, where did you install librxtx.so and OneWireAPI.jar?  

I think my problem is either the API or RXTX.  I'm using Sun Java, the latest OneWireAPI.jar and librxtx from the repositories.  

The online OneWireViewer finds my DS9097U (newer version), but crashes when going to the next screen.

I'm using a Sarbent PL2303 USB-Serial adapter and also connecting directly to an RS232 port (two different laptops).  It works fine under windows XP.  Under Linux, digitemp found the devices using the USB-Serial adapter, so it looks like either a OneWireAPI.jar problem or RXTX problem.

I had success with mango serotonin using this DS9087U, so I know it can work.  I was using 8.10 32-bit.

---

