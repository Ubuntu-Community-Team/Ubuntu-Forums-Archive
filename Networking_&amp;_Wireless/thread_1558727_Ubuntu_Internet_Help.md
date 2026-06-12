---
title: "Ubuntu Internet Help"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by MrMicrowave on 2010-08-22
Hi, I am not very techie when it comes to Ubuntu, so I could use some help.

I have a Belkin USB device that is plugged into my computer, and on Win XP it works fine.

On Ubuntu (I have 10.04) it doesn't recognize it and no wireless Internet signal's come up.

Could I please get some help on this? Thanks.

---

### Post by Raymond2201 on 2010-08-22
Assuming your trying to get a USB mobile Broadband device working.
try installing usb-modeswitch..

```
sudo apt-get install usb-modeswitch
```

This should allow your USB device to be used as a wireless card in Ubuntu.

You should then be able to make a Mobile Broadband connection through gnome connection manager.


hope this helps..

---

### Post by PaulReaver on 2010-08-22
you'll need to install the drivers, to help i'd need to know exactly what belkin wifi stick you have. 

plug in the belkin and in a terminal type 
lsusb

---

### Post by PaulReaver on 2010-08-22
> **Raymond2201 said:**
> Assuming your trying to get a USB mobile Broadband device working.
try installing usb-modeswitch..

```
sudo apt-get install usb-modeswitch
```

This should allow your USB device to be used as a wireless card in Ubuntu.

You should then be able to make a Mobile Broadband connection through gnome connection manager.


hope this helps..



raymond, dude your lettin the side down, are you sure your scottish?
belkin don't make 3g modems.  this is a usb wifi adaptor.  


MrMicrowave If you tell us the exactly which usb adaptor you have we could be more helpful.

"lsusb" without quotes in a terminal and post the output.

---

### Post by MrMicrowave on 2010-08-22
Ok, Only thing I see that comes up with Belkin is this

Bus 001 Device 003 ID 050d : 825b Belkin Components

---

### Post by MrMicrowave on 2010-08-22
actually i might have found a fix,

[http://ubuntuforums.org/showthread.php?t=1387483](http://ubuntuforums.org/showthread.php?t=1387483)

---

### Post by MrMicrowave on 2010-09-09
Could someone give me a simplified version of [http://ubuntuforums.org/showthread.php?t=1387483](http://ubuntuforums.org/showthread.php?t=1387483) ?

---

