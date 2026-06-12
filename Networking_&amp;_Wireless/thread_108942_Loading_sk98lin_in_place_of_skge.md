---
title: "Loading sk98lin in place of skge"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by gsdefender on 2005-12-27
I have been experiencing several troubles using skge in place of sk98lin to manage my Marvell Yukon Gigabit Ethernet board; while in Slamd64 and Gentoo I could default loading sk98lin in place of skge, I could not figure out how to do that in Ubuntu. I tried putting 

```
sk98lin
```

in /etc/modules, and 

```
alias eth0 sk98lin
```

in /etc/modules.d/aliases

but nothing happened. It seems to me that module loading is handled somewhat strangely - as to me - at the very first of the boot process, and I don't know how to force a change. I would be really glad for any help.

---

### Post by Lambert on 2005-12-29
to prevent a module from loading add it to /etc/hotplug/blacklist

```
sudo echo "blacklist skge" >> /etc/hotplug/blacklist
```

with sk98lin in /etc/modules that should be ok to load that module.

---

### Post by gsdefender on 2006-01-02
Thank you so much!

---

### Post by gsdefender on 2006-01-06
Well, no way. Skge continues to be loaded. Any other idea?

---

