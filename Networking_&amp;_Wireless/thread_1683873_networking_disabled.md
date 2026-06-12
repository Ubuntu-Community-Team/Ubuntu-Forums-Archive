---
title: "networking disabled"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by parimaln on 2011-02-08
hi i have internet working but the network manager applet in the ubuntu 10.10 says that it is disabled and i am not able to enable it however i have previously forced the ip address which i am still getting in ifconfig

but in wired section of network connections there is no such interface as eth0 where can i see these settings and how can i enable the etwork manager applet in the title bar thanks in advance

---

### Post by ephestione on 2011-03-30
I am having the same exact problem, and I will try to circumstanciate:

I installed ubuntu server 64bit, and then minimal gnome over it:
```
sudo apt-get -y install gnome-core gdm network-manager-gnome fast-user-switch-applet human-theme x11-xserver-utils tangerine-icon-theme gnome-themes-ubuntu ubuntu-artwork jockey-gtk gnome-screensaver gnome-utils
```So it's not a proper ubuntu-desktop package, but it's a server so who cares.

Anywho, network works like a charm, it's just that I cannot make network-managet-gnome "see" it.
I have had limited  success with Wicd, which sees it, and I can change the dynamic ip by DHCP to a static one, but the settings are not remembered at next boot, while network-manager tells me networkin is disabled, even if it's not, and if I right-click on the notification area icon, and select "edit connections", I see nothing in the wired networks pane... no idea how to "hook" network-manager-gnome with networking, as ifconfig shows it fine.

EDIT: solved by this post: [http://ubuntuforums.org/showpost.php?p=10591919&postcount=5](http://ubuntuforums.org/showpost.php?p=10591919&postcount=5)

EDIT2: solved partially, as I can now see the connection listed under wired connections, but the edit button is grayed out so I cannot modify it in any way :(

---

### Post by bkratz on 2011-03-30
In case you originally set up you connection in /etc/network/interface, Network Manager does not manage anything found there.

Normally that file should only say:

auto lo
iface lo inet loopback

If this answers your questions.

---

### Post by ephestione on 2011-03-31
Hello bkratz
and thanks for the feedback :)
Your reply gave me hope for a while, until I went there and checked the /etc/network/interfaces file... it contains exactly that already, excluding some comments.
So I am back at square one.
My /etc/NetworkManager/nm-system-settings.conf file contains:
> [main]
plugins=ifupdown,keyfile

no-auto-default=00:1b:38:1b:a8:93,

[ifupdown]
managed=false



Changing the manahed to true I can see the network interface on network manager listed as ifupdown(eth0), but I cannot edit it yet.

---

### Post by dineshs on 2011-03-31
> EDIT2: solved partially, as I can now see the connection listed under wired connections, but the edit button is grayed out so I cannot modify it in any way
1)Did you select (click on) the connection before trying to edit?
2)When you run ```
gksudo nautilus /etc/NetworkManager/system-connections
```Is there a file corresponding to your ethernet connection.When opened a part of the file should look like ```
[ipv4]
method=manual
dns=4.2.2.1;8.8.8.8;
addresses1=192.168.1.222;24;192.168.1.1;

```
Have you tried editing this file ?(IP,mask,gateway and DNS)

---

### Post by ephestione on 2011-04-01
> **dineshs said:**
> 1)Did you select (click on) the connection before trying to edit?

Naturally :p
But I think it's a "did you try to turn it off and on again?" kind of question to clear the basics, so it's okay :D

> 
2)When you run ```
gksudo nautilus /etc/NetworkManager/system-connections
```Is there a file corresponding to your ethernet connection.When opened a part of the file should look like ```
[ipv4]
method=manual
dns=4.2.2.1;8.8.8.8;
addresses1=192.168.1.222;24;192.168.1.1;

```Have you tried editing this file ?(IP,mask,gateway and DNS)

this is curious, I have no files in that path.

---

