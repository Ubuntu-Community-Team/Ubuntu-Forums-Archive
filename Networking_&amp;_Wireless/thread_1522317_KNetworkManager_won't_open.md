---
title: "KNetworkManager won't open"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by MountainX on 2010-07-02
I have a new install of Kubuntu 10.04. When I click Network Manager in the main menu it acts like it is going to open, but then no window comes up. There is no error, but the app never opens. Any ideas?

---

### Post by Arkold Thos on 2010-07-02
Same problem, plus the networking doesn't even work (with knetworkmanager, ifup, ifdown, restart networking) :/ I have to join single-user mode, then netroot, then resume the startup and start kdm

---

### Post by MountainX on 2010-07-02
> **Arkold Thos said:**
> Same problem, plus the networking doesn't even work (with knetworkmanager, ifup, ifdown, restart networking) :/ I have to join single-user mode, then netroot, then resume the startup and start kdm

It would be nice if someone would give us some troubleshooting steps.

I'm thinking about purging the networking related packages and then reinstalling, but I'm not sure which packages to purge.

Would this do it?
```
apt-get –purge remove network-manager knetworkmanager network-manager-kde dhcdbd
```
But if I purge those packages, will the package manager be able to reinstall them without a network?

I'm also wondering if a reconfigure might do it:
```
dpkg-reconfigure knetworkmanager
dpkg-reconfigure network-manager-kde
```
or maybe this:
```
dpkg-reconfigure -fnoninteractive -a --force
```

Some feedback from someone who knows what to do would be great.

---

### Post by MountainX on 2010-07-02
none of the dpkg-reconfigure stuff I tried worked... however:

**_Solved_**

It's a bug. See this link
[https://bugs.launchpad.net/ubuntu/+bug/555571](https://bugs.launchpad.net/ubuntu/+bug/555571)

This fixed my problem:
    service network-manager stop
    rm /var/lib/NetworkManager/NetworkManager.state
    service network-manager start

---

