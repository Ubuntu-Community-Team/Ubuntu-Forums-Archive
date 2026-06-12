---
title: "Broadcom driver install woes (bcm4400)"
date: 2006-03-13
forum: Networking &amp; Wireless
---

### Post by dbunder on 2006-03-13
Very new to Ubuntu.  Just installed it today.  First, I must say I'm mightily impressed.  Haven't been a linux fan since desktop linux became the focus of all the distributions (started with slackware 2, gimme my command line, dammit!), but Ubuntu install was painless, and the default desktop is very easy to use and like I said, I'm utterly impressed.

Now, the matter at hand.  Trying to install broadcom drivers for wireless (WPA2 encryption) from source RPM using the instructions provided by broadcom.  I've had to install numerous packages (make, gcc 3.4, linux kernel source, rpm itself, a few others), and I'm nearing the end of installing it.  I'm at the build phase (rpmbuild -bb ...) and it's exiting with:

WARNING: Symbol version dump /usr/src/linux/Module.symvers is missing; modules will have no dependencies and modversions.

I'm assuming this means I need to do a make config on the kernel and go through that whole process.  I'm fine with that.  Been doing it for years.  My question is: is there anything I should enable that will help me along with the wireless/WPA2 configuration that I should enable and/or modularize in the kernel config?  That's really it.  It's been a long time since I've used linux and the kernel has changed so much that I don't know what's going on with all these new options.

Doing this on a Dell Inspiron 8600 laptop if that makes any difference.  Any nice options in the kernel config that are nice for laptops (ie sleep/hibernate features, power management, battery meters, etc)?

Thanks for any help at all, and I hope ubuntu and I have a healthy life together. :)  Getting wireless working is just step #1.

---

