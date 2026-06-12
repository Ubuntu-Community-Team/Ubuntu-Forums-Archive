---
title: "rt2070sta wireless usb adapter module won't load"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by Euro_Par on 2010-03-05
I am running Jaunty 64 bit and trying to get my USB wireless adapter to install.

Can anyone tell me why I get the following errors ?
Am I missing a package/module that supplies the following missing functions ?

> insmod rt2070sta.ko
insmod: error inserting 'rt2070sta.ko': -1 Unknown symbol in module

> dmesg -c

[ 6366.432624] rt2070sta: Unknown symbol usb_alloc_urb
[ 6366.432746] rt2070sta: Unknown symbol usb_free_urb
[ 6366.433042] rt2070sta: Unknown symbol usb_register_driver
[ 6366.433311] rt2070sta: Unknown symbol usb_put_dev
[ 6366.433403] rt2070sta: Unknown symbol usb_get_dev
[ 6366.433589] rt2070sta: Unknown symbol usb_submit_urb
[ 6366.434039] rt2070sta: Unknown symbol usb_control_msg
[ 6366.434326] rt2070sta: Unknown symbol usb_deregister
[ 6366.434752] rt2070sta: Unknown symbol usb_kill_urb
[ 6366.434874] rt2070sta: Unknown symbol usb_buffer_free
[ 6366.435257] rt2070sta: Unknown symbol usb_buffer_alloc

> lsmod |grep usb
usblp                  22656  0 
usbhid                 47040  0 
usb_storage           115520  1 

Thanks in advance.

---

