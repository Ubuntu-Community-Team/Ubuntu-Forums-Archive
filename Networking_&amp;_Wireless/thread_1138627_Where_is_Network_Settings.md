---
title: "Where is Network Settings?"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by rick71 on 2009-04-26
I just did an install of Ibex and Jaunty, and I can't seem to find Network Settings. It was at System -.Administration -> Network in Hardy. And help appreciated.

---

### Post by Another Monkey on 2009-04-26
In Jaunty it's System/Administration/Network Tools, I odn't have Intrepid running at the moment to check that.

The command is "gnome-nettool".  You can run that from the terminal if you need to (you'll probably need to use "sudo gnome-nettool").

---

### Post by rick71 on 2009-04-26
gnome-nettool isn't the same set as "Network" that appeared in the Administration menu in Hardy.

---

### Post by rick71 on 2009-04-26
I checked Hardy. The name of the tool is gnome-network-admin. It did not install when I installed Jaunty. When I tried to run it from the command line, the error message said it was installed, but was available. I installed it, and it now appears in the menu.

---

### Post by doas777 on 2009-04-26
I believe that the network admin package was removed in intrepid, becuause intrepid and jaunty use the gnome-network-manager subsystem. do you see a network-manager icon in your tray? it usually autostarts by default from a link in your System/Preferences/Startup Applications  (formerly "Sessions").

is your network card defined in your /etc/network/interfaces file?

---

### Post by rick71 on 2009-04-26
> **doas777 said:**
> I believe that the network admin package was removed in intrepid, becuause intrepid and jaunty use the gnome-network-manager subsystem. do you see a network-manager icon in your tray? it usually autostarts by default from a link in your System/Preferences/Startup Applications  (formerly "Sessions").

is your network card defined in your /etc/network/interfaces file?

There is a network manager applet icon, however, you can't set DNS or hostnames in mine.

---

### Post by NoExQQ on 2009-04-26
Under 9.04 - System - Preferences - Network Connections and select interface to edit.

---

### Post by doas777 on 2009-04-26
> **rick71 said:**
> There is a network manager applet icon, however, you can't set DNS or hostnames in mine.
are you useing DHCP, or a static address?

either way, you can set your dns servers by configuring your /etc/resolv.conf. here us mine (i redacted a little info):

```

search mydomain.net
nameserver 192.168.xx.yyy
nameserver 2.2.2.1

```

and you can set your hostname in your /etc/hostname. just put your hostname in it and save.

after this restart networking with 
```
sudo /etc/init.d/networking restart
```

---

### Post by rick71 on 2009-04-26
> **doas777 said:**
> are you useing DHCP, or a static address?

either way, you can set your dns servers by configuring your /etc/resolv.conf. here us mine (i redacted a little info):

```

search mydomain.net
nameserver 192.168.xx.yyy
nameserver 2.2.2.1

```

and you can set your hostname in your /etc/hostname. just put your hostname in it and save.

after this restart networking with 
```
sudo /etc/init.d/networking restart
```

Yes, I can do all of that, but can a "general user"? At the mommet, I am thinking network-admin should have been left in.

---

### Post by doas777 on 2009-04-26
> **rick71 said:**
> Yes, I can do all of that, but can a "general user"? At the mommet, I am thinking network-admin should have been left in.

usually a general user would set the hostname at install when asked by the gui, and would receive their dns server settings from their dhcp server. if they had a static address, then you can easily add those in the network-manager. Right Click -> edit connections, go to wired connections, select your connection and click Edit. then go to the last tab, "IP settings" and set your dns servers, as a list, comma delimited.

---

### Post by rick71 on 2009-04-26
So ... no more GUI to set (or reset)  hostnames?

---

### Post by Ittiger on 2009-04-28
Not by default but if you look in add/remove, you can install it with a couple of clicks.  The app. is just called network.

---

