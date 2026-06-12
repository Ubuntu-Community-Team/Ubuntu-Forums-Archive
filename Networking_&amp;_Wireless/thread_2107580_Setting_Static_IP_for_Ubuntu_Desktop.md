---
title: "Setting Static IP for Ubuntu Desktop"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by chilisastry on 2013-01-22
Changing to a static IP address (including DNS servers) in Ubuntu Desktop (12.04) by editing the /etc/network/interfaces file, followed by ifdown eth0, if up eth0, does not work well for browsers.  The browser is unable to do DNS lookup for the web-site, and returns with a web-site not available error.

On a fresh install of Ubuntu, I changed to a Static IP address using the Connection Manager.  Browsing works fine now.  However, the /etc/network/interfaces file comntains just these lines:

auto lo
iface lo inet loopback


Does it mean that the Connection Manager does not store the static IP parameters in this file?

On a server (not desktop), setting the static IP address in the /etc/network/interfaces file works fine (I am able to do a apt-get install).

Can someone clarify what is going on?

---

### Post by Bucky Ball on 2013-01-22
You shouldn't need to edit that file on a regular machine with a desktop environment. Use Network Manager. Easier. That will write the changes to it anyway. 

Right click network icon and Edit Connections. Set 'Method' to 'Manual' under IPv4 tab (I use Xubuntu but should be the same) and choose a static IP and insert the gateway IP (IP of your router usually). The netmask is generally 255.255.255.0

Add the DNS IPs as provided by your ISP. You may need to dig around on the site or email them for these. If you have a few computers in a domain, add the name of that, too.

Should be good to go ...

Once you're done, check the /interfaces file and that should reflect the changes you have made.

---

### Post by steeldriver on 2013-01-22
I agree with Bucky - set it through the network manager applet

One small correction though - network-manager doesn't use /etc/network/interfaces, it has its own config file /etc/NetworkManager/NetworkManager.conf and saves the actual connection information in /etc/NetworkManager/system-connections/ (at least in 12.04)

You should revert any changes you made in /etc/network/interfaces - that is supposed to only contain the lo (loopback interface) definition when network-manager is being used for external connections

---

### Post by brent1975 on 2013-01-22
Here is what mine looks like and I don't use that network manager. I do mine old el naturel!!  :) 


```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

    address 192.168.2.106
    netmask 255.255.255.0
    network 192.168.2.0
    gateway 192.168.2.1
    broadcast 192.168.2.255

    dns-nameservers 192.168.2.1 8.8.8.8
    dns-search google.com
```

---

### Post by ahallubuntu on 2013-01-22
You don't have to use Network Manager to set a static IP - but if you wish not to use it, you should uninstall it and do everything with the terminal, including setting a static IP.  If you want to keep using Network Manager at all, don't edit your /etc/network/interfaces file - use the GUI in Network Manager to set your static IP instead.

---

