---
title: "I only want static IP. Should I remove network manager?"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by yelvington on 2010-12-04
I have a static-address problem.

I have a desktop computer that primarily works as a server in my home. It has a recent install of Maverick server edition, upgraded by adding the desktop packages. 

Since it's a server, I need a static IP address, but when I run the network manager (system->preferences->network connections) the dialog box won't let me create a static configuration, as I easily can do with my laptop. 

I edited /etc/interfaces and added:


# The primary network interface
auto eth0
iface eth0 inet static
# no dhcp
address 192.168.0.33
netmask 255.255.255.0
gateway 192.168.0.1

Restart the network and all is fine.

Several days later my web and mail services fail and my family is hollering. I discover the server's address has been changed to one provided by DHCP. I kill network-manager, restart networking, and it all comes back to life.

I want this to stick. So my questions: Is it safe to simply uninstall network-manager? Will that make the DHCP problem go away?

---

### Post by karthick87 on 2010-12-04
Just remove the network-manager from the startup applications.

---

### Post by amsterdamharu on 2010-12-04
192.168.0.33 That is the address your router gave you.

Open up your router settings (usually [http://192.168.0.1](http://192.168.0.1) in a browser usually uses user admin and password is password). Then in my router under dhcp there is a choice to set the IP adress to static which means it won't expire.

Now you can keep using DHCP but the router won't give you a new IP address when it expires.

---

### Post by chili555 on 2010-12-04
> Is it safe to simply uninstall network-manager?Yes.> Will that make the DHCP problem go away?Yes, although it may take a reboot.

Please post back if it doesn't go smoothly.

---

### Post by gradinaruvasile on 2010-12-04
> **yelvington said:**
> I have a static-address problem.

I have a desktop computer that primarily works as a server in my home. It has a recent install of Maverick server edition, upgraded by adding the desktop packages. 

Since it's a server, I need a static IP address, but when I run the network manager (system->preferences->network connections) the dialog box won't let me create a static configuration, as I easily can do with my laptop. 

I edited /etc/interfaces and added:


# The primary network interface
auto eth0
iface eth0 inet static
# no dhcp
address 192.168.0.33
netmask 255.255.255.0
gateway 192.168.0.1

Restart the network and all is fine.

Several days later my web and mail services fail and my family is hollering. I discover the server's address has been changed to one provided by DHCP. I kill network-manager, restart networking, and it all comes back to life.

I want this to stick. So my questions: Is it safe to simply uninstall network-manager? Will that make the DHCP problem go away?

Short answer: yes.

Long answer: there is absolutely no need for network manager if you have a fixed ip machine and you know how to configure it.  I dont have it installed (never did) on any of the computers that use fixed ips and have 0 problems.
I strongly suggest uninstalling network-manager (and all related packages) if you do not need it.

---

### Post by yelvington on 2010-12-04
apt-get remove network-manager
got rid of the packages. Rebooted and kept my assigned static address so I'm marking this "solved."

Thanks.

---

### Post by jcmtnez on 2011-01-16
I respectfully disagree with...

> there is absolutely no need for network manager 

You may need the network manager later to connect to a VPN.

I uninstalled mine and the DHCP problem went away but today I needed to connect to my office using PPTP and I have done everything and I can't. If you try to reinstall network manager, chances are that it won't work. After a day of installing and reinstalling and reading every blog I'm almost ready to reinstall Ubuntu.

I think that...

> Just remove the network-manager from the startup applications

...is safer.

---

