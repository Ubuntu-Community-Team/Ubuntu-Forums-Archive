---
title: "static IP, and filtering in synaptic"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by IQRules on 2009-03-03
I did this,

$ sudo aptitude uninstall network-manager-gnome

When I issue " # apt-get update; apt-get upgrade", I do not want to reload the network-manager.

How to filter the checking on certain packages?

Thanks

---

### Post by N04h on 2009-03-04
What is the issue or what are you trying to achieve?

Is there a particular reason you don't want to reload?

Have you tried doing the update-upgrade commands?  You should update your system periodically anyway.

---

### Post by N04h on 2009-03-04
Did you try running those commands that it gives you?
```

sudo apt-get update
sudo apt-get upgrade
```

I don't think that will install the network monitor if you don't already have it installed.  Does it list it in the list before you say yes or no?

---

### Post by IQRules on 2009-03-08
Good, it does not re-install at all. I use static IP here, so I do not need network-manager.

Thanks

---

