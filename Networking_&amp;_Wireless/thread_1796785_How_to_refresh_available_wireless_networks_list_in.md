---
title: "How to refresh available wireless networks list in nm applet?"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by New00Folder on 2011-07-04
Is there a way I can refresh the list of available wireless networks in the network manager applet? It works correctly when I've just booted but doesn't after I resume after suspending. There's just a message like "wireless networks not available".

I can assure you that the wi-fi is not disabled using a button (my laptop doesn't have such a button), "Fn" key combination or in any other way and the network doesn't go down when I need it.;)

---

### Post by chili555 on 2011-07-04
Often, the real cause is that the wireless driver doesn't reload when the computer comes out of suspend/hibernate/cryo-freeze. You can try to simply reload the driver in a terminal:```
sudo rmmod <driver>
sudo modprobe <driver>
```Find out the driver in:```
sudo lshw -C network
```Here is a snip from my machine:```
description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       logical name: wlan0
       version: 02
       configuration: broadcast=yes driver=[COLOR="Red"]iwl3945[/COLOR] driverversion=2.6.38-8-generic firmware=15.32.2.9 ip=192.168.1.111 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:edf00000-edf00fff

```In some cases, but not all, it helps to write a little file to ask the system to reload the driver:```
sudo gedit /etc/pm/config.d/config
```Add one line:
```
SUSPEND_MODULES="iwl3945"
```Proofread carefully, save and close gedit. It may take a reboot in order to restart all the dependent systems. Of course, substitute your driver here.

Post back so the searchers will learn from your experience. If you get stuck, post back.

---

### Post by New00Folder on 2011-07-05
Well I've tried the commands.

rmmod deletes the wireless networks part from the nm-applet.
modprobe was probably supposed to bring it back, but it didn't.

I've now created the file /etc/pm/config.d/config.
Let's see how that works out.

PS.

There's another [new thread]("http://ubuntuforums.org/showthread.php?t=1427177") about the same thing.

---

### Post by New00Folder on 2011-07-06
Yeah, creating the file did sort out the problem.
Thanks a lot.

---

### Post by chili555 on 2011-07-06
Glad it's working. Please use the thread tools at the top to Mark Solved. This will help the searchers.

---

### Post by Iowan on 2011-07-06
> **chili555 said:**
> ...Please use the thread tools at the top to Mark Solved. This will help the searchers.Got that for you... :)

---

### Post by New00Folder on 2011-07-07
> **Iowan said:**
> Got that for you... :)

Thanks.

---

