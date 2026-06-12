---
title: "error installing lirc-modules-source"
date: 2010-07-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by skeve on 2010-07-01
Those functions were renamed in the current kernel:
usb_buffer_alloc() is renamed to usb_alloc_coherent()
usb_buffer_free()  is renamed to usb_free_coherent()

but lirc-modules-source still uses the old ones, so there're errors while dkms rebuildes the modules:

```

/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_atiusb/lirc_atiusb.c: In function ‘free_in_endpt’:
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_atiusb/lirc_atiusb.c:825: error: implicit declaration of function ‘usb_buffer_free’
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_atiusb/lirc_atiusb.c: In function ‘new_in_endpt’:
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_atiusb/lirc_atiusb.c:870: error: implicit declaration of function ‘usb_buffer_alloc’
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_atiusb/lirc_atiusb.c:870: warning: assignment makes pointer from integer without a cast
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_atiusb/lirc_atiusb.c: In function ‘new_out_endpt’:
/var/lib/dkms/lirc/0.8.6/build/drivers/lirc_atiusb/lirc_atiusb.c:967: warning: assignment makes pointer from integer without a cast


```

---

