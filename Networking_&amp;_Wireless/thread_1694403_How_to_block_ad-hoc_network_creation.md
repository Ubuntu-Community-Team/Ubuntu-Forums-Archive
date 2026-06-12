---
title: "How to block ad-hoc network creation"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by bellera on 2011-02-24
Hello!

I'm administering a wireless network with more than 200 notebooks
running network-manager (Ubuntu 10.04 LTS).

Some users are creating ad-hoc networks. This is a problem because
originates WiFi noise and can be also a security problem.

Is there any way to block ad-hoc network creation with network-manager
configuration?

I looked at /etc/NetworkManager/nm-system-settings.conf and search
information about it at the Internet. I can't find information about.

I tried some changes like:

[802-11-wireless]
mode=infraestructure

And I restarted the service:

/etc/init.d/network-manager restart

but no results.

I looked also NetworkManager.conf and nm-applet.conf at
/etc/dbus-1/system.d but I don't understand how they work.

Any idea?

Thanks in advance,

Josep Pujadas-Jubany

---

