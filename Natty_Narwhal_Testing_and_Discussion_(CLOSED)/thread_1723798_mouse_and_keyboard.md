---
title: "mouse and keyboard"
date: 2011-04-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by mdhollis on 2011-04-07
Anyone having issues with their mouse and keyboard after latest updates?

---

### Post by mdhollis on 2011-04-07
Yeah I can't even Ctrl Alt F2.  Not to big of a deal because I'm running this on an old machine.  I installed the latest updates and after a reboot everything boots up fine I just can't control my mouse.

---

### Post by vwchris on 2011-04-07
I'm having tons of issues with USBHID after latest updates.  No USB devices functioning (Mouse, Keyboard, etc).  Errors in syslog:


Apr  7 16:03:27 arwyn kernel: [    7.980438] usbcore: registered new interface driver usb-storage
Apr  7 16:03:27 arwyn kernel: [    7.989420] USB Mass Storage support registered.
Apr  7 16:03:27 arwyn kernel: [    8.020028] usb 3-1: new full speed USB device using ohci_hcd and address 2
Apr  7 16:03:27 arwyn kernel: [    8.280465] usbhid: disagrees about version of symbol hid_output_report
Apr  7 16:03:27 arwyn kernel: [    8.289153] usbhid: Unknown symbol hid_output_report (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.298230] usbhid: disagrees about version of symbol hid_unregister_driver
Apr  7 16:03:27 arwyn kernel: [    8.306825] usbhid: Unknown symbol hid_unregister_driver (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.315830] usbhid: disagrees about version of symbol __hid_register_driver
Apr  7 16:03:27 arwyn kernel: [    8.324405] usbhid: Unknown symbol __hid_register_driver (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.333104] usbhid: disagrees about version of symbol hid_allocate_device
Apr  7 16:03:27 arwyn kernel: [    8.341631] usbhid: Unknown symbol hid_allocate_device (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.350218] usbhid: disagrees about version of symbol hid_destroy_device
Apr  7 16:03:27 arwyn kernel: [    8.358906] usbhid: Unknown symbol hid_destroy_device (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.368569] usbhid: disagrees about version of symbol hid_set_field
Apr  7 16:03:27 arwyn kernel: [    8.377581] usbhid: Unknown symbol hid_set_field (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.387011] usbhid: disagrees about version of symbol hid_output_report
Apr  7 16:03:27 arwyn kernel: [    8.396359] usbhid: Unknown symbol hid_output_report (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.405866] usbhid: disagrees about version of symbol hid_check_keys_pressed
Apr  7 16:03:27 arwyn kernel: [    8.415405] usbhid: Unknown symbol hid_check_keys_pressed (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.425380] usbhid: disagrees about version of symbol hid_unregister_driver
Apr  7 16:03:27 arwyn kernel: [    8.435069] usbhid: Unknown symbol hid_unregister_driver (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.445401] usbhid: disagrees about version of symbol hid_input_report
Apr  7 16:03:27 arwyn kernel: [    8.455451] usbhid: Unknown symbol hid_input_report (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.466160] usbhid: disagrees about version of symbol hidinput_find_field
Apr  7 16:03:27 arwyn kernel: [    8.476433] usbhid: Unknown symbol hidinput_find_field (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.487103] usbhid: disagrees about version of symbol __hid_register_driver
Apr  7 16:03:27 arwyn kernel: [    8.497328] usbhid: Unknown symbol __hid_register_driver (err -22)
Apr  7 16:03:27 arwyn kernel: [    8.507613] usbhid: disagrees about version of symbol hid_allocate_device

---

### Post by stanz on 2011-04-07
Haven't had usb at all, with this dell laptop.
[Bug #709611]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/709611")

---

