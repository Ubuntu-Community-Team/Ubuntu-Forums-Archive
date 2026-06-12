---
title: "SOLUTION for burning audio CDs from guest OS!  iTunes fix!!!"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Jim March on 2008-05-03
Y'all will love this.

In Virtualbox 1.5.6 and 1.6.0 that I know of so far, you can attach the CD drive to the guest in the VM settings screen, and you can enable the "passthrough" checkbox, but it then warns you that audio CD burning won't work.  So far as I'm aware, all other virtual machine managers share this weakness.

This screws iTunes users or anybody else switching to Linux who already owns DRM music libraries.  iTunes can be made to work in Wine as well, but it can't burn CDs there either.

So no CD burning.

EXCEPT!

For less than $20, get an adapter that lets you hook up your ATAPI or SATA CD/DVD drive via USB.  You can even leave it mounted in a desktop chassis, just run the USB cable from the adapter out the back and into a USB port.

Then in Virtualbox, go to the USB section, enable USB passthrough of the CD or DVD drive, Windows will load it's own driver for that and bingo - you CAN burn audio CDs.

Example adapters:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812189169](http://www.newegg.com/Product/Product.aspx?Item=N82E16812189169)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812156101](http://www.newegg.com/Product/Product.aspx?Item=N82E16812156101)

[http://www.newegg.com/Product/Product.aspx?Item=N82E16812226001](http://www.newegg.com/Product/Product.aspx?Item=N82E16812226001)

...or any number of similar cheap critters.  If you're dealing with a desktop, some of these come with a drive power adapter brick but you can toss that (or use it for something else) and continue running the drive off the chassis power.

FOR LAPTOPS: you'll need a complete external USB CD-burner setup to get to the same place.  Either build your own using a generic drive bay with USB port and a basic drive, or buy a complete critter such as:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827106248](http://www.newegg.com/Product/Product.aspx?Item=N82E16827106248)

THIS SOLUTION WAS TESTED WITH:

* Virtualbox 1.5.6 "full tilt edition"

* Ubuntu Hardy host OS with the "USB tweaks" applied - see also:
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

* Windows XP SP2 guest OS (strongly suggest this or (barf) Vista rather than Win2k or lower).

* iTunes 7.6.2 for Windows

* Sony DVDirect VRD-VC10 external USB DVD drive:
[http://www.pcmag.com/article2/0,1759,1750223,00.asp](http://www.pcmag.com/article2/0,1759,1750223,00.asp)

NOTE: this drive is an expensive unit that can connect straight to an analog camcorder or similar, recording DVD without a computer.  However, it has a standard USB port and when I connected it to the PC I loaded no drivers (in either host or guest OS).  When I connected it to the PC, the small screen on the drive said something about "direct connect mode".  All this leads me to believe that any standard USB-connected CD or DVD drive (including far cheaper hardware!) will work with this same stunt.

This isn't tested yet in the new Virtualbox 1.6 but I'd be shocked if it failed.

Jim

---

