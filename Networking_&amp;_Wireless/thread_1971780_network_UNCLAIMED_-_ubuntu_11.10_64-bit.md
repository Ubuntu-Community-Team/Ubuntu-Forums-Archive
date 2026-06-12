---
title: "network UNCLAIMED - ubuntu 11.10 64-bit"
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by Vanish00 on 2012-05-02
I've updated my Ubuntu 11.10 before I actually do the upgrade to 12.04.  However now my computer cannot connect to the internet at all.  I can't copy & paste the results from my terminal but this is where I'm at right now.

ifconfig -a:
   "Only lo (Local Loopback) is detected"

lshw -C network:
   "network UNCLAIMED, product RTL8111/8168B"

lspci:
   "Ethernet controller: Realtek Semiconductor RTL8111/8168B"

Any ideas on getting me back online again?

---

### Post by farrukh_najmi on 2012-06-21
I have the same problem though after upgrading to 12.04.

> **Vanish00 said:**
> I've updated my Ubuntu 11.10 before I actually do the upgrade to 12.04.  However now my computer cannot connect to the internet at all.  I can't copy & paste the results from my terminal but this is where I'm at right now.

ifconfig -a:
   "Only lo (Local Loopback) is detected"

lshw -C network:
   "network UNCLAIMED, product RTL8111/8168B"

lspci:
   "Ethernet controller: Realtek Semiconductor RTL8111/8168B"

Any ideas on getting me back online again?

---

### Post by chili555 on 2012-06-21
Please open a terminal and run and post:```
sudo modprobe r8169
dmesg | grep r816
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by farrukh_najmi on 2012-06-22
Hi chili555, The network UNCLAIMED problem went away after I reinstalled drivers as described here:

[http://askubuntu.com/questions/126227/12-04-wired-network-doesnt-work-rtl8111-8168b](http://askubuntu.com/questions/126227/12-04-wired-network-doesnt-work-rtl8111-8168b)

After that my network kept dropping frequently and required restarting. This is described here and unresolved:

[http://ubuntuforums.org/showthread.php?p=12045961](http://ubuntuforums.org/showthread.php?p=12045961)

Thanks for your kind help.

---

### Post by farrukh_najmi on 2012-06-22
The network unclaimed problem went away after I reinstalled drivers using:

[http://askubuntu.com/questions/126227/12-04-wired-network-doesnt-work-rtl8111-8168b](http://askubuntu.com/questions/126227/12-04-wired-network-doesnt-work-rtl8111-8168b)

After that I have the network dropping frequently for no reason and requiring restart as decsriobed here:

[http://ubuntuforums.org/showthread.php?p=12045961](http://ubuntuforums.org/showthread.php?p=12045961)

The screen too gets garbeled frequently then fixes itself. Its been quite a tough road upgrading to 12.04 whereas ubuntu upgrades were almways smooth in the past.

---

