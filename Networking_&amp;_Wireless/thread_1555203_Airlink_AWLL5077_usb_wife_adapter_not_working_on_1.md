---
title: "Airlink AWLL5077 usb wife adapter not working on 10.04"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by ANew on 2010-08-17
I was trying to setup the driver but was not able to. When
pluged in it installs ** "r8192s_usb" ** driver from staging directory
and wlan1 interface appears but no network are visible.

Then i used the latest driver from Realtek website for
adapter RTL8188 or RTL8192, compiled it, got ** 8712u.ko **
module and installed it. This new driver does not see the
adapter. If i remove the old driver ** r8192s_usb **
new driver 8712u does not install when adapter pluged in.

Any suggestions what driver to use with this adapter?
Maybe Ralink driver? but which one?

Thanks for reply.

---

### Post by Victor Gonzalez on 2010-09-02
Hello, I have the same problem do you fixed it alredy?

i can't fixed myself not even with ndiswrapper

excuse my english is not my native language 

tanks for your time ):P

Ubuntu 8.10

---

### Post by ANew on 2010-09-04
> **Victor Gonzalez said:**
> Hello, I have the same problem do you fixed it alredy?


No, it seams to me neither old ** r8792s_usb ** module
no new ** 8712u ** module does not recognize the adapter. 
I can post * dmesg * output when these modules are loaded,
but that is all.

maybe Ralink driver will work but i have not tryed it. If
anybody had sussess with Ralink drivers please reply.

---

### Post by ANew on 2010-09-05
[UPDATE]

It works with linux driver for Realtek RTL8192SU or RTL8188SU
chipset available from Realtek website. Use the latest tar-file
from 6/30/10, compile it and get ** 8712u.ko ** module.

You may however need to add 8192 device to the list of devices
recognized by driver:

in untar directory in the file

.../driver/rtl8712_8188_8191_8192.../os_intf/linux/ubs_intf.c

add after the line 56 

USB_DEVICE{(0x0bda,0x8192)}

and then compile the module.

---

