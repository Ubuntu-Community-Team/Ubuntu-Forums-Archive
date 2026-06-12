---
title: "static addresses and DNS nameservers?"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by wkearney99 on 2010-03-05
I've got a karmic box with two ethernet interfaces using static addressing.  It does not use DHCP at all (nor is there any DHCP available on either of it's network connections).  It does not have a DNS server running on it (nor is any desired).  There are two other DNS servers running on one of the network connections (eth1 in this particular case).  The network-manager package is NOT installed (nor is it desired).  

When it boots there's no nameserver records configured.  When I try bringing up network-admin the location isn't set nor are there any nameserver entries.  I can add them manually but they get lost when the machine reboots.  WTF?

So where should the nameservers be configured on this machine?

I've searched a number of threads and nothing directly addresses my particular setup.  

And why doesn't network-admin have a way to save and edit a default location profile?  Is there a way to set one of them as a default; brought up at boot?

Thanks!

---

### Post by Barriehie on 2010-03-05
When you add them manually you're putting them in /etc/resolv.conf right?

---

### Post by wkearney99 on 2010-03-05
> **Barriehie said:**
> When you add them manually you're putting them in /etc/resolv.conf right?  I have now.  After removing the resolvconf package.  I'm sure that mess is useful to someone but, ugh, does it cause more trouble that it's worth with static interfaces.  And complete removal actually doesn't.  It left behind the warning in resolv.conf about not editing.  Which is no longer true without resolvconf installed.    So yes, I ripped out resolvconf and network-manager and then made direct edits to the /etc/network/interfaces and /etc/resolv.conf files.  Now the setup seems to be functioning properly.

---

### Post by Barriehie on 2010-03-05
Those 2 files should do it!  Glad you got it.

---

