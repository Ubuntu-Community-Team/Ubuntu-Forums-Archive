---
title: "Static wireless ip"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by wootwoot123 on 2006-06-23
I am trying to figure out how to setup a static ip on my ubuntu laptop that is connnected by wifi. My router has no setting for this and in windows I am able to assign my ip in the network settings and everything connects fine. How can I do this in linux?

---

### Post by Ptero-4 on 2006-06-23
ifconfig might be what you're looking for.

---

### Post by nixternal on 2006-06-23
Use the text editor of your choice. I use nano, you may use Kate or Gedit, replace nano with the text editor you choose.
```

# sudo nano /etc/network/interfaces

```

This will open up a window that probably looks similar to this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 <- or whatever your network port is wlan0 maybe
iface eth0 inet dhcp

```

You want to change # The primary network interface to look like:
```

auto eth0
iface eth0 inet static
              address 192.168.1.100 (or whatever ip you want)
              netmask 255.255.255.0
              network 192.168.1.0
              broadcast 192.168.1.255
              gateway 192.168.1.1

```

After you get that in, save it and close out (if using nano, do ctrl+x and then say yes to save and close). AFter that restart networking by:
```

# sudo /etc/init.d/networking restart

```

now you have static!!!  I know there are graphical versions, but im a terminal type of person. Enjoy :)

---

