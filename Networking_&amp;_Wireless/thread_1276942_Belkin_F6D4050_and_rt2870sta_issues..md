---
title: "Belkin F6D4050 and rt2870sta issues."
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by absinthe on 2009-09-27
I'm pulling my hair out trying to load rt2870sta and recognize my Belkin USB wireless G stick. It uses the rt2870sta module.
What it boils down to is "rt2870sta" will not recognize my USB Wireless adapter. It's plugged in, and lit up. But under ifconfig -a the device is not listed. It does show up under lsusb as a belkin component.

I finally got it recognized by compiling the driver with the line "{USB_DEVICE(0x050d,0x935a)}, /* Belkin F6D4050 */" in the /os/linux/usb_main_dev.c of the package before compiling.

Now the module recognizes my device but when I go to DHCPCD it stops at "waiting for carrier" and then times out. I am connecting to the correct SSID and everything. I should note that the drivers that come with the stick work through ndiswrapper but they crap out after awhile so I'm trying to use the native ones from the ralink website.

Any ideas? 

Thank you.

---

### Post by SeaJayEmm on 2010-02-14
First off the rt2870sta is the wrong driver. You need the rt2870.inf.

---

