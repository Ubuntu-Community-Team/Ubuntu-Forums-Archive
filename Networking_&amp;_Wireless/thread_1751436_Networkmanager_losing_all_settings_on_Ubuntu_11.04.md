---
title: "Networkmanager losing all settings on Ubuntu 11.04 64 bit"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by maverick280857 on 2011-05-06
Hi,

I found several threads addressing a similar problem, but neither of the remedies suggested there worked. So I decided to start a new thread.

I am using a Dell XPS 15 laptop to connect to a wireless connection at home. I use Network Manager, and it loses all my static DNS settings.

For now, I have made a custom /etc/resolv.conf.old and every time I log in, I have to manually do

```
sudo cp /etc/resolv.conf.old /etc/resolv.conf
```

to get the network to work.

Is there a permanent way to store my nameservers (at least), in Ubuntu 11.04?

Thanks in advance!

---

### Post by maverick280857 on 2011-05-07
```

sudo apt-get remove network-manager*
sudo reboot
sudo apt-get install wicd wicd-gtk

```

Then, set static DNS in wicd.

Works so far in GNOME3 :-)

---

