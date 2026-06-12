---
title: "Auto Eth0 won't go away!"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by wizardStan on 2009-06-09
Hi,
I've created a new connection, named simply "Wired Connection 1" with a static IP.  There already existed Auto Eth0, which gets a dynamic IP.
I want to use my static IP, I do not want a dynamic one, so I deleted Auto Eth0.
It came back.
So under the options for Auto Eth0, I unchecked "Connect Automatically"
Now I have two Auto Eth0.  No matter what I do, Auto Eth0 comes back as the default connection.
How can I keep this from happening?

---

### Post by Iowan on 2009-06-09
My suggestion would have been to uncheck  "Connect Automatically"... but you already did. I presume you also tried editing "Auto eth0" to use a static address.

---

### Post by wizardStan on 2009-06-09
yes and yes.  If I delete Auto Eth0, it comes back.  If I edit it in any way, a new one with the same name appears as the default with the default values.  I can't figure out when it comes back.  I can go for a few days, and then suddenly notice that my IP has changed.

---

### Post by superprash2003 on 2009-06-10
just configure auto eth0 to static ip.. dont delete that..

---

### Post by wizardStan on 2009-06-10
As I said, I did configure it to a static IP.  A second Auto Eth0 appeared.  I deleted both of them now.  I'll try to figure out what triggers it coming back, but it's seemingly random, or I might go for some time before trying to do something that requires a static IP that I miss when it actually happens.

---

### Post by thieaux on 2009-06-11
/etc/network/interfaces edit it and set your address accordingly see if it helps

---

### Post by superprash2003 on 2009-06-11
editing the interfaces file as mentioned above will work as well.. heres a guide [https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html)

---

### Post by wizardStan on 2009-06-17
I followed the network-configuration suggestion, adding lines to make a static connection.  It worked in that the Auto Eth0 did not come back this time.  On the other hand, the network icon indicated to me that the device was no longer managed at all.  It also didn't start automatically, I had to manually run ifup to start it.
I have discovered that it (Auto Eth0) always comes back as default connection at boot up.  I delete it, restart, it comes back.  I change it to static, restart, it changes back, or creates a duplicate of itself.  I still haven't figured out how the duplicate got there the first time since I haven't been able to reproduce it.
I just want whatever keeps creating this Auto Eth0 connection to stop doing that.  What keeps adding it?

---

### Post by wizardStan on 2009-06-27
Sorry to bring this up again, but are there any further suggestions?  It's really annoying to have to remember to remove the unwanted connection every time I restart.

---

### Post by wizardStan on 2009-07-11
bumping because it's still doing it, and I'm having trouble believing that I'm the only one who has noticed.

---

### Post by wizardStan on 2009-08-13
This is still a source of great frustration.  If I delete Auto-Eth0, it is simply recreated when I restart my system.  If I edit it in anyway, a new, duplicate Auto-Eth0 is created at boot, forcing me to delete both of them.  This is undesired behavior.  How do I make it stop?

---

### Post by Iowan on 2009-08-14
Unfortunately, I can provide only vague recollections of a process that generates the "auto eth0" option. I'll try to search for the thread shortly.

---

