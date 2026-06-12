---
title: "Network Connections in Panel Disappears"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by Justin C. on 2009-12-06
When I press the network connection button in the panel, the menu with the network choices opens as normal. However, when I select the wireless network I wish to connect to (in this case an ad hoc), the network connection button disappears entirely. It reappears after rebooting, but the same problems happen. I've been doing a lot of googling and I can't figure out the problem. Any help would be greatly appreciated.

Thanks,

-Justin C.

---

### Post by Justin C. on 2009-12-07
And if this helps any, if I take the laptop to a wireless connection that I already have saved, it connects automatically, internet and all. It's just new connections that do not work.

---

### Post by NoBugs! on 2009-12-07
Sounds like your networkmanager applet is crashing, can you get a [crash report]("https://wiki.ubuntu.com/Apport") of it?

---

### Post by Justin C. on 2009-12-07
Thanks NoBugs. Do I have to install a package to use Apport? Nothing pops up regarding a crash.

---

### Post by Justin C. on 2009-12-07
Nevermind, I read down farther and see the line of code to enable it. I will do so and get the crash report. Thanks again.

---

### Post by NoBugs! on 2009-12-10
When the networkmanager disappears you should be able to get it back by pressing alt+F2 and running "nm-applet".

---

### Post by wijit on 2010-05-28
NoBugs,
No, it didn't work.

---

### Post by NoBugs! on 2010-06-15
Do you see an error when you try "nm-applet" in the terminal?

---

