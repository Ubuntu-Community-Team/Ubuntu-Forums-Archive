---
title: "command to connect to and disconnect internet"
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by thallasrihari on 2011-05-15
what is the command in the terminal to [COLOR=Lime]_**connect to and disconnect to internet**_[/COLOR]

i have mobile broadband usb modem

---

### Post by coffee412 on 2011-05-15
> **thallasrihari said:**
> what is the command in the terminal to [COLOR=Lime]_**connect to and disconnect to internet**_[/COLOR]

i have mobile broadband usb modem

If Im not mistaken here:

Run the command 'ifconfig' and note the network interface name. Probably something like 'eth0'

Then run this command 'sudo ifconfig eth0 down'

To bring it back up again run the command 'sudo ifconfig up'

That should do it.

coffee :)

---

### Post by thallasrihari on 2011-05-15
is there any way to run it [COLOR=Magenta]_**automatically at startup**_[/COLOR]???

---

### Post by coffee412 on 2011-05-15
Well, I think you can put it in your /etc/rc.d/rc.local file as a command line. I might be wrong on the location of rc.local though as Im in my fedora install right now.

ifconfig eth0 up


I think you would skip the 'sudo' command in the command line. Try and see.

coffee

---

### Post by thallasrihari on 2011-05-15
i will try it

---

### Post by chili555 on 2011-05-15
> **coffee412 said:**
> Well, I think you can put it in your /etc/rc.d/rc.local file as a command line. I might be wrong on the location of rc.local though as Im in my fedora install right now.

ifconfig eth0 up


I think you would skip the 'sudo' command in the command line. Try and see.

coffeeYou are on the right track but not quite correct. Assuming that Network Manager is *NOT* present and running on the computer, please amend /etc/network/interfaces to read:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```The auto eth0 part tells the system to start the interface and get an address by DHCP automagically.

In this case, rc.local is not needed; it's in /etc/rc.local, not rc.d.

---

