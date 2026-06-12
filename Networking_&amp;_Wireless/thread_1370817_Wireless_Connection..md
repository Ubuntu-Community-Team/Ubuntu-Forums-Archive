---
title: "Wireless Connection."
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by ruri03 on 2010-01-02
I am wanting to install ubuntu i installed it on a VB to test it out, How hard is wireless to connect up? I have a Intel Wifi 5100 On a laptop. Could any one please try and guide me how to set it up, so i can try it out on the VB before  installing the live cd onto my laptop thank you very much.

---

### Post by hhh on 2010-01-02
When you run the Live CD (if you can boot from CD, or USB via UNetbootin), you can test your wireless and other hardware without installing. There is a panel at the top of a default Ubuntu setup, and an applet at the right end of the bar called "NetworkManager", it's next to the Volume icon and it looks like the AT&T "how many bars" logo. Click on that. If you wireless adapter is recognized, a list of available wireless networks will display. Click a network, enter a security key (unless it's an open network your using, usually labeled "linksys") and you're good to get started.

Both Jaunty and Karmic have recognized my Belkin wireless USB adapter. I've had to do some configuring after that (just adding a startup script to set a stable connection rate, very easy to do as it turns out) but there's no harm in trying except for the time spent and the price of a blank CD.

For info on the kludge I needed to add, see this thread...
[http://ubuntuforums.org/showthread.php?t=1370481](http://ubuntuforums.org/showthread.php?t=1370481)

-edit- BTW, you don't need to run the Live CD through VB, it doesn't install anything to your computer. Just boot from the CD, which most computers do automatically now if a bootable CD is in the drive during startup.

Post if you don't understand anything, of course.

---

