---
title: "Switching from static ip ethernet and wireless to dhcp wireless?"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by vayu on 2006-01-09
I need to run my laptop in three network environments.  A static IP cabled ethernet, a static IP WPA wireless and internet hotspots which I assume are DHCP.

I have the first two working well but I have to go into /etc/network/interfaces and comment out eth0 or eth1 whichever I'm not using.  Is that normal?

They could use the same ip address but on windows it only worked if they were different so that's what I did here.  (to get the wireless going, I manually run wpa_supplicant when I want to do that)

The third thing I have never tried, but I would like to be able to go to internet hotspots.  I don't know anything about how to do set up DHCP, let alone how to switch back and forth from my other two scenarios smoothly.

How do I set up DHCP? Is it all done in /etc/network/interfaces? 
How do I switch from one to the other?

Here is my /etc/network/interfaces:
```

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
        map eth1

# The primary network interface
#iface eth0 inet static
#       address 10.0.0.27
#       netmask 255.255.255.0
#       network 10.0.0.0
#       broadcast 10.0.0.255
#       gateway 10.0.0.100
#       # dns-* options are implemented by the resolvconf package, if installed
#       dns-nameservers x.x.x.x
#       dns-nameservers x.x.x.x x.x.x.x

#auto eth0

iface eth1 inet static
        address 10.0.0.57
        netmask 255.255.255.0
        network 10.0.0.0
        broadcast 10.0.0.255
        gateway 10.0.0.100
        dns-nameservers x.x.x.x x.x.x.x
        wireless-essid myssid
auto eth1

```

---

### Post by Lambert on 2006-01-09
One thing you can do is create virtual interfaces. so instead of lines like these

iface eth0 inet static
xxx
xxx

iface eth1 inet static
xxx
xxx

you would call them something like

iface work inet static
xxx
xxx

iface home inet static
xxx
xxx

iface hotspot inet dhcp

don't use any auto stanzas such as auto eth0.

Now you have to bring up the interface through the command line like this. And you don't have to keep opening the file and commenting out lines.

sudo ifconfig eth0=work up
or 
sudo ifconfig eth1=work up
etc...

To automate this you can look into some scripts I've seen floating around here on the forums such as [this one]("http://doc.gwos.org/index.php/WLAN_Autodetect")  or look into something called guessnet but I'm no help in these areas as I have not used these.

---

### Post by vayu on 2006-01-11
Thanks much!  This is just what I was looking for.  I had seen that other post but was totally confused by it.  After reading yours, now I understand the other one too. :D

---

