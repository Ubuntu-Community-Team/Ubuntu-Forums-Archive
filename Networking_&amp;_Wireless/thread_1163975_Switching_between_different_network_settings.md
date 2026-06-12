---
title: "Switching between different network settings"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by krippa on 2009-05-19
I have a Ubuntu laptop (dell studio xps 16) with built in HSPDA/HSUPA connectivity and I want to be able to have very different network setups based on where I am. Sort of like location-based network settings. Let me explain further by giving three examples that I will want to use often.

**LAN/WLAN client mode**

Connect to any available network and get an IP using DHCP. Basically what ubuntu does out of the box.

**3G shared mode**

Internet connectivity is provided by the built in hsdpa/hsupa card. Single IP available.

I would in this mode like to have my WLAN interface to accept direct connections from other computers using ad-hoc WLAN. Since I only have one IP from the ISP I will also need to start up DHCP and NAT services and configure them to use the WLAN/3G interface.

**LAN shared mode**

Internet/LAN connectivity is provided through the wired LAN interface.

In this mode I want to set up WLAN to accept ad-hoc connections from other computers but I do not want to act as DHCP/NAT provider since the wired network already does this. Thus, I want to somehow bridge the LAN/WLAN interfaces to forward traffic, everything from dhcp requests to HTTP traffic.

First of all, is there some type of program that lets me manage this type of advanced network settings based on defined profiles?

I am almost assuming there is not and that I will have to create multiple config files and create scripts that will rename these config files and reboot the appropriate daemons. Will this be possible?

Then, it would be very interesting if I could somehow trigger these changes automatically based the state of my computer, for example if I connect using 3G. Does anyone know of a way to start a script when a network event occurs , such as for example network connectivity on a certain interface?

Any help greatly apprieciated!

I will post any progress I make here...

---

### Post by krippa on 2009-08-01
I finally got it working and it seems the solution was really simple (at least in Ubuntu 9.04 Jaunty Jackalope). NetworkManager takes care of everything.

All I really had to do was to create a new wireless network by right-clicking the network applet, set whatever security I want (in my case none since the idea is to share with everyone). I then connect by wire or by my 3G connection and it will automatically be shared. If you are running an older version of ubuntu you might have to install dnsmasq-base. Please see the following post:

[http://ubuntuforums.org/showthread.php?t=1000942]("http://ubuntuforums.org/showthread.php?t=1000942")

I also run into trouble where a specific MAC address was required for internet connectivity and found that the easiest way to change the mac address and still use NetworkManager to share your connection is to run use the macchanger application:

[http://www.alobbs.com/macchanger/]("http://www.alobbs.com/macchanger/")

---

