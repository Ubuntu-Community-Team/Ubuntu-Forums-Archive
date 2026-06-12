---
title: "Attempting to connect to PPTP VPN in Intrepid"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by maxmartin on 2009-02-11
I'm running Intrepid and attempting to connect to my school's Windows VPN. I've had no luck with Network Manager, so I'm attempting to install pptp-config. Unfortunately, when I try to, it complains that it can't install the dependency package php-gtk-pcntl. I tried manually grabbing the .debs for php-gtk-pcntl and php-pcntl from the pptp-config site (as per another thread I found), but when I try to install them, they complain about libglade0. When I try to install libglade0, I get this mess:

```
Package libglade0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libglade0 has no installation candidate
```

Please help! I just want to get access to my school files from home...

---

