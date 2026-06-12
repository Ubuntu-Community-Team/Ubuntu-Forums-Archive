---
title: "Fixed IP Address"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by spegru on 2010-10-26
Hi, I need to configure a Fixed IP address but i cant find out how to do it in 9.10 (OK Linux Mint 8 in reality).
I right clicked the network icon and selected Edit Connections. Then I tried to add a new wired connection and chise IPv4 settings, copied the Mac address from the original one and put in the address and put in 192.168.2.1 with netmask 255.255.255.0. I left dns and gateway blank.
Problem is the system wont let me Apply!

Help please!

---

### Post by SlugSlug on 2010-10-26
may not suit you but I always do this firstly by removing network manager

apt-get remove nework-manager

and the editing /etc/network/interfaces

sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.254

set to your own settings,

sometimes its needed to add your gateway IP address to /etc/resolv.conf  as a name server

nameserver 192.168.1.254

---

### Post by spegru on 2010-10-31
Thanks, I'm sure that would work
However I'd prefer not to uninstall network manager as it seems to work very well for most things incl 3G dongles and mobile phone connections.

I did find one way to temporarily fix an IP address though - simply by opening a terminal and typing

sudo ifconfig eth0 192.168.2.1

If anyone else wants to do this you will have to remember to replace the eth0 with the name of your ethernet adaptor and the IP address with the one you want. You have to redo this after every reboot though.

On one occasion I also had to add 'up' to the end of the command string to turn the interface on

Oddly, when set up this way, network manager still thought it was offline!

BTW, why did I want to do this? because I wanted a direct connection to a windows machine, when there was no DHCP server available. This way, I was able to open a shared folder on the windows machine and stream the content (an AVI movie) for projection on an external monitor using gnome-mplayer. Worked very well!

I'd still like to know why I couldn't simply apply the IP settings from network manager though!

---

