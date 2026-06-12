---
title: "Avahi services disappear from network?"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by PartisanEntity on 2011-03-09
Hi all,

I am sharing some folders from my Ubuntu machine, using Netatalk and Avahi, over my network.

I access these folders from my Mac using the AFP protocol.

When all is well, my Ubuntu folders show up in Finder on the Mac and I can connect to them.

But at random intervals, the Ubuntu folders will disappear. 

Sometimes they reappear a short while later.

At other times, they wont appear until I go to my Ubuntu machine, and re-save (even if i don't change anything) the file:

/etc/avahi/services/afpd.service

Anyone with similar experiences, or any ideas what could be the problem?

---

### Post by PartisanEntity on 2011-03-13
Bump, anyone?

I noticed that Avahi services will disappear from the network very often when I am copying large amounts from my iMac to my Ubuntu machine.

Anyone with similar experiences?

---

### Post by PartisanEntity on 2011-04-03
Bumping this again. If anyone has any ideas please do let me know. I still have not been able to find any helpful info concerning the issue here.

---

### Post by DirtyNerd on 2011-09-20
Bump exact same problem gonna try edit the avahi upstart to, after a 60 sec delay move the afpd.service file then move it back. see if that works then ill come up with a better solution unless you have had any luck??

---

### Post by tbotcotw on 2012-09-20
Exactly one year later, I have the solution: you need to allow mDNS traffic on your firewall. Traffic to 224.0.0.251, UDP port 5353 must be accepted.

---

