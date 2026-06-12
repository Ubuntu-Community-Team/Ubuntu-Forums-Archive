---
title: "Setting static IP address"
date: 2009-08-15
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-08-15
I originally configured my Mythbuntu box to use DHCP, but I've realised that static IP would be better (mainly because of the need to set the IP address of the backend server if I want other devices on my network to be able to use it).

If I right click on the network icon in the top right of the screen in the Ubuntu desktop, I can change the network settings, but my changes are ignored. Is this something to do with permissions? I don't seem to be entering a root password anywhere to be able to make the changes, and I'm guessing that you need root permissions to change the IP address.

Is that right? If so, how do I change the IP address as root?

Thanks
NM

Mythbuntu 8.10

---

### Post by s3MA00RRNY on 2009-08-15
No, you don't. I've done it many times. You only need root permissions to change the settings system-wide. I can't really understand why it wouldn't be working.

---

### Post by ian dobson on 2009-08-16
Hi,

Maybe get rid of network-manager and manually configure your network configuration by editing /etc/networks/interfaces

And add something like:
```

auto lo
iface lo inet loopback

#On board RTL adapter
auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.254

```

You'll need to be root to edit this file and you'll need to reboot after making the changes.

Regards
Ian Dobson

---

### Post by joho500 on 2009-08-16
I use wicd network manager ([http://wicd.sourceforge.net]("http://wicd.sourceforge.net/")). It replaces the default network manager. I started using it when I had the same problems with the default Gnome network manager in Ubuntu. 

It works like a charm

Joost

---

### Post by NautiusMaximus on 2009-08-16
Many thanks for the helpful suggestions.

I decided to go with the wicd option, and it did indeed work like a charm. I now have a static IP address.

---

