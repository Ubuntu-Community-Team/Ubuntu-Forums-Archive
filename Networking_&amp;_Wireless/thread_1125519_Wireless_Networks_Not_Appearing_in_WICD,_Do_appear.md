---
title: "Wireless Networks Not Appearing in WICD, Do appear from Terminal"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by hurricanesfan66 on 2009-04-14
I am running a Dell e1705 with the infamous Broadcom 4328 that I have to reinstall ndiswrapper with on each upgrade.  After a day, I finally get it up and running, but this time I have lost more wireless networks.

I had the computer completely turned off, and when turning it on, WICD was not seeing any wireless networks, mine or any of the 10ish in the neighborhood.  On another desktop, the router is recognized, and this laptop will connect fine with a hardwire into the router.

Using 

> sudo iwlist scan

Returns me a list of the networks around.  My Wifi light is on.  I just cannot see the wireless networks in WICD.  

Help!

---

### Post by imdano on 2009-04-14
Is the corrrect wireless interface name showing up the in wicd preferences window?  Fix it if it's not.  If that doesn't make a difference, try running wicd-client from a terminal window and post any error messages you see.

---

### Post by hurricanesfan66 on 2009-04-14
> **imdano said:**
> Is the corrrect wireless interface name showing up the in wicd preferences window?  Fix it if it's not.  If that doesn't make a difference, try running wicd-client from a terminal window and post any error messages you see.

Wow--easy fix--

How did wicd change the interface name?  It had been working with now.  

Anyway, always the easy fixes.  I appreciate it...

---

