---
title: "no network manager, no internet to get it"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by akzachernuk on 2010-09-26
So, I have a problem. I've been running Xubuntu on my Toshiba netbook without a problem, until I tried to connect to the wired network just installed in my new flat. NetworkManager saw the network, called it eth0, and let me try to connect to it, but couldn't find an IP address. I went and installed WICD as an experiment, that didn't work, tried it with a static IP, at which point it ran into DNS problems.

In a moment of frustration, I deleted NetworkManager, figuring WICD had brought me closer to getting connected, and I liked the interface better. Trouble is, now WICD won't hook up to the wireless networks at my school either, which means I can't even get a connection to install NetworkManager again, which did the wireless just fine.

I've been looking for network drivers I can install without a connection already, but the only ones I can find need GTK, which I don't have and am finding the same troubles in getting.

Can someone help me fix at least one of my problems here?

Thanks a ton,
Alex

---

### Post by lexfati on 2010-09-26
What error do you get when you try to connect with wicd?  Do you get an authentication failure, or does it just hang forever when you try to obtain an IP address?

---

### Post by akzachernuk on 2010-09-27
it hangs for a long time, then says "Unable to acquire IP address," or something to that effect

---

### Post by lexfati on 2010-09-27
Well, it sounds like your at least making it past the authentication part, which is good.  I understand not having an Internet connection makes it near impossible to get new packages in the event you are missing something.

From the wicd user interface, there is a DHCP Client section under preferences.  You may try changing between them if you have more than one installed.  That had helped me connect when I had problems with a previous version of wicd.

You might also try getting an IP address from the command line.

First, release any IP address you might have on lease:
```
sudo dhclient -r
```Then, obtain an IP address
```
sudo dhclient
```Hopefully, this helps enough to at least get you connected.

Another Alex

---

### Post by akzachernuk on 2010-09-28
right, so, I got the IP thing figured out it seems, and now I get hung up on "Verifying access point" and "Connection failed: could not contact the wireless access point." This happens on both DHCP options Any thoughts?

---

