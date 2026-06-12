---
title: "ICS lan and wlan card bug?"
date: 2012-02-22
forum: Networking &amp; Wireless
---

### Post by sale666 on 2012-02-22
Hello i have a setup that consist of my main pc dual booting windows7 (gaming) and linux ubuntu 11.10 (work)
my pc connects to internet via a wlan card.
my lan card connects to an access point that gives internet to all wlan devices in range of my pc as follows:

(clients)<----[AP]<--->(lan)<--->[DualBoot Machine]<--->(wlan)<--->[Router-internet]--->

In windows everything works fine i enabled routing set static ip's that i needed mostly for ports and its fine.. however on linux i cannot get internet access with clients connection over AP but i can ping the AP and the LAN connection without problems!
I found this:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/881284](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/881284)

seems theres a bug can some 1 confirm this still active as i have issues netowrk connecting disconnecting when i set "share this connection" in network manager!

There is a work around that did not work for me in fact didnt really work for most.. its disabling ipv6 and killall maquarade in term..

thanks!
but no effect

---

### Post by roelforg on 2012-02-22
Let me check my pc (it functions as a router for my cluster)...
Ah!

Run:
```

sudo echo 1 > /proc/sys/net/ipv4/ip_forward

```
This enables packet forwarding.

---

### Post by roelforg on 2012-02-22
> **roelforg said:**
> Let me check my pc (it functions as a router for my cluster)...
Ah!

Run:
```

sudo echo 1 > /proc/sys/net/ipv4/ip_forward

```This enables packet forwarding.

Now if i'd only could remember the config you've got to change to make this persistent...

---

### Post by sale666 on 2012-02-22
Hi roelforg! Thanks for your reply i did that and made it persistent i found that on ubuntus documentation! however what keeps happening wireless keeps turning on and off and ICS is not working i only get local conectivity but it does not let me connect to internet!

---

### Post by roelforg on 2012-02-22
> **sale666 said:**
> Hi roelforg! Thanks for your reply i did that and made it persistent i found that on ubuntus documentation! however what keeps happening wireless keeps turning on and off and ICS is not working i only get local conectivity but it does not let me connect to internet!
There's a wiki article about this; i remember that there are extra steps (i don't remember what they were...).

---

