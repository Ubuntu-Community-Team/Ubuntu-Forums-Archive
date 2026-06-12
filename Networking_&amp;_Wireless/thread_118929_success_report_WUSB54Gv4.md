---
title: "success report: WUSB54Gv4"
date: 2006-01-18
forum: Networking &amp; Wireless
---

### Post by isaidi on 2006-01-18
what should have been a simple procedure, was overwhelmed with insignificant documentation. 
the common misconsiptions about this card are:
yes, Linksys has aparently changed the chipset on the WUSB54Gv4. so you might hear reports of people getting WUSB54Gv1 andv2 working easily. and it should very easily work if you follow ndiswrapper wiki.

However as most users have experinced. ndiswrapper DOES not easily work with v4, 
ndiswrapper -l   shows 
```

root@ubuntu:/etc/network# ndiswrapper  -l
Installed ndis drivers:
rt2500usb       driver present, hardware present

```

but when you perform modprobe ndiswrapper .. the kernel gets stuck in an endless loop reseting the usb-device.. go figure!!!
```

tail -f /var/log/messages
[code] Jan 17 22:01:46 localhost kernel: [4627832.032000] usb 4-2: reset high speed USB device using ehci_hcd and address 3
Jan 17 22:01:47 localhost kernel: [4627832.290000] usb 4-2: reset high speed USB device using ehci_hcd and address 3
Jan 17 22:01:47 localhost kernel: [4627832.548000] usb 4-2: reset high speed USB device using ehci_hcd and address 3
Jan 17 22:01:47 localhost kernel: [4627832.806000] usb 4-2: reset high speed USB device using ehci_hcd and address 3
Jan 17 22:01:47 localhost kernel: [4627833.064000] usb 4-2: reset high speed USB device using ehci_hcd and address 3
Jan 17 22:01:48 localhost kernel: [4627833.322000] usb 4-2: reset high speed USB device using ehci_hcd and address 3
Jan 17 22:01:48 localhost kernel: [4627833.580000] usb 4-2: reset high speed USB device using ehci_hcd and address 3
Jan 17 22:01:48 localhost kernel: [4627833.838000] usb 4-2: reset high speed USB device using ehci_hcd and address 3
Jan 17 22:01:48 localhost kernel: [4627834.096000] usb 4-2: reset high speed USB device using ehci_hcd and address 3

```

and you are stuck here...  very close... but still the your system hasn't properly assigned wlan0, since the kernel keeps reseting the device.

you have three options. 

A.)  aparently, if you upgrade ndiswrapper to 1.7 this will work. but it is not available as a deb package, you will have to manually buid it.. and do the standard apt-get install kernel-headers... build-essentials..etc...

B.) Use native driver support for rt2570 cards.. which is baisically usb version of rt2500... i didn't follow this route so i don't know too much about it.. but there has been reported sucess using this route. again you will have to compile/build your own module for this driver

c.) on the ndiswrapper wiki list of supported hardware. I found the following

```

Card: Linksys #[WUSB54Gv4], 802.11b/g, USB 2.0 -- [link here|List#WUSB54Gv4]

    * Chipset: RT2500USB (RT2571F) (They just changed the chip and didn't tell anybody. Be careful which version (v1/v2/v4) you buy!)
    * usbid: 13b1:000d
    * Driver 00: Ralink Driver, Open Source: http://rt2x00.serialmonkey.com/ - 2005-07-25 / Good alternative to ralinktech.com's driver. Works WELL.
    * Driver 0: Ralink driver: http://www.ralinktech.com/supp-1.htm - 2005-03-25 / Drv2.0.1.0, rt2500usb.inf & rt2500usb.sys Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): works on both USB2.0 (load with modprobe ehci-hcd log2_irq_thresh=4 to avoid "usb X-Y: reset high speed USB device using ehci_hcd and address Z") and USB1.1 (UHCI (OHCI not tested (yet?))). WEP works with 64bit and 128bit keys. but bitrate is only 11Mbit/s Note: rename the configuration file for the adapter once you installed the drivers (getting them extracted is quite a mess (WINE/Cedega) you need rt2500usb.*). 'mv /etc/ndiswrapper/rt2500usb/148F\:2570.0.conf /etc/ndiswrapper/rt2500usb/13b1\:000d.0.conf' should do the trick.
    * Driver 1: Linksys Windows XP driver: http://www.linksys.com/download/default.asp Notes: ndiswrapper v1.1, kernel 2.6.11.7 vanilla: kernel-oops! ndiswrapper v1.2-rc1 loads fine (EHCI loaded with modprobe ehci-hcd log2_irq_thresh=4) but oopses when unloading the module and the adapter is still plugged in (Kernel 2.6.11.7 vanilla). Yet transmission seems to fail completely (except increasing 'Tx Invalid misc' values nothing happens).
    * Driver 2: older Linksys Windows XP driver: ftp://ftp.linksys.com/pub/network/WUSB54Gv4_20040703.exe Notes: ndiswrapper v1.2-rc1, kernel 2.6.11.7 (also works with grsec2 patch v2.1.5): seems to work, but only 11Mbit/s and without any encryption. no need to unplug the device before removing the ndiswrapper module. works on USB2.0, USB1.1 not tested (yet).
    * Driver 3:There is a native driver for rt2x00 but it has no USB support yet. View its status at rt2x00.se

```

the key part is 
```

load with modprobe ehci-hcd log2_irq_thresh=4 to avoid "usb X-Y: reset high speed USB device using ehci_hcd and address Z"
[code]

so before injecting ndiswrapper... remove ehci_hcd and modprobe with the command mentioned above
[code]
  modprobe ehci_hcd log2_irq_thresh=4

```

that's it... this worked for me. everything else beyond that was easy...
just had to add this to /etc/network/interfaces
```

iface wlan0 inet dhcp
        wireless-mode managed
        wireless-essid any

```


hope this helps some one.. this is a quick and crude success report.. i can post details and proper links if anyone shows interest.. i am just posting this to give an overview to get this card working.

---

### Post by The Belgain on 2006-02-27
Wow!  Thanks for this.  I've hit this exact problem on my Belkin wireless USB card (model number 7050 - also based on the same Ralink chipset).

I did a quick Google, and found this post and the ndiswrapper entry exactly at the same time.  I've followed your instructions, and the card works fine now!  Thanks for taking the trouble to write this up to help other people out.

This should go somewhere in the wiki too...

---

### Post by The Belgain on 2006-02-27
My next question however is... how do I make the ehci_hcd module load with those parameters at startup?

As things are the PC will just hang when modprobe'ing ndiswrapper at startup, because it isn't inserting the ehci_hcd module with this extra parameter.

---

### Post by willywear on 2006-02-27
Fantastic! \\:D/ 

I was stuck with the Belkin 7050 also.

Many thanks for the posting.

---

