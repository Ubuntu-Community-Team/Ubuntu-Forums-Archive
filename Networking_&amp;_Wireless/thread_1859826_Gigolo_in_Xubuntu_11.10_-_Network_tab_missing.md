---
title: "Gigolo in Xubuntu 11.10 - Network tab missing"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by Kronalias on 2011-10-14
I'm having real difficulty in getting Gigolo to browse my network in Xubuntu 11.10, although it works just fine if I boot into Ubuntu 11.10

I've attached two screenshots that show the problem...

The shot on the left (Gigolo in Unity) is from Ubuntu, and shows the Network and Bookmark tabs in Gigolo. That's how it should be.

The shot on the right (Gigolo in Xfce) is from Xubuntu, and shows the Bookmark only tab in Gigolo - i.e. the Network tab is missing, and there's the problem.

Can anyone help me get Gigolo going in Xubuntu 11.10 please?

Thanks in advance, K

---

### Post by Morbius1 on 2011-10-14
I just installed Xubuntu 11.10 myself and noticed that not only Gigolo but running the following in Thunar doesn't work either:
```
network://
```OR
```
smb://
```I poked around in Synaptic and discovered that a package was missing:
```
sudo apt-get install gvfs-backends
```

---

### Post by Kronalias on 2011-10-14
Thanks very much - that's sorted it!

After you've installed it you just need to log out and back in, and Gigolo works.

Cheers, K

---

### Post by kholis on 2011-10-18
It's also happen to me on Xubuntu 11.10 fresh installation. 

Thanks to Morbius1

---

