---
title: "Modem not showing in new mobile broadband connection - ZTE MF636 HSDPA"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by flutes on 2010-01-04
Hi,
Complete noob here.

I've been trying to get a USB modem stick to work with Karmic.

The modem is the ZTE MF626 HSDPA on a Telstra Next G plan.

I've followed all the guides and links on the forums:

[LIST]
[*]Have deactivated the CD autorun on the USB stick in XP
[*]lsusb is showing "Bus 002 Device 003: ID 19d2:0031 ONDA Communication S.p.A."
[*]demsg is showing "usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1"  This seems stable as well, ie checking periodically it doesn't seem to be disconnecting
[*]By the way, the blue light indicating network communication/modem active lights up after the device has been plugged in for a second or so.
[/LIST]

When I go through Network Connections and add a new mobile broadband connection, there is nothing listed in the "Create a connection for this mobile broadband device" drop-down on the first configuration screen - all the guides I've read say that it should be listed here, but none say any debug steps if it doesn't.

Some other guides for older versions of Ubuntu and earlier versions of the modem reference a "/usr/share/hal/fdi/information/20thirdparty/20-zte-mf626.fdi"file which I don't have.

Can anyone offer any advice here?

Thanks,
Matt.

---

### Post by alexfish on 2010-01-04
Hi

Can I ask which version of Ubuntu you are using

  There are Threads About This Device So Maybe able to point You In the Right Direction

---

### Post by flutes on 2010-01-04
Sorry - should have added that info.  I'm using Ubuntu 9.10.

I've followed the other threads as best I can - I haven't gone down the path of trying other dialer software aside from Network Connections.

Any help would be much appreciated!

Thanks,
Matt.

---

### Post by pdc on 2010-01-05
I got an MF636 working using wvdial

[http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=54271](http://www.geekzone.co.nz/forums.asp?forumid=46&topicid=54271)

(currently using the MF636 to send this)

in the wvdial.conf script; that lives in the /etc directory would need the APN changed to that of telstra; I could not run this modem on network manager

---

### Post by flutes on 2010-01-05
Thanks pdc - I'll give that a whirl.  I had seen reference to a similar work around but it was implied that those work arounds weren't necessary in 9.10; guess they mustn't be for other modems...

---

