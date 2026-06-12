---
title: "NEWBIE: ndisgtk package says ndiswrapper not found"
date: 2013-01-21
forum: Networking &amp; Wireless
---

### Post by Justplainwyrd on 2013-01-21
and asks "is the ndiswrapper module installed?"...but it is.

I'm trying to get my wireless working, and 

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper)

lead me to 

sudo lshw -C network

which said UNCLAIMED

so I installed  [the **ndisgtk** package]("apt:ndisgtk").

found the drivers on the realtek site, used the ndisgtk, found the inf, and was given:

Module could not be loaded. ERROR WAS:
FATAL: Module ndiswrapper not found.
is the ndiswrapper module installed?
OK

When I go to Ubuntu Software Center, ndiswrapper is installed with both add ons

Help?

---

