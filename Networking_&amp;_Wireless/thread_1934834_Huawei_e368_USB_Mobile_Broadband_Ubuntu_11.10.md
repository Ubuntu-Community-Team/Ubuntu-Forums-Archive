---
title: "Huawei e368 USB Mobile Broadband Ubuntu 11.10"
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by Dubious9 on 2012-03-02
Hello,

I want to report to the Ubuntu Community that I succeeded in getting the Huawei e368 to work in Ubuntu 11.10. I will discuss how I got it working in this post.

When I plugged in the Huawei E368 into a usb port I went to the Ubuntu 11.10 Gnome Network Manager and checked enable mobile broadband. Next I went to create new mobile broadband connection and this was a wizard that stepped me through the process.

I selected United States for the location/country, AT&T for the carrier, and Laptop Connect (Data Card) for the billing plan name.

Then I selected the connection and connect and it worked.

My discovery of this solution took me several hours. The reason I was able to solve this problem had much to do with the fact Ubuntu 11.10 and Gnome Network Manager happened to support the Huawei E368. 

I want to share the fact that I made several changes that you may need to know about if following the above procedure does not go as smoothly.

install usb-modeswitch and usbutils.

use lsusb and notice if huawei technologies comes up as one of the devices. Get the manufacturer and product id - they should be 12d1 (colon) 1506.

type

sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules

if you search for huawei you&#539;ll get several hits and just find anyone of the huawei entries and change
the manufacturer id to 12d1 and the product id to 1506 and save the changes.

I restarted and I also used a command

usb_modeswitch -v 12d1 -p 1506 -s 5

the output said several things including that I did not specify a mode change and further that it was testing
to see if my device had vanished and that it did and that meant that the mode change was a success....

Those were things I did before discovering the right answers to the Network Manager new mobile broaband wizard...

When I found out what answers to give the mobile broadband connection wizard I was able to connect. The other things I did with usb modeswitch may also have effected the outcome...just so you know!

Later,

Dubious9

refrences - 

[https://wiki.archlinux.org/index.php/USB_3G_Modem](https://wiki.archlinux.org/index.php/USB_3G_Modem)
[http://manpages.ubuntu.com/manpages/karmic/man1/usb_modeswitch.1.html](http://manpages.ubuntu.com/manpages/karmic/man1/usb_modeswitch.1.html)

---

