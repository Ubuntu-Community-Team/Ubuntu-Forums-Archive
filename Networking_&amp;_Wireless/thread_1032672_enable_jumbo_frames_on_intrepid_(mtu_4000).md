---
title: "enable jumbo frames on intrepid (mtu 4000)"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by graysky on 2009-01-06
I'm using Intrepid-amd64 and currently Gnome's NetworkManager Applet is setting up my NIC via DHCP.

I found that I can right-click the applet>edit connections and there is a blank for 'mtu' which defaults to 'automatic.'  I can manually type in 4000 and then I assume it's using the 4k frame size.

I'd like to know how I can enable jumbo frames (mtu size = 4000) and have the setting stay retained on a reboot.

---

### Post by graysky on 2009-01-07
I never did find out how to do this in the GUI [nm-applet], but a google search unearthed [this thread](http://ubuntuforums.org/showthread.php?t=163749).  One solution basically involves a simple script that's called at boot to do it via ifconfig.  You must also DISABLE your nm-applet (gnome network manager) or else it will NOT work.  Disable it by system>preferences>session.  Now find the auto startup for the network manager and uncheck the startup.

Now make the script.  Let's call it [color=green]setMTU[/color]:

```
#!/bin/bash
/sbin/ifconfig eth1 mtu 4000
```

Now just paste that 2-liner into /etc/init.d/setMTU and do the following:

```
$ sudo chmod 755 /etc/init.d/setMTU
$ cd /etc/rcS.d
$ sudo ln -s ../init.d/setMTU S90setMTU
```

Take care to use a number (90 in my case) that is greater than your network startup.  Say you have a link to your networking called 'S85networking' - in this case you'll wanna use a number higher than 85 so this script runs AFTER the network comes up.  I used S90 in my example.

That should take care of the jumbo frames.  It just pisses me off that the damn GUI doesn't take care of this.  Makes me wonder why even include it as an option if it doesn't work.

---

### Post by graysky on 2009-01-10
Another solution: DISABLE the retarded gm-network manager as described above.

Back up your current /etc/network/interfaces
Replace it with something similar to mine that WORKS:

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
address 192.168.1.2
network 192.168.1.0
netmask 255.255.255.0
broadcast       192.168.1.255
gateway 192.168.1.1
mtu     4000
```

Restart it by restarting gdm (ctrl+alt+backspace) then issuing a $ sudo /etc/init.d/networking restart from the shell.

That should do it!

---

### Post by Yogi291 on 2009-01-14
How would you go about setting it for dhcp?
My eth1 that connects to my cable modem sets the mtu at 576 and now i can't play games.
If i do ifconfig eth0 mtu 1500 it seems to set it, but not really set, cause xbox360 can't go online.

```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
hostname "yaaa"
name WAN Interface
pre-up /sbin/ifconfig $IFACE mtu 1500
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-restore < /etc/iptables.rules

auto eth1
iface eth1 inet static
        address 192.168.192.1
        netmask 255.255.255.0
        broadcast 192.168.192.255
        network 192.168.192.0

```

nics

```
lspci | grep -i ethernet
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)

```

---

### Post by graysky on 2009-01-17
Have you tried what I outlined in my 2nd post?

---

### Post by Yogi291 on 2009-01-17
This is for ubuntu server edition 8.1, so i dont have the network manager installed.
I found the solution on another post.
It looks like the problem only is because of my isp provider (cablevision)

so in this file - /etc/dhcpd3/dhclient.conf
```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu;
```

i removed interface-mtu so that when i make a dhcp request to my modem it doesn't return the isp mtu setting and it automaticly sets it to 1500,

I do appreciate your post because it sent me searching and thinking in the right direction.  Big swoosh and woot for you. :P

---

