---
title: "avahi-daemon and internet connection"
date: 2013-08-13
forum: Networking &amp; Wireless
---

### Post by Bacon77 on 2013-08-13
The problem:
I have Ubuntu working within Windows 7, not true dual boot but it appears that way.
On the windows side I can connect to the internet and on the Ubuntu side I am able to also connect to a network through wifi and Ethernet, but cannot connect with a printer or any website.

This all started when I was making changes with avahi-daemon

I ran this command
sudo update-rc.d -f avahi-daemon remove

When I couldn't connect with the internet I attempted to undo this by 
sudo update-rc.d avahi-daemon defaults

It appeared to do its job but then it gave "warning missing LSB information... see wiki.debian.org/LSBInitScripts". I still cannot connect to a website or printer on the Ubuntu side.

Is the missing LSB information related to my current problem or is there another reason?

---

