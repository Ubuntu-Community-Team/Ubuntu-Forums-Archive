---
title: "iphone tether crapped out"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by silent122bob on 2010-03-12
i've been using my iphone usb tether for my main browsing for long bus rides, but after a while of wifi-ing, i got around to installing updates and now my tether won't recognize on ubuntu. how would i go about troubleshooting this?

9.10

---

### Post by FuManShu on 2010-03-12
What method of USB tethering were you using?  iProxy, ipheth (using the built in USB Tether with an ethernet driver) or PDAnet?

---

### Post by silent122bob on 2010-03-15
i was using ipheth.

---

### Post by FuManShu on 2010-03-16
Most likely it was libusbmuxd, usbmuxd, or libiphone that was updated.  Try getting the most recent version of ipheth which drops libiphone and instead uses the libimobiledevice API.  libimobiledevice is the next stage in iPhone and iPod Touch compatibility.

Another thought is that perhaps there was a kernel update that broke the ethernet driver.  I haven't tested ipheth on the newest kernel.  I'm still using 2.6.31-16.

---

### Post by silent122bob on 2010-03-17
the update released sometime this morning remedied my dilema. i'll be more wary of blindly updating after this. thanks =]

---

### Post by Shutter4U on 2010-04-04
Try this solution I posted it in the PDANet thread as well - 

You guys know you can use internet tethering via the USB cable, right?

I got it to work on my (non-jailbroken) iPhone 3g by doing this:

1) go into System->Preferences->Network Connections in Ubuntu
2) in the "Wired" tab, click "Add"
3) Give the new connection a friendly name
4) enter the MAC address of your iPhone in the field that asks for it

- you can get this address from your iPhone:
- goto Settings->General->About and and scroll down to "Wi-Fi Address"
- the "Wi-Fi Address" is the MAC address

5) click checkboxes for "connect automatically" and "available to all users"
6) click "Apply" then "Close"
7) connect your iPhone and it should automatically connect. make sure "internet tethering" is enabled on your iPhone first, of course ;)

---

