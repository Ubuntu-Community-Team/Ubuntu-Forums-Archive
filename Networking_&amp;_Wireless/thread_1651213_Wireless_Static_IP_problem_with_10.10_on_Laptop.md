---
title: "Wireless Static IP problem with 10.10 on Laptop"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by McC4b3 on 2010-12-22
Hello forum community,
     I'll be frank. I recently switched to Ubuntu 10.10 to become more familiar with linux as I set up a website, but I'm also an avid user in a private torrent tracker.  Coming from windows to linux, I don't know how to properly set up a static IP address from my wirelessly connected laptop. Other walk-throughs for setting up a static IP seem to focus on desktop machines and not a wirelessly connection machine. These walk-throughs also tell me to delete Network manager, which really messes up the ability to find connections for a wireless laptop.  I also have two homes I go back and forth with, so I'd simply like the ability to just emit a static IP, and for my main networks to allow me to connect, and upload/download from it easily. Thanks.

---

### Post by lisanels47 on 2011-01-01
I'm working on the same thing.  I want my wireless clients to connect normally via. network-manager, but when the connection is complete, I'd like to add an alias to the wireless connection such as this in my /etc/network/interfaces file:

iface eth0:1 inet static
address 192.168.1.10
netmask 255.255.255.0
auto eth0:1

I can bring the interface up manually, but need to know where to add it in the post if-up scripts.  When finished, this computer will have and IP like 192.168.1.104 and also a constant IP address of 192.168.1.10.  

Anyone out there able to help with this?

Side-note:  Also looking for a way to startup wireless networking before a user signs in....

Thanks,
Lisa

---

### Post by PatchesTheCaveman on 2011-01-01
Hello all.  Happy new year!

You can replace NetworkManager with a program called wicd, which does the same thing as NetworkManager but can also be configured to connect to your wireless network on boot.

To uninstall NetworkManager and install Wicd, go to Applications > Accessories > Terminal and run the following three commands, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

---

### Post by perspectoff on 2011-01-01
> **PatchesTheCaveman said:**
> Hello all.  Happy new year!

You can replace NetworkManager with a program called wicd, which does the same thing as NetworkManager but can also be configured to connect to your wireless network on boot.

To uninstall NetworkManager and install Wicd, go to Applications > Accessories > Terminal and run the following three commands, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

+1

But you also have to remove other network-manager modules as well (such as network-manager-gnome or network-manager-kde), and reboot once after removing network manager so remove it completely, before installing wicd. Once network-manager is removed, you must be connected by a wired connection to access the Internet, in order to install wicd.

Wicd handles static IP addresses over wireless fine for me.

---

### Post by PatchesTheCaveman on 2011-01-01
> But you also have to remove other network-manager modules as well (such as network-manager-gnome or network-manager-kde)

APT will automatically uninstall those packages when you uninstall the main network-manager package, as they "depend" on network-manager.

---

### Post by xalu on 2011-07-07
> **PatchesTheCaveman said:**
> Hello all.  Happy new year!

You can replace NetworkManager with a program called wicd, which does the same thing as NetworkManager but can also be configured to connect to your wireless network on boot.

To uninstall NetworkManager and install Wicd, go to Applications > Accessories > Terminal and run the following three commands, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

I lost internet after remove. How do I get it to work for just installing? I have an Ethernet connection but its not working...Was working fine before. (its static)


-----

I fixed it by switching my static off. For some reason setting static in my network/interface file is causing connection issues.

---

