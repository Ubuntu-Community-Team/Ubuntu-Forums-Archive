---
title: "wireless not working"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by hannah2312 on 2009-07-27
Hi all =)

My brother has an acer aspire one netbook, as do I. We both installed Ubuntu Netbook remix 9.04 a few months ago. His wireless has suddenly stopped working and he doesn't know how he's done it or how to sort it out. It isn't a problem with the OS disk as far as I know because mine connects to the internet fine. There is no option to search for wireless networks and when I type all the details of the network in it connects but there is no signal. sorry thats not very helpful info but all I have. 
Thankyou in advance everyone =)

---

### Post by Newfoundlander on 2009-07-27
There seems to be something breaking Ubuntu 9.04 systems relating to DSN.

Open your terminal and try the following:

```
ping www.google.com
```

My guess is you'll get an error saying "ping: unknown host www.google.com"

Next try:

```
ping 74.125.79.99
```

If the first one does not work but the second one does then you are in the same boat as me and the growing number of users posting here.

---

### Post by hannah2312 on 2009-07-28
ok I tried that and it did what you said it would. We've decided to reinstall ubuntu. thankyou anyway =)

*edit* I tried reinstalling and the wireless still doesn't work. Can anyone recommend a different version of ubuntu please? thankyou

---

