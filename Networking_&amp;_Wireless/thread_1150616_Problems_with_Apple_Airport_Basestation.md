---
title: "Problems with Apple Airport Basestation"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by Tomist on 2009-05-06
Hello everyone!

I have been switching from Linux to Linux trying to find the right one. But in every one of Linux distros I used (besides Mandriva, idk why) my internet would "time out". My applications wouldn't be able to do anything on the internet, but Linux would still say that I was connected. I would have to reconnect to get back online. And now that I am back w/ Ubuntu, I thought I would ask the community.

I know it isn't because my wireless card is corrupt or something because I can connect to and stay connected to my friends router. I think it has something to do with my Apple Airport Extreme Basestation. I am using an Acer Aspire 5735Z, not an Apple laptop/desktop.

Any ideas? :confused:

---

### Post by Tomist on 2009-05-06
Any help at all would be great!

---

### Post by hajk on 2009-05-07
You should, first of all, make sure that the AEBS is not the problem, and the only way of doing that is to fire up Mac OS X and open the Airport Utility to do a manual check of the AEBS. Could it be that you're trying to establish a static IP with an out-of-range address? Do you have MAC filtering switched on? And so on... play with the settings, if you have to.

Then, if you're absolutely sure that the problem is not the AEBS, you could start tracing possible problems on the Linux side. You could start, e.g., by tossing network-manager out and switching to Wicd instead. 

Go to it, you have work to do!:)

---

### Post by danipoak on 2009-05-07
I have an airport express base station and this is how I got it to work:  It needs to be AES rather than TKIP.  I figured out that by default WPA encryption is is TKIP whereas WPA2 is AES so I simply changed it to WPA2.

---

