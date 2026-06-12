---
title: "ubuntu 10.4 and skype with v-gear camera 0c45:612c not work"
date: 2010-06-23
forum: Multimedia Software
---

### Post by lshulov on 2010-06-23
Hi all!
I have Futjitsu with v-gear camera with Ubuntu 10.4.
When I launch Skype with: 
      LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
on terminal I see:
$ ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

lsusb:
Bus 002 Device 013: ID 0c45:612c Microdia PC Camera (SN9C110)

dmesg:
[319646.220861] usb 2-2: USB disconnect, address 12
[319646.224279] gspca: disconnect complete
[319653.810075] usb 2-2: new full speed USB device using ohci_hcd and address 13
[319654.033563] usb 2-2: configuration #1 chosen from 1 choice
[319654.036467] gspca: probing 0c45:612c
[319654.048304] sonixj: Sonix chip id: 12
[319654.054512] gspca: probe ok

Thanks for any help.

---

### Post by ajgreeny on 2010-06-23
Are you running a 32 or 64 bit system as if it's 64 you will need to change the PRELOAD command, though you will need to search more for the exact path of the .so file needed.

---

### Post by lshulov on 2010-06-23
skype is 32 bit system:
/usr/bin/skype: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.8, stripped 

With LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so camera don't work absolutely.

---

