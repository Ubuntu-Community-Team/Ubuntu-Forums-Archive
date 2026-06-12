---
title: "how to disable 'Auto usb0' in NetworkManager Applet"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by davidmaxwaterman on 2009-11-17
Hi,

I have a device that I use connected via usb that I want to ssh into.

I want the interface to be have a fixed IP. By default, it seems to have an 'Auto usb0' interface with dhcp enabled. I want to disable dhcp and manually set the IP address and netmask, so that when the device is connected the interface is brought up with those values.

However, if I do that, when I connect the device, I get two 'Auto usb0' devices, one of which is still trying to do dhcp, and the other is how I want it.

If I try to delete the dhcp one, I get a 'Message did not receive a reply (timeout by message bus)', and I get yet another 'Auto usb0' listed, so now there's three. Restarting the applet again shows two.

How to make it do what I want?

Thanks,

Max.

Ubuntu 9.04/NetworkManager Applet 0.7.0.100

---

### Post by nixscripter on 2009-11-18
I believe that network manager applet looks in **/etc/network/interfaces** for its information. What does that file look like?

---

### Post by davidmaxwaterman on 2009-11-20
> **nixscripter said:**
> I believe that network manager applet looks in **/etc/network/interfaces** for its information. What does that file look like?

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

Nothing relevant, I guess.

---

### Post by nixscripter on 2009-11-20
One thing I could suggest is set up the interface via scripts by adding this syntax to the file:

```

# Set up an interface which will not be allocated an IP address by
# ifupdown but will be configured through external programs. This
# can be useful to setup interfaces configured through other programs,
# like, for example, PPPOE scripts.
#
auto usb0
iface usb0 inet manual
      up ifconfig $IFACE 0.0.0.0 up
      up /usr/local/bin/myconfigscript
      down ifconfig $IFACE down

```

This way, you could have the script set the values.

Or, if there is one configuration and you know it in advance, you can:

```

# An example setup: (broadcast and gateway are optional)
#
auto usb0
iface usb0 inet static
    address 192.168.0.42
    network 192.168.0.0
    netmask 255.255.255.0
    broadcast 192.168.0.255
    gateway 192.168.0.1


```

You might also look at raising the interface automatically here:

[http://ubuntuforums.org/showthread.php?t=2038](http://ubuntuforums.org/showthread.php?t=2038)

---

### Post by davidmaxwaterman on 2009-11-21
Thanks for the tips. I was really hoping to get the GUI to work, but it seems incapable of such. Would you agree?

---

### Post by t0mppa on 2009-11-21
@nixscripter: Network Manager actually ignores what's written in /etc/network/interfaces. It reads its configuration from the gconf, i.e., xml files stored in the users home directory. Quite an unusual way of handling configuration on Linux, but that's besides the point. Bottom line is that you can use either Network Manager or the interfaces file, but not both.

@davidmaxwaterman: While configuring your network manually with the interfaces file and managing it through the command line interface might seem natural to some advanced users, the GUIs were built, so that being a Linux user didn't necessarily mean using everything through command line.

Network Manager does behave in very odd ways from time to time and I have yet to see any real answers as to how to get around problems like the one you're facing. However, there are other programs for the same task, you should try WICD or WifiRadar out, both offer a GUI as well and often work where Network Manager doesn't.

---

### Post by davidmaxwaterman on 2009-11-22
> **t0mppa said:**
> @nixscripter: Network Manager actually ignores what's written in /etc/network/interfaces. It reads its configuration from the gconf, i.e., xml files stored in the users home directory. Quite an unusual way of handling configuration on Linux, but that's besides the point. Bottom line is that you can use either Network Manager or the interfaces file, but not both.


Is there a way to disable network manager, since it's so broken with anything but the simplest of setups?

I wonder if the version with 9.10 is any better. Do you know?

> 
@davidmaxwaterman: While configuring your network manually with the interfaces file and managing it through the command line interface might seem natural to some advanced users, the GUIs were built, so that being a Linux user didn't necessarily mean using everything through command line.


Obviously. I'm not sure what your point is here.

> 
Network Manager does behave in very odd ways from time to time and I have yet to see any real answers as to how to get around problems like the one you're facing. However, there are other programs for the same task, you should try WICD or WifiRadar out, both offer a GUI as well and often work where Network Manager doesn't.

OK, I'll give them a try, even though they seem to be mostly about wireless networking while I'm talking about a wired connection (USB).

Thanks,

Max.

---

### Post by gradinaruvasile on 2009-11-22
Well in order to make Network Manager to work u have to have in the /etc/network/interfaces ONLY THIS:

auto lo
iface lo inet loopback

The other devices then will be managed by network manager.
Also, you can change the "Auto whatever" options on the networking (i dont have it installed so i cant say the name for sure) tab and assign manually the desired addresses. Do not remove it, only change its settings.

Might try wicd though. I like it more, but it has no support for usb modems.

---

### Post by gradinaruvasile on 2009-11-22
Also here you can get a newer version of network manager:

[https://launchpad.net/~network-manager/+archive/ppa?field.series_filter=jaunty](https://launchpad.net/~network-manager/+archive/ppa?field.series_filter=jaunty)

---

### Post by davidmaxwaterman on 2009-11-22
> **gradinaruvasile said:**
> Well in order to make Network Manager to work u have to have in the /etc/network/interfaces ONLY THIS:

auto lo
iface lo inet loopback


oh, that's worth a try.

> **gradinaruvasile said:**
> 
The other devices then will be managed by network manager.
Also, you can change the "Auto whatever" options on the networking


yes, this is what i've been trying and doesn't work, but perhaps because of the above file.

> **gradinaruvasile said:**
> 
 (i dont have it installed so i cant say the name for sure) tab and assign manually the desired addresses. Do not remove it, only change its settings.

Might try wicd though. I like it more, but it has no support for usb modems.

I don't care about usb modems, just usb networking - ie tcp/ip over usb.

thanks,

max.

---

