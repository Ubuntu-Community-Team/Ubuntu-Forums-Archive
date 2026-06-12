---
title: "How do I disable IPv6 in Ubuntu 9.04?"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by Rytron on 2009-04-23
Hi.
How do I disable IPv6 in Ubuntu 9.04?

I used these methods before in previous versions of Ubuntu but they dont work in Ubuntu 9.04.

METHOD 1:
gksudo gedit /etc/modprobe.d/aliases
Change
alias net-pf-10 ipv6
to
alias net-pf-10 off
Reboot.
Validate with
lsmod | grep v6
Should return nothing

METHOD 2:
sudo gedit /etc/modprobe.d/bad_list/
Add alias net-pf-10 off to the file
Save and Quit
Reboot Your Machine
To confirm Ipv6 is Disabled
Type ip a | grep inet6
no output = ipv6 is disabled

---

### Post by kerry_s on 2009-04-23
i used the /etc/modprobe.d/blacklist in debian.

blacklist net-pf-10
blacklist ipv6

does ubuntu not have that anymore?

---

### Post by kaixi on 2009-04-23
> **kerry_s said:**
> i used the /etc/modprobe.d/blacklist in debian.

blacklist net-pf-10
blacklist ipv6

does ubuntu not have that anymore?

I think it's /etc/modprobe.d/blacklist.conf now. :)

---

### Post by kerry_s on 2009-04-23
> **kaixi said:**
> I think it's /etc/modprobe.d/blacklist.conf now. :)

:lolflag: i would have looked but that computers down right now, i knew it was blacklist something. :lolflag:

---

### Post by Claus7 on 2009-04-23
Hello,

from intrepid and on someone cannot disable so easy ipv6. Just take a look at this thread(post):
[http://ubuntuforums.org/showpost.php?p=7087946&postcount=42](http://ubuntuforums.org/showpost.php?p=7087946&postcount=42)

Regards!

---

### Post by Rytron on 2009-04-24
Its okay. I though that IPv6 being on that it was slowing down my internet connection. However it was perhaps just a coincidence yesterday. My internet connection is now running quite fast so I'll just leave IPv6 as it is. Thanks anyway guys. Cheers.

---

