---
title: "e1000 fails on boot"
date: 2006-03-25
forum: Networking &amp; Wireless
---

### Post by BlackWoxs on 2006-03-25
I have a DeLL Dimension 9150 - the e1000 network card did not work on install, however after build and install from the intel source files the e1000 has worked perfectly. Whenever I have done a kernel upgrade I have simply rebuilt the e1000 and installed it for the new kernel. 

Following the last upgrade to 2.6.12-10-686 after reboot e1000 loads but the eth0 does not come up. If I remove the module, insert the new module via a specific path and bring eth0 up its seems fine. The steps I have to follow manually are:

sudo rmmod e1000
sudo insmod /lib/modules/2.6.12-10-686/kernel/drivers/net/e1000/e1000.ko
sudo ifconfig eth0 up

then configure the card to add a DNS.

/etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
    network 192.168.0.0
    broadcast 192.168.0.255

Any help so that this occurs automatically (as it has been) would be appreciated

---

### Post by mips on 2006-03-25
Do a search for "e1000" or something of the sorts as I'm sure others have also reported this problem. Maybe someone found a solution.

---

### Post by chenel on 2006-03-27
I have exactly the same problem, although the procedure I discovered is a little less complicated:

```

sudo modprobe -r e1000
sudo modprobe e1000
sudo /etc/init.d/networking restart

```

and then all is well.  If you find a solution please post it here though!  Thanks!

---

### Post by BlackWoxs on 2006-03-28
Agreed a much simpler solution to the problem - this also works fine for me - thanks.

Now we just need a solution to the problem, anyone with any ideas (I have searched through e1000 postings but to no avail)?

---

### Post by chenel on 2006-04-15
Well, I don't have a solution.  But I managed to at least create a script that automates the hack...

1. Switch to root user:
```
 sudo -s 
```

2. Create /etc/init.d/fixe1000:
```

#!/bin/sh

case "$1" in
        start)
                modprobe -r e1000
                modprobe e1000
                /etc/init.d/networking restart
                ;;

        stop)
                ;;

        restart|reload|force-reload)
                ;;

        *)
esac

```

2. Make it executable:
```
 chmod +x /etc/init.d/fixe1000
```

3. Add it to the default runlevels:
```
 update-rc.d fixe1000 defaults
```

Now when you boot it should pull and re-insert the module automatically.  If you use DHCP, it might take a minute or two to finish refreshing that and give you an IP address (at least it does for me), but otherwise things should work.

Best of wishes.  [And please post if you find a better solution!]

-Jeremy

---

### Post by vfxdude2 on 2006-04-23
Uhhh... anyone found a better solution yet?

I having this exact same problem.  I even re-compiled the e1000 driver and updated to the latest one posted on Intel's site.

Does the same thing -- won't load during boot, but I can manually unload/re-load the driver and it works fine.

Anyone know why this is happening?

-Andrew

---

