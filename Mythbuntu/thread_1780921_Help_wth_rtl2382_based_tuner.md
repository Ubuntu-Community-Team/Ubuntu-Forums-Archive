---
title: "Help wth rtl2382 based tuner"
date: 2011-06-12
forum: Mythbuntu
---

### Post by jensk on 2011-06-12
I have got my hand on a couple of tuners based on rtl2382 a chipset. it's a AGK 10508 [http://www.agknordic.com/index.php?side_id=496]("http://www.agknordic.com/index.php?side_id=496")
I would like to have this tuner to work under Mythbuntu 11.04 but don't know how to.

I have updated usbids and the dongle is detected correct when i do an lsusb.

I have stumpled on this page [https://gitorious.org/rtl2832]("https://gitorious.org/rtl2832")where there is drivers for the RTL2832 chipset.

I have edited the rtl2832u.h file so that the DEXATEK driver corresponds with the usbid (8202) of my dongle.

My problem is that when i try to do a make it fails at the start. I can se that I need have some parts of the v4l drivers along with the rtl2832 driver package but I don't know what to include and where to the tree the rtl2832 driver i to be put in.

How do i get this make and make install to work with the driver?

---

