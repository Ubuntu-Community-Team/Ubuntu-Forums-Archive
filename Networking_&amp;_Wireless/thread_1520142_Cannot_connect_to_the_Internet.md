---
title: "Cannot connect to the Internet"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by DzmitryG on 2010-06-29
Both ethernet and wireless connections are down, Windows on the same machiene works with both - not hardware problem. Networking is enabled in the applet, but WiFi indicator and ethernet adapter indicator do not flash. Problem appeared after I closed the lid of the laptop at night (set to suspend), but next morning battery was empty indicating that it failed to suspend. I could not find any "hardware manager" inbuilt to turn devices on.

Any help will be very much appreciated as I don't like using Windows, and internet is a necessity.

PS It's Ubuntu 10.4, Gnome on Dell Inspiron 6400 (x86)

---

### Post by dineshs on 2010-06-29
I dont know whether this is related
[http://ubuntuforums.org/showthread.php?t=1505217](http://ubuntuforums.org/showthread.php?t=1505217)
post#3

---

### Post by DzmitryG on 2010-06-29
Did not help. I think the devices cannot wake up for some reasons. I am going to install device manager and see if that helps.

---

### Post by DzmitryG on 2010-06-29
Device Manager for Gnome just displays some information. I ran test on Networking and attached is the report (won't open in browser, but OO Calc will open it), if any help.

---

### Post by DzmitryG on 2010-07-02
Actually, ethernet adapter was flashing.
The problem was in a blacklisted for unknown reason module wl, just had to remove it from /etc/modprobe.d/blacklist-local.conf
I have no idea how I got the name of the module, I did so many things that cannot recall, and bash history did not help.

---

