---
title: "network-manager dependency"
date: 2007-10-08
forum: Mythbuntu
---

### Post by pug on 2007-10-08
```
apt-get --purge remove network-manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mythbuntu-gdm-theme
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mythbuntu-default-settings* mythbuntu-desktop* network-manager* network-manager-gnome*
```

Why would anything mythbuntu depend on network-manager? Sorry, but I fail to understand this.

I'm trying very hard to get RID of network-manager as it seems like it keeps messing up my wireless connection...

---

### Post by tgm4883 on 2007-10-08
> **pug said:**
> ```
apt-get --purge remove network-manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mythbuntu-gdm-theme
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mythbuntu-default-settings* mythbuntu-desktop* network-manager* network-manager-gnome*
```

Why would anything mythbuntu depend on network-manager? Sorry, but I fail to understand this.

I'm trying very hard to get RID of network-manager as it seems like it keeps messing up my wireless connection...

mythbuntu-desktop is a metapackage which installs all parts (one of them being network manager.  mythbuntu-default-settings must set something in network manager therefor it needs network manager installed.

---

### Post by superm1 on 2007-10-08
> **pug said:**
> ```
apt-get --purge remove network-manager
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mythbuntu-gdm-theme
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mythbuntu-default-settings* mythbuntu-desktop* network-manager* network-manager-gnome*
```Why would anything mythbuntu depend on network-manager? Sorry, but I fail to understand this.

I'm trying very hard to get RID of network-manager as it seems like it keeps messing up my wireless connection...
I see the complication here, and I'll see if we can change network manager to be a recommend instead.  It's tied a bit hard to the env right now.

To use a static address or network, click the network manager icon and choose "Manual Configuration".  You can then setup a static access point from the list and/or static IP address.

---

