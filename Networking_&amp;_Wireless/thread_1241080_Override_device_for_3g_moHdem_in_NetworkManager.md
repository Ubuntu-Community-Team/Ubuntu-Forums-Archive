---
title: "Override device for 3g moHdem in NetworkManager?"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by leibnitz27 on 2009-08-15
Hi all -

I've got a vaio tt11wn with an integrated option 3G modem - NetworkManager sets this up "fine", but always fails to connect.  Looking at syslog, I can see it's using /dev/ttyHS2, (there are several devices created for the modem - HS0->9).  

The device I need to be using is /dev/ttyHS8 - I've checked with wvdial, and everything works fine if I use this.

NetworkManager's config doesn't *seem *to have anywhere I can override the device choice, tho I might be missing something really obvious!

Anyone know how to override this?

Thanks!

Lee.

(Vaio, tt11wn, Vanilla Jaunty other than adding HSO 1.12, and a modified sony_laptop module)

---

### Post by GeorgeVita on 2009-08-15
Hi **leibnitz27**,
I am not sure if I can help as from 9.04 many things are changed with modem recognition/'drive'. I 'll give you just an idea:

0. Find the vendorID ; productID of your modem ```
lsusb
```

1. Open file with HAL info for modems ```
sudo gedit /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```

2. Search (CTRL-F) for usb.vendor_ID (ex. 0af0) scroll some lines below to see your exact model's usb.product_ID (ex. 7211)

3. Change the contents of next (?) line from 2 (?) to 3,4,5... SAVE, EXIT ```
... usb.interface.number" int="2">
```

4. It is better to reboot and test

Regards,
George

---

