---
title: "I messed up network configuration"
date: 2011-01-29
forum: Networking &amp; Wireless
---

### Post by Superdust on 2011-01-29
Hi

I`m relatively new to Linux and Ubuntu.

Now I have been playing around, editing the settings files for the networks cards, and now I have messed things a bit up.

Any way to delete all settings, and make Ubuntu autodetect my hardware again?
Just want to start over again :)

This is Ubuntu 10.04 LTS.

---

### Post by sikander3786 on 2011-01-29
From Applications > Accessories > Terminal, please post the output of this command.

```
cat /etc/network/interfaces
```

---

### Post by Superdust on 2011-02-01
```
cat /etc/network/interfaces
```

Gives:

```

auto lo
iface lo inet loopback

auto eth0_rename
iface eth0_rename inet static
address 10.10.10.5
netmask 255.255.255.0
network 10.10.10.0
broadcast 10.10.10.255
gateway 10.10.10.1

```

And it kinda works now on one network card.
But I have two cards in the machine.

And the name eth0_rename was something that came up when I was playing around.

Is there any way to get back to basics?
Delete all config, and make it autodetect the two cards again.
Eth0 and eth1...

---

### Post by sikander3786 on 2011-02-02
If you want to make manage your connections using network manager in system tray, just edit your /etc/network/interfaces.

```
gksudo gedit /etc/network/interfaces
```

Delete everything except these 2 lines.

```
auto lo
iface lo inet loopback
```

Save and reboot. Hopefully, your Network manager should once again take control of your connections.

---

