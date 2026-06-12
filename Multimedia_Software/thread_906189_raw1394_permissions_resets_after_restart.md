---
title: "raw1394 permissions resets after restart"
date: 2008-08-31
forum: Multimedia Software
---

### Post by Dreamerman on 2008-08-31
Hi. I use kino for dv capture & managed to bypass the raw1394 problem by changing its permissions from root to master (ie me) via sudo nautilus. That is fine but every time I restart Ubuntu, raw1394 permissions reverted back to root.

Is there any way to change permissions permanently ?

Thanks

---

### Post by Dreamerman on 2008-09-03
anyone ?

---

### Post by Erlander on 2008-09-03
Have a look at:

[https://help.ubuntu.com/community/Firewire]("https://help.ubuntu.com/community/Firewire")

Particularly Method 5 which is nearly at the bottom of the page.

Rob

---

### Post by remeeraz on 2008-10-13
> **dreamerman said:**
> hi. I use kino for dv capture & managed to bypass the raw1394 problem by changing its permissions from root to master (ie me) via sudo nautilus. That is fine but every time i restart ubuntu, raw1394 permissions reverted back to root.

Is there any way to change permissions permanently ?

Thanks

> **sudo chown** username **/dev/raw1394**

:)

---

### Post by muranyia on 2009-07-08
Funny indeed, dev/raw1394 seems to be recreated upon each restart, with default owner:group (root:disk) and default permissions (660).

What you can still do:

1. Create a group called 'firewire', and make yourself a member of it.
AND
2. Change udev rule for raw1394 to allow members of the 'firewire' group to access it:

> **sudo gedit /etc/udev/rules.d/**40-permissions.rules
(This works on my Ubuntu Hardy - could be another file on your system)

> # IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="firewire"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

As the comment in the file already shows, the group for raw1394 shall not be 'video', and you shall not either make yourself member of the 'disk' group, as both ways are dangerous for your system.

---

