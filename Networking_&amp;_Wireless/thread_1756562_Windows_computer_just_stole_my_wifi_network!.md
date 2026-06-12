---
title: "Windows computer just stole my wifi network!"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by aronstandley on 2011-05-12
A friend came by, and we tried to log her on to our wifi network when she was having trouble accessing it with her Windows (Dist #) machine.

The wifi network itself was set up with macs, and had standard, open settings as far as I could tell - no password, NETGEAR title of the network.

The Windows computer prompted us for a Security Pin, which we gave it from the router, and then all of the computers already on the network got dropped, while the Windows machine got set up onto the wifi, renamed the network with its own username, and automatically set up a password.

I'm currently on the network using LAN, but can't figure out how to set up the network through Ubuntu back to the original settings for the rest of the people that need to access the network.

Specs:
I'm running Ubuntu 11.04,
The Windows machine is unknown right now. I'll repost if that will help.
The wifi router is a Netgear Wireless N 150 WSR 1000, with the serial, mac, and security pin numbers.



What can I do?

---

### Post by doas777 on 2011-05-12
it sounds like your router enabled "Wireless Protected Setup" for devices, so I woudl go in and disable it. the PIN in an indication of WPS. if you can't get into the router admin interface, just use a pen to reset it to defaults (there should be a little hole in the back of the router; insert the pen and hold the little button inside down, until the lights on the front make a drastic change. ) check the netgear documentation for quick start guides before you reset it however, as you may not have internet once you do.

---

### Post by aronstandley on 2011-05-12
Solved.

I went through Netgear's admin website, [http://routerlogin.net](http://routerlogin.net) with the login information given by the Netgear Router pdf, found online with a google search.

Then: Wireless settings > Redefined the SSID name; Security Options: None
Saved.

Then we're back online.

:)

---

