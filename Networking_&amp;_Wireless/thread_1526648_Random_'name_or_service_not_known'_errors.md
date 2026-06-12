---
title: "Random 'name or service not known' errors"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by markoid8 on 2010-07-08
I've been a Ubuntu user for 3 years and I rarely need to post questions but I have been pulling my hair out on this one and I really need some help.

Let me set the scene:
I have a fairly new laptop which is running Ubuntu Server 10.04. It has GDM on it [as I use it as an app server], and it serves LAMP/SMB/CIFS/FTP/SSH and a whole bunch of other protocols.

I have dual interfaces, wlan0 [wifi with internet] and eth0 [my in-home local only wired network].

Pretty much at "random", like every other day or so, no program on my server can resolve a hostname. They either say the server could not be found, or 'name or service not known'.
The only way to resolve the problem is to reconnect to my wireless network using Network Manager. I still have a functioning connection [I can accept incoming connections], but no hostname lookups.

I have looked at /etc/resolv.conf and there are 3 entries:
8.8.8.8
4.4.4.4
4.2.2.2

They were all added by Network manager and 2 are from Google, one from Verison. [My ISP has an awful DNS]
I use the same configuration on my other computers and I haven't had any problems with them.

Thanks in advance

---

### Post by markoid8 on 2010-07-22
I seem to have fixed the problem myself.

It was Avahi that was causing the problem.

I had to edit a line in /etc/avahi/avahi-daemon.conf to read:

```
domain-name=.alocal
```

---

