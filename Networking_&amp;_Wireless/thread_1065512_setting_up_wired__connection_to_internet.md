---
title: "setting up wired  connection to internet"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by edthetermite on 2009-02-09
looking for wired network directions to set up new install.
I have a dual boot os that has XP up and running and connected to the internet through a wired LAN connection. Ubuntu is not seeing the settings and I need info.

Thanks,

Ed

---

### Post by jerrrys on 2009-02-10
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by issih on 2009-02-10
If you have a router, then typically that will serve ip addresses by dhcp, so the only thing you'd need to do is plug the cable in and ubuntu should just pick up the connection and start functioning.

As you state that this isn't happening I can only presume that you are plugging into a network that uses static ips.

In order to get this to work you need to boot into xp, go into the network preferences page and look at the details of the lan connection, I forget exactly where it secrets the data away, but somewhere in the settings are the tcp/ip settings.

From there you need to grab the ip address and subnet mask and the default gateway.

With these come back into ubuntu and set the lan connection to use these same values.

Hope that helps

---

### Post by Iowan on 2009-02-10
If the Windows side is working, you can use it to verify whether the connection is static or DHCP. It is possible that you may need different drivers for your card.  **ifconfig -a** and **lshw -C network** (maybe **lspci**) can shed some light as to what is going on.
It's possible DNS or gateway address needs to be adjusted... but first, the card must have valid IP address.

---

