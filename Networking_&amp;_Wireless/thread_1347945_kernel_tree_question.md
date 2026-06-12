---
title: "kernel tree question"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by expxe on 2009-12-06
here are the instructions for my wireless card driver

i don't understand step one, what do i do to continue? i'll probably have trouble with the later steps as well, so a more detailed step by step would be much appreciated. thanks

Build instructions:

[B]* Create drivers/net/wireless/acx subdirectory inside
  your kernel tree.[/B]
* BTW, if your kernel has drivers/net/wireless/tiacx directory,
  you already may have acx driver (some different version).
  Decide which one do you want.
* Unpack tarball into drivers/net/wireless/acx directory.
* Add a line to drivers/net/wireless/Makefile:
	obj-m += acx/
* Build your modules as usual (perhaps "make modules modules_install").

This will create acx module.

Remove "acx-obj-y += usb.o" line in Makefile
and "#define CONFIG_ACX_USB 1" line in acx_config.h
if you want PCI-only driver. Ditto for USB-only one.

---

