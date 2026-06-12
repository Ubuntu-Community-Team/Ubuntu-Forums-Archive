---
title: "How to prevent network int renumbering?"
date: 2009-07-05
forum: Networking &amp; Wireless
---

### Post by gurt on 2009-07-05
I have a bunch of eth NICs in jaunty 64-bit desktop. 
I noticed that when I get an updated kernel (via Update Manager) my ethernet interfaces are renumbered. I changed the numbering in /etc/udev/rules.d/70-persistent-net.rules. And that is working. But is there a way to prevent the interface renumbering (other than not accepting updates)? I would like to avoid having to remember to edit 70-persistent-net.rules every time I update.

It seems the persistent rules aren't all that persistent. :rolleyes:

Incidently, if the interfaces do get renumbered, and I reboot or shutdown, all my ethernets fail, I get a screen full of grub message "nm-system-settings: SCPlugin-Ifdown: devices removed" and I can't start my desktop. I have to boot from the LiveCD, edit 70-persistent-net.rules to reflect my configuration and alls well. That's quite an ugly crash situation.

Ta!

---

