---
title: "Odd network problem"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by capennington on 2009-04-02
I'm new to ubuntu but i've been working really hard to get familiar with the system.

Managed to get my wifi working but then I installed the updates and POOF back to nil.  I'm using ubuntu 8.10

At first there was an ip conflict, got it sorted but now it won't list my wireless networks.  When i click the network manager on the toolbar it goes down and underneath it says "Network is unmanaged" or something along those lines.

I checked my ifconfig and iwconfig and saw a mode: managed but that can't be right cause it's saying unmanaged?

I'm stumped with this one and any help would be great -- wanna get my system back online ASAP.

Thanks,
Colby

---

### Post by abyssius on 2009-04-02
This may be a bug. [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/280417"). If you read through the thread, someone claims to have fixed it by editing their *nm-system-settings.conf* file: 
> ...I've managed to solve it by change managed=true in /etc/NetworkManager/nm-system-settings.conf... 

---

### Post by superprash2003 on 2009-04-03
post output of the following
1)lshw -C network
2)iwconfig
3)ifconfig
4)iwlist scanning

---

### Post by CyberMando on 2009-04-03
If /etc/NetworkManager/nm-system-settings.conf contains 
[ifupdown]
managed=false
which it does by default, and /etc/network/interfaces contains wlan0 network-manager will see your wlan0 as unmanaged.

---

### Post by capennington on 2009-04-03
Thanks for the help.  I think I managed to get it fixed and I'm back online again.

Cap

---

