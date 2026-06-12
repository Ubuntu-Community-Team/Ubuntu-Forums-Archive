---
title: "Weird: Wireless disconnects ONLY when browsing to Wikipedia"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by Corvias on 2010-07-13
I've worked in IT for 10 years, and never have I come across this before. My wife has a Dell XPS M1330 laptop, which has an Intel ProWireless. Over the weekend, I did a clean install of Ubuntu 10.04, 32-bit. The install went smooth and everything seems fine, except - I kid you not - Her wireless disconnects every time she goes to wikipedia. When it does this, our wireless router disappears from the NetworkManager tray menu. Even after a reboot, it does not come back. Other routers in our neighborhood show up, but not ours. To get it to come back, we have to shut her laptop down, reset the router, and start her computer up. None of the other machines on our home network do this, including my laptop. 

Also:

- I've installed the backport modules with no effect
- She was previously running 8.04 with no trouble.
- She can get to wikipedia without the wifi disconnecting if she does it through an XP install with a virtualized NAT ethernet adapter inside VirtualBox.

Please don't think this is a joke -I'm seriously stumped on this one! HELP!

Yikes! I just saw the guidlines for posting wifi issues. -- I'll do those steps when I have her laptop on hand later. Sorry!

---

### Post by BbUiDgZ on 2010-07-13
whats her hosts file look like?
```
cat /etc/hosts
```

---

