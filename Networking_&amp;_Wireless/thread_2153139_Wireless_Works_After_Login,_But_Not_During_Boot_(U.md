---
title: "Wireless Works After Login, But Not During Boot (Useful to SSH Admin w/o Logging In)"
date: 2013-06-10
forum: Networking &amp; Wireless
---

### Post by galvaros on 2013-06-10
Dear Ubuntu Community

My wireless connection is working only after I log in and issue

> sudo /etc/init.d/networking restart

(i.e. the computer then gets an IP for wlan0 and I can ping e.g. [www.google.com]("http://www.google.com"))

However, during boot, I get the message

- Waiting for network configuration
- Waiting an additional 60 seconds for network configuration

For a while, getting a network connection with wlan0 worked during boot as well. Since then, I upgraded and installed OpenSSH.

I'm not sure how/what I broke for this to happen, and I don't have an idea where to look right now.

The forum is full of posts reg. "Waiting for network configuration", but mostly with people having a bad configuration in /etc/network/interfaces (or just wanting to get rid of the error message during boot). My interfaces file is identical to when it worked. Did I break another file somewhere else I'm not aware of?

I hope somebody can point me in the right direction! :)

Thank you!
G

P.S. I'm running Ubuntu Server 12, installed from CD with downloading also happening via wireless during install.

---

### Post by galvaros on 2013-06-10
As a side note, if I use Ethernet (eth0) instead of wlan0 in /etc/network/interfaces, then the computer connects during boot, before login.  I'm puzzled why it can't do the same using wlan0 (even though the configuration for wlan0 seems OK as after login /etc/init.d/networking restart will actually connect and get the machine an ip)  Thanks again guys :)

---

