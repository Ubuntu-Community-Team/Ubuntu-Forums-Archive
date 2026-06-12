---
title: "Yes, Wireless Isn't connecting, but I don't think it's ndiswrapper!"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by ryancarpenter on 2008-12-19
Hey, as you may guess I'm new to linux/Ubuntu and am getting used to working with the different structure.  Here is the issues:

To my knowledge, I've set up ndiswrapper successfully because in all my checks, the terminal acknowledges the existence of my card.  In fact, I can successfully use the driver and check for wireless networks and attempt to connect to them.

Herein lies the problem: each attempt to connect to my home network fails.  I am entering the WPA2 key properly, because during each attempt, the animation shows a green light on the bottom part of the icon only when I enter the right key.  From that point, it'll churn and go back to "no network connection."

I've tried every FAQ I've seen, on this site and others.  My only suspicion is an ndiswrapper -l shows two installed drivers--bcmwl5 and oem3, both with the same device ID.  I tried blacklisting one or the other but it didn't really do anything.

Any ideas?

---

### Post by rixtr66 on 2008-12-19
I had the same problem with ndiswrapper it doesnt connect to wpa.
so i installed the latest madwifi driver 0.10.5.6 supports wpa.
and i uninstalled network manager and installed wicd.
that solved my problem.im running an atheros pci express card.
i dont know if this will help you but it worked for me!
hope it works for you!!!
Rick):P

---

