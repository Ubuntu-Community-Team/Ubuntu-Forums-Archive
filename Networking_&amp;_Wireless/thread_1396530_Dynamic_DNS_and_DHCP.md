---
title: "Dynamic DNS and DHCP"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by dunkirk on 2010-02-02
I've recently switched my firewall / NAT box to Ubuntu (from Gentoo, for the record), and I saw a little hiccup in my logs. The problem was that the bind user was not able to create or update journal files that bind needed to maintain for the dynamic DNS function. I surmised that this was due to apparmor, and, sure enough, /etc/apparmor.d/usr.bin.named showed that the bind user was not able to do anything in /etc/bind, regardless of permissions on that directory.

I found an old forum post about this situation, and then looked around for a way to cause bind to keep the journal files in /var/lib/bind, like Ubuntu's apparmor config specified. However, I wasn't able to find any directive to support this. It would seem that bind is adamant about keeping the journal file in the same location as the database it's modifying (which makes sense). So, as a fix, I just moved my custom database files into /var/lib/bind, and updated /etc/bind/named.conf.local to reflect the change. Problem solved. I just wanted to write this down in case it would help someone else.

---

