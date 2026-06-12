---
title: "Network configuration files"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by martin_legion on 2009-06-17
I recently installed kubuntu and I couldn't get the wired connection to work. I tried and tried with the network manager GUI but no case. So then I realized that I had no idea where to look.
I normaly use Ubuntu (forget about Kubuntu, it's not for me), and I have the network configured and working (thanks to the Network config GUI), but I want to know how to configure the network "by hand". So I googled a little: I've found my DNS in /etc/resolv.conf, no problem with that.
Then went to see what's inside of /etc/network/interfaces, and I found this:
```
auto lo
iface lo inet loopback
```
That's great, but where's my STATIC IP and my gateway?
I'm familiar with the network config files of Mandriva, but, which are they in Ubuntu.
(I'm using Jaunty, just in case)

Thank you!

---

### Post by t0mppa on 2009-06-17
By hand, you've found the right files for it. /etc/network/interfaces is the place for the static IP, gateway, netmask and wireless definitions while nameservers go to /etc/resolv.conf like you said.

However, Network Manager doesn't handle the configurations specified there very well. There's managed mode that's been added in the latest versions that you can set in the /etc/NetworkManager/nm-system-settings.conf file. According to the documentation it checks the interfaces file for configurations and should work with those, but that's disabled by default on Jaunty and personally I've never tested how well that works in practice.

If you want to find the location of the settings you specify in the GUI, the Gnome network manager stores them in gconf. Not sure about KDE's manager, I stopped using it pretty quick due to the buggy nature of its Jaunty version and swapped to WICD.

---

### Post by Iowan on 2009-06-17
You can set up a static address in (Ubuntu's) Network Manager, or you can configure it in */etc/network/interfaces*.  On my laptop, it worked either way.  If you configure it directly into */etc/network/interfaces*, NM may complain a little (I haven't tried changing the "managed=" setting).

---

### Post by martin_legion on 2009-06-18
Ok, thank you for the replies.
I still think configuration files should be in one place, and should be standard, and not depend on which distro you are running.
Anyway...
Thanks again!

---

