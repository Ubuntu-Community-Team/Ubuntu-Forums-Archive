---
title: "[SOLVED] Static network address from CLI"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by andreasis on 2008-12-15
I have been trying to figure out this mystery by looking at dozens of other threads and the debian documentation, but I have had no luck.

On a fresh install of Ubuntu (Hardy) I make and install the rt2570 (wireless) driver from the rt2x00 website.  I blacklist the original driver that comes with Hardy (rt2500usb).

I absolutely hate gnome network manager, have used wicd, but I would still prefer to get the CLI tools working for greater stability.

I got this far: I can connect to the internet by:

```

ifconfig rausb0 down
iwconfig essid NAME
iwconfig key 128BITWEPKEY
iwconfig mode Managed
ifconfig rausb0 up
sudo dhclient
```

after which it binds to the ip address 10.0.1.3 on the local network.

However, for some reason, by putting the following lines into /etc/network/interfaces doesn't get me anywhere.... unless I do sudo dhclient again, but that's not using the static ip that i want.

```
auto rausb0
iface rausb0 inet static
     address 10.0.1.3
     netmask 255.255.255.0
     gateway 10.0.1.1
     wireless-essid NAME
     wireless-key wirelesskey
     wireless-rate 54M
     wireless-mode Managed
```

Your help is GREATLY appreciated.

---

### Post by andreasis on 2008-12-15
So I revisited the WEP section in [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188) and it all seems to work now.... >_<*

---

### Post by andreasis on 2008-12-16
Setting up a network from the CLI seems to be very sensitive to the order of the commands... which may possibly make sense to many linux users out there.  For those that have struggled as I have, this is the magical order that works:

In my rc.local file, I put:

ifconfig <wired adapter> down
ifconfig <wireless adapter> down
dhclient -r <wireless adapter>
ifconfig <wireless adapter> ##.##.##.## netmask 255.##.##.0 up
route add default gw ##.##.##.##
iwconfig <wireless adapter> essid "NAME"
iwconfig <wireless adapter> key keeeeeeeeeeeeeeeeeeey
iwconfig <wireless adapter> mode Managed
iwconfig <wireless adapter> rate 54M

I hope this helps someone else

---

