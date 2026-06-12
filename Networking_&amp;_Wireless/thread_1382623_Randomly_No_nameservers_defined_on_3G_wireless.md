---
title: "Randomly: No nameservers defined on 3G wireless"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by josamoto on 2010-01-16
I have a Huawei E220 3G modem and I'm using Ubuntu 9.10. The modem picks up on USB, and the connection works, sort of. With random times, I can't get on the internet, and when running:

```
mtr -n -c3 -r 4.4.4.4
```

it tells me:
> Could not get fd's flags: Bad file descriptor
No nameservers defined

Network Manager Applet 0.7.996 is reporting my wireless connected, and applications like Skype is working perfectly. I just can't browse.

When I restart a couple of times, and my internet browsing capability starts working eventually at times. The behavior is very random.

It appears that when I fiddle with USB devices, like unplugging my external hard drive, and plugging the USB modem in and out, restarting, it helps.

Also, when plugging in my USB 3G modem, an icon pops up on the desktop, mounting the USB device as a USB flash drive. The device has on-board memory, but can I disable this / prevent it from mounting?

I also disabled IPv6 by setting:
```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable= 1 quiet splash"

```in /etc/default/grub
as per suggestion from some forum posts here on Ubuntu forms.

What I also did was to "hard code" DNS by adding:
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;
```
to /etc/dhcp3/dhclient.conf

This was also suggested on a forum thread here.

---

### Post by josamoto on 2010-01-17
Is it at all possible to refresh the DNS server list or something like that, and put that in a startup script or something?

Skype works, updates work, and even my weather widget updates...it's just browsing that's broken.

---

### Post by JDahl on 2010-01-17
I have the exact same problem,  and also try various
suggestions to fix it, for example hardcoding 
nameservers in the mobile broadband configuration
from the network manager.

Maybe one should file a bug report about it.

---

### Post by josamoto on 2010-01-17
Man, this is frustrating, it appears as if Ubuntu is initializing DNS before the wireless is being initialized, and then ends up with no valid name servers.

Just a silly guess.

---

### Post by alexfish on 2010-01-17
hi

have you tried setting IPv4 setting to Automatic (ppp) Address only

---

### Post by josamoto on 2010-01-17
> **alexfish said:**
> hi

have you tried setting IPv4 setting to Automatic (ppp) Address only

That sounds like a good idea, I'm willing to give anything a try. Do you mind helping out on how to do that?

---

