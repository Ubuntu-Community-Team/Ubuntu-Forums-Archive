---
title: "Weird Bluetooth Issue"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by jitaroo on 2011-04-28
I have a usb bluetooth adapter I just bought and when I plug it into my desktop gnome's bluetooth manager gives me a huge turn on button that when I push just sits there for a while and then turns back off. The bluetooth icon in the panel doesn't give me any options other than turn on/off. I tried installing the other bluetooth manager and got the same error. The weird part is that when I plug in the device to my laptop that also doesn't have bluetooth and also runs ubuntu it works just fine there. I have no idea whats wrong on my desktop, but I need it there!

---

### Post by jitaroo on 2011-04-30
anyone?

---

### Post by Beazel on 2011-04-30
I've got the same issue with an inbuilt Bluetooth adaptor.  I'll post here if I find anything useful for you.

---

### Post by Beazel on 2011-04-30
Looks like we're experiencing [this]("https://bugs.launchpad.net/system76/+bug/762964") bug.  Until a fix comes along you could try:
```
sudo service bluetooth restart
```
OR:
```
sudo /etc/init.d/bluetooth restart
```
in a terminal and that should get things working again.  Needs to be done after each reboot though.

Best of luck!

---

