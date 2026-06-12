---
title: "edit/delete greyed out for wired connection in nm-applet"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by acabre on 2011-01-28
I have an entry in my list of wired connections in nm-applet which
(1) is auto connecting by default whenever I use my ethernet nic, and
(2) I cannot delete, because the edit and delete buttons are greyed out (see attached screencap)

I am wondering if anyone knows how to make it possible to remove the connection through nm-applet, or where the list is stored on the filesystem so I can just manually edit it?

--- info ---
$ apt-file find $(which nm-applet)
...
network-manager-gnome: /usr/bin/nm-applet
$ dpkg -l network-manager-gnome
...
ii  network-manager-gnome    0.8~a~git.20091014t13453 network management framework (GNOME frontend)
$ cat /etc/issue
Ubuntu 9.10 \n \l

---

### Post by grahammechanical on 2011-01-28
Do you have administrator permissions?

Regards.

---

### Post by acabre on 2011-01-28
Yes, I am an admin/sudoer.

However, the buttons are only greyed out for the problem connection, so I don't think it's permissions related.

---

### Post by acabre on 2011-02-04
bump?

---

### Post by dineshs on 2011-02-05
What happens when you run ```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
``` make ```
managed=true

```and restart.
Also please post the contents of /etc/network/interfaces```
sudo cat /etc/network/interfaces
```

---

### Post by acabre on 2011-02-06
Setting managed=true in /etc/NetworkManager/nm-system-settings.conf makes no difference post reboot. Edit/delete are still greyed out.

However, there is a n900 entry in /etc/network/interfaces:
```

$ cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto n900
iface n900 inet static
	address 192.168.2.14
	netmask 255.255.255.0
	up iptables -A POSTROUTING -t nat -s 192.168.2.15/32 -j MASQUERADE
	up echo 1 > /proc/sys/net/ipv4/ip_forward
        down iptables -D POSTROUTING -t nat -s 192.168.2.15/32 -j MASQUERADE
	down echo 0 > /proc/sys/net/ipv4/ip_forward

```

Commenting it out removes the entry in nm-applet.

Thanks for your help!

---

