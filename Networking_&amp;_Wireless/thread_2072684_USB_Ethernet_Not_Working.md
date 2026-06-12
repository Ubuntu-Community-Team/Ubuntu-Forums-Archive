---
title: "USB Ethernet Not Working"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by breimer273 on 2012-10-18
Hey guys, I read an old post where someone had the same problem as me but the links in it were broken, so I thought I'd ask again to get some up-to-date help.

My situation is that I am using an old laptop running Ubuntu Server 12.04 and I want to use a USB ethernet card and the integrated ethernet. I am going to be using this server as a firewall/IDS. Right now I just have the laptop sitting as another computer on my current network, so only the integrated NIC is actually configured and it is currently configured to use DHCP (i will change this once I am all setup and ready to go). So my problem is that I can't get my usb ethernet adapter to be recognized as an ethernet interface. I am using the Dlink DUB-E100 which I have heard good reviews about especially related to its compatibility with Ubuntu server. Here is what I get in lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2001:1a02 D-Link Corp. 

```
And that last device is my ethernet. Here is my /etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto
#secondary interface
auto eth1
iface eth1 inet dhcp
iface eth1 inet6 auto

```

I also do not currently have a network attached to the interface, I can change that if I need to. My interface just does not show up in ifconfig. And maybe this is right? I don't know.

---

### Post by chili555 on 2012-10-18
It will not show up in ifconfig if no driver has claimed it. Let's try a highly experimental process and see if we can get it going. Remove the device.

In a terminal, do:```

sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="2001", ATTR{idProduct}=="1a02", RUN+="/sbin/modprobe -qba asix"
```Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```

install asix /sbin/modprobe --ignore-install asix $CMDLINE_OPTS; /bin/echo "2001 1a02" > /sys/bus/usb/drivers/asix/new_id
```
Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe asix
```We look forward to your report.

---

### Post by breimer273 on 2012-10-18
Thanks for the reply, still not getting anything to show up in ifconfig. even switched over to using that interface for the network and it still wasn't giving me anything. I feel like I'm missing something really simple here...

---

### Post by chili555 on 2012-10-18
Any clues here?```
sudo modprobe asix
dmesg | grep asix
```Please double-check:```
cat /etc/udev/rules.d/network_drivers.rules
cat /etc/modprobe.d/network_drivers.conf
```

---

### Post by breimer273 on 2012-10-18
ouput of
```

[47582.344101] usbcore: registered new interface driver asix

```

```

cat /etc/udev/rules.d/network_drivers.rules
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="2001", ATTR{idProduct}=="1a02", RUN+="/sbin/modprobe -qba asix"

```

```

cat /etc/modprobe.d/network_drivers.conf
install asix /sbin/modprobe --ignore-install asix $CMDLINE_OPTS; /bin/echo "2001 1a02" > /sys/bus/usb/drivers/asix/new_id

```

---

### Post by chili555 on 2012-10-18
I told you it was experimental! Not all experiments work. You might try this procedure and we'd have to experimentally (!!) hack the C code. [http://plugable.com/2010/10/18/howto-asix-88178-usb-ethernet-adapter-on-ubuntu-10-10-linux/](http://plugable.com/2010/10/18/howto-asix-88178-usb-ethernet-adapter-on-ubuntu-10-10-linux/)

You could install 12.10 and be done:> $ modinfo asix
filename:       /lib/modules/[COLOR="Red"]3.5.0-17-generic[/COLOR]/kernel/drivers/net/usb/asix.ko
license:        GPL
description:    ASIX AX8817X based USB 2.0 Ethernet Devices
version:        22-Dec-2011
author:         David Hollis
srcversion:     0889AC645D9EA92D3DE4C5B
<snip>
alias:          usb:v[COLOR="Red"]2001[/COLOR]p[COLOR="Red"]1A02[/COLOR]d*dc*dsc*dp*ic*isc*ip*
<snip>
depends:        usbnet
intree:         Y
vermagic:       3.5.0-17-generic SMP mod_unload modversions 686 I will be happy to help in any event.

---

### Post by breimer273 on 2012-10-18
Yea, I get that. I just feel like this should just work out of the box. I have heard other people use this interface with ubuntu server and it worked out of the box. I guess thats the beauty of open source software!

---

### Post by breimer273 on 2012-10-18
Is it possible to upgrade to 12.10 without having to reimage the entire computer and redo all of my settings? If you think that 12.10 would be the best solution to this problem.

---

### Post by chili555 on 2012-10-18
> **breimer273 said:**
> Yea, I get that. I just feel like this should just work out of the box. I have heard other people use this interface with ubuntu server and it worked out of the box. I guess thats the beauty of open source software!Your device is covered by *asix* in 12.10 and not in 12.04. Have you an objection to upgrading?

---

### Post by breimer273 on 2012-10-18
nope, other than I really don't want to have to reconfigure all my stuff if I don't have to. It's really not that much. So if the only way to upgrade is to download the iso and do a fresh install well then I guess thats what I'll do.

BTW: Thanks for all the help and the patience.

---

### Post by chili555 on 2012-10-18
> **breimer273 said:**
> Is it possible to upgrade to 12.10 without having to reimage the entire computer and redo all of my settings? If you think that 12.10 would be the best solution to this problem.Yes, indeed. In a day or so, Update Manager will offer the upgrade. Click OK and wait for the conclusion. The Ubuntu servers will be clogged so it will take a couple of hours.

I got antsy and did a fresh install in about 15 minutes from a DVD. I use a separate /home partition, so my data was untouched.

---

### Post by breimer273 on 2012-10-18
Sweet. Thanks again for the help, I guess I didn't realize 12.10 had just been released. I'll be back if things don't work but hopefully they will!

---

