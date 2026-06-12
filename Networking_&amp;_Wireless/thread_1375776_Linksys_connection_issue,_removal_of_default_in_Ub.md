---
title: "Linksys connection issue, removal of default in Ubuntu"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by pifactory on 2010-01-08
I'm having problems connecting my Eeepc netbook (celeron processor) running 9.1 netbook remix to my Linksys wrt54gl wireless router. The machine can see the wireless network, but won't engage.

I recall some weeks ago a useful post that said words to the effect that there was a default setting in Ubuntu hardy onwards that was getting in the way. A fairly simple command line was given to remove the setting.

I did this on another Eeepc machine (atom processor) which cleared the issue.

I cannot now find this v helpful post.

Anyone out there who can point to either the original post or the relevant default and the command req'd to nullify it?

Thanks.

PS As I see this Linksys thing is a real issue for lots of ubuntu users this would be a great solution to emphasize. It would be real nice if Linksys just solved the problem of course, or the next distro of ubuntu fixed the default...

best wishes

DW

---

### Post by Iowan on 2010-01-08
Did the suggestion have to do with blacklisting modules, or bypassing IPv6?

---

### Post by pifactory on 2010-01-08
Yes, bypassing IPv6...

Thanks

Do you know the commands required?

---

### Post by Iowan on 2010-01-08
> **pifactory said:**
> Do you know the commands required?Unfortunately, no... but now you (we?) have a phrase to search for. I need to update the "disable IPV6" link in my signature.

---

### Post by pifactory on 2010-01-09
Thanks.

I found this in my Ubuntu helpfile:

In terminal...

gksudo gedit/etc/modprobe.d/aliases

find alias net-pf-10 ipv6

change it to read alias net-pf-10 off

reboot



I did this, and after a v long delay the machine showed it was connected to my wireless network. But Firefox couldn't find the url (google for test). I'd also turned ipv6 off in firefox.

So, one step forward, two backwards.

There's lots on the forum about changing the firmware on the linksys router... but it looks v daunting.

Thanks again for your help.

---

### Post by Iowan on 2010-01-09
[Here]("http://ubuntuforums.org/showpost.php?p=8637126&postcount=2") is another method to look over.

---

### Post by pifactory on 2010-01-10
Thanks again.

I'm following this thread at the moment... trying to load madwifi drivers onto the Ubuntu machine:

[http://art.ubuntuforums.org/showthread.php?p=8642012#post8642012](http://art.ubuntuforums.org/showthread.php?p=8642012#post8642012)

---

