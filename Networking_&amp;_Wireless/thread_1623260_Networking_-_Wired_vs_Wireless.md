---
title: "Networking - Wired vs Wireless"
date: 2010-11-16
forum: Networking &amp; Wireless
---

### Post by bradb59 on 2010-11-16
I notice this problem quite a bit...

I start up ubuntu on my laptop and the wired cord connected, it works no problem.

Then I go wireless for a while, works no problem

Then I reconnect the cord and instead it connects to the wireless, when I go and disable the wireless it just goes offline instead of using the wired.

In this state ifconfig shows eth0 as being up, but with no IP address.

The hardware is:
Wireless: Broadcom BCM4312
Wired: Realtek RTL8101E

Any ideas on how to "force" the laptop to use wired would be fantastic.  I did try restarting /etc/init.d/networking, but the only way I can use wired again at this point in time is to reboot, which I would prefer not to do.

thanks!

---

### Post by pricetech on 2010-11-16
Just a thought;  Have you tried disabling wireless before you connect the wired ??  Might help.

---

### Post by bitscarre on 2010-11-16
Try to disable networking and wireless from the network manager and then reenable only networking and not wireless.

An auto connection should appear in the network manager applet, telling you that it automatically connected to the wired connection.

---

### Post by bradb59 on 2010-11-17
yes, I have tried different combinations of disabling wireless, enabling networking, still nothing.

For some reason my wired will not get an IP address...

I guess the interim solution is to remove and install the kernel module, just seems like this should be handled a little more cleanly....

---

### Post by peyman on 2010-11-17
Try setting up manual IP addressing using ip command and see if it works.

```

sudo ip link set down dev wlan0
sudo ip link set down dev eth0
sudo ip link set up dev eth0
sudo ip addr add 192.168.0.1/24 dev eth0

```

---

