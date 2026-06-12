---
title: "Bluetooth receiving on 10.10 RC"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by theopulus on 2010-10-08
I'm trying to receive files from a bluetooth device on Ubuntu 10.10 RC but it fails.

When I open the bluetooth preferences and click on "Receive Files" I get an error telling me that (translated from my language) "Personal Files Sharing" preferences cannot be opened, check that the app is installed.

What am I missing?

---

### Post by P4man on 2010-10-08
Have a look here:
[http://ubuntuforums.org/showpost.php?p=9543629&postcount=7](http://ubuntuforums.org/showpost.php?p=9543629&postcount=7)

---

### Post by theopulus on 2010-10-08
The problem is I'm not getting such options written on that post :(

It feels like there are some things missing on 10.10 RC regarding bluetooth

---

### Post by Melclic on 2010-10-14
This solved it for me. Go to Synaptic Package Manager, search and select to install for :

Apache2.2.bin
lib-apache2-mod-dnssd
gnome-user-share

I guess that there are some missing packages. 
You can then go and select from the preferences of the bluetooth icon "receive files"

(I also installed bluetooth manager)

Hope that helps

---

### Post by theopulus on 2010-10-15
Thanks a lot, I'll try

---

### Post by P4man on 2010-10-15
Dont see why you would need to install apache? But  gnome-user-share you should have I guess.

---

