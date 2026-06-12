---
title: "up / post-up route add doesn't work"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by garyjj on 2010-02-18
I have uninstalled network-manager and am using a plain, vanilla, etc/network/interfaces file to configure networking. I have the following:

auto eth0
iface eth0 inet ipv4ll
    post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw myserver.local dev eth0:avahi

the route never gets added. ever. I have to do it manually from the commandline after every reboot.

I thought maybe this had to do with avahi, but, alas, no. On another machine I have:

iface eth1 inet dhcp
    post-up route add -net 0.0.0.0 netmask 0.0.0.0 gw myserver.local dev eth1

same exact thing.

I've tried using 'up' instead of 'post-up', same thing.

Why is networking so horribly broken on ubuntu?

Oh, and I don't use network-manager because that seems to do per-user settings that get lost/changed when each user logs in / out. These are workstation machines that double as servers. I can't have my nfs shares disappearing when different users login/out. That's silly.

---

