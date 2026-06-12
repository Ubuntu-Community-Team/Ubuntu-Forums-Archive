---
title: "PEAP/MSCHAPv2 wifi connection problems"
date: 2012-06-06
forum: Networking &amp; Wireless
---

### Post by aciddesir on 2012-06-06
I've been searching the net for weeks and still can't find an answer or work around for this:

When trying to connect to my university's wifi, or eduroam, I can connect for a few minutes, usually a max of five, then the connection shuts down and I'm booted off the network and cannot reconnect. When it was connected, I tried pinging a few websites, and it is connected, but then abruptly stops.

As usually, the uni's IT department is useless with linux.  I use a Broadcom 43xx card, with the STA driver.  I've tried it without the driver as well and same problem, running 12.04.  The same problem arises when I switch and use the gnome-shell as well.

I've tried a lot of things, I'm more than willing to retry or change any configuration, really, anything. I hate to say it, but this is a make or break thing for me on Ubuntu, and any other university student as well, I suspect.  Does anyone know where the issue lies and/or how to fix it?

EDIT: A set-up a wifi tether through my Galaxy S2 and the same situation occurs, with the exception that the connection lasts longer, approximately 20 mins each.

---

### Post by paulromano on 2012-07-02
Are you using 802.11n? I'm having similar problems and after searching around for a while, it seems that it could be a problem with 802.11n. I would recommend trying to disable 802.11n on your wireless card, typically done using a kernel module configuration file in /etc/modprobe.d.

---

