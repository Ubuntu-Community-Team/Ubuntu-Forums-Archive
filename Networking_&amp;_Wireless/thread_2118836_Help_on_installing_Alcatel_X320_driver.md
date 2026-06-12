---
title: "Help on installing Alcatel X320 driver"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by nishlomi on 2013-02-22
I have Ubunto 12.10, and Mobile Broadband Alcatel X320, there a link to the product site:
[http://www.alcatelonetouch.com/global-en/products/mobile_broadband/one_touch_x230.html#.USdtnVEvk8o](http://www.alcatelonetouch.com/global-en/products/mobile_broadband/one_touch_x230.html#.USdtnVEvk8o)
and I don't have any Idea how to make it work
I tried to install  USB_ModeSwitch without success..
Can you give me a guide or help how to install this modem?

thanks. and sory about my bad english..

---

### Post by sanderj on 2013-02-22
General method for unrecognized USB devices:

unplug the device, type 'lsusb' in terminal
plug in the device, and type 'lsusb' again. Now note the difference; that's your USB device. Post that line with the USB ID here.

Search the USB ID on Google (preferrably in combination with 'Ubuntu'). Check the first few Google hits. Does that help?


Then, open a terminal
Unplug the USB-device. Type 'dmesg', and make a note of the last line.
Then plug in the device, type 'dmesg' again, and copy everything after the noted line into this thread.

---

