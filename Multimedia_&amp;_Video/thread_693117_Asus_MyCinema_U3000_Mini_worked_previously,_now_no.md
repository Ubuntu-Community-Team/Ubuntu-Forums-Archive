---
title: "Asus MyCinema U3000 Mini worked previously, now not loading."
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by neocookie on 2008-02-10
I'm having problems with my Asus My Cinema U3000 Mini DVB dongle.

A couple of weeks ago I found a tutorial online which had details of installing the linux sw/fw for the card, and after following it was able to view dvb through kaffeine. Now, it won't load when I plug it in.

tail -f /var/log/messages returns the following when its plugged in:
Feb 10 22:55:08 iyoti kernel: [   90.032000] usb 3-2: new high speed USB device using ehci_hcd and address 2
Feb 10 22:55:09 iyoti kernel: [   90.164000] usb 3-2: configuration #1 chosen from 1 choice

and if I load the firmware: sudo modprobe dvb-usb-dib0700
Feb 10 22:55:52 iyoti kernel: [  133.808000] dib0700: loaded with support for 2 different device-types
Feb 10 22:55:52 iyoti kernel: [  133.808000] usbcore: registered new interface driver dvb_usb_dib0700

And that's it. No messages about something being found in a "cold state" or anything like that. 

Any ideas how I can get this dongle to start up properly?

---

### Post by steefjeqv on 2008-02-11
Hi,

Did you do a kernel update the last few weeks ?

If so, you can try installing the newest v4l-dvb drivers.

[http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://www.linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")

Greetings,
Steven

---

