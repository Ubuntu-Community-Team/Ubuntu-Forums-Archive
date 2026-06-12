---
title: "Weird DNS problem"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Cheiz87 on 2009-04-15
Today suddenly i couldn't connect anymore to a lot of domains. The weird thing is some work, most don't (e.g. [www.google.com](www.google.com) works but [www.ubuntuforums.org](www.ubuntuforums.org) doesn't). Which work and which don't seems pretty random.
It seems to be a DNS error because when i "ping" in a terminal window every hostname that does not work also doesn't resolve into an IP address.
However when i boot windows XP it does work normally (that is why i can post this message now)
I tried to enter a manual DNS address in the connection settings. The weird thing is - the behaviour doesn't change, even if i enter a bogus DNS IP or no IP at all, it still connects to the same addresses (also after disabling and enabling the connection, so at "connection information" it shows the bogus DNS IP)!!!
Also, when I start firefox now i get a page "Welcome to Ubuntu 8.10" instead of the default google-ubuntu search page. This might be because the IP of the latter also can't be resolved.
This is really frustrating me because now I can't use ubuntu and have to use XP...
I am connected trough a speedtouch ADSL modem (so i have a gateway adress like 192.168.1.254)
I tried this but didn't help: sudo install apt-get resolvconf
Anyone help me?

---

### Post by ajmctaggart on 2009-04-15
I don't know much about your particular Modem or its settings...

But have you tried to create a new network location (Other than Auto?)In there, try using OpenDNS, 208.67.222.222 208.67.220.220...

Let us know if there is any change with the behavior with a new location...

Sorry if you've tried this or it's redundant...

Good Luck...

---

### Post by Cheiz87 on 2009-04-15
It's getting even weirder...
I booted from ubuntu CD, there everything worked as it should (with the same network settings = full dhcp)
Then i rebooted and chose another option in the boot menu (i can choose between ubuntu(..)-11 and ubuntu(..)-7 and XP, now i chose -7 instead of -11)
There suddenly i was able to download updates (which didn't work before) and access ubuntuforums.org, but other addresses still did not work...
Then i rebooted and started -11 as normal again. But still the same problem... (and now also no ubuntuforums.org and no updates).
Even when rebooting again to -7: NO ubuntuforums.org, no updates.
So:
XP/ubuntu CD: everything works fine
ubuntu normal boot: lot of names do not resolve!

Is there anything general i can do less drastic than reinstalling ubuntu (like reinstalling only some packages or something?)
I kind of hope it's some weird combination between my ubuntu and my ISP and that it will cure automatically...
now i'm back to XP...

---

### Post by Cheiz87 on 2009-04-15
> **ajmctaggart said:**
> I don't know much about your particular Modem or its settings...

But have you tried to create a new network location (Other than Auto?)In there, try using OpenDNS, 208.67.222.222 208.67.220.220...

Let us know if there is any change with the behavior with a new location...

Sorry if you've tried this or it's redundant...

Good Luck...

Thank you for your reply.
I did try that, but doens't change a thing... Like I said, it seems it doesn't matter what i enter as DNS IP...
I also disabled IPv6 and rebooted, but also no effect

---

### Post by puppywhacker on 2009-04-15
just a stab in the dark, you maybe running your own dns server, or you're maybe using zeroconf. could you try to stop both?

/etc/init.d/named stop
/etc/init.d/avahi-daemon stop

Then could to resolve ubuntuforums.org manually using dig or nslookup

dig ubuntuforums.org
dig @208.67.222.222 ubuntuforums.org
dig @localhost ubuntuforums.org

---

### Post by Cheiz87 on 2009-04-15
SOLVED!
(kind of)

I looked into the resolv.conf file. Turned out there were 3 DNS ip's in there. The first two didn't look familiar to me, the last one was my default. I sudid the file and commented the first two ip's and now everything is back to normal! Turned out those 2 ip's are from my university. Probably got there because sometimes i use VPN to connect through my university network. Probably their nameservers are having some problems...

The only thing is resolv.conf says DO NOT CHANGE THIS FILE IT WILL BE OVERWRITTEN!!! so i'll see what happens when reboot... but i'll find something for that at least i know what was wrong now (apparently when there are 3 dns ip's in resolv.conf the last one is not tried?)

---

### Post by Iowan on 2009-04-15
[This]("http://ubuntuforums.org/showthread.php?t=971064") thread discusses a (kind of) similar problem.

---

### Post by ajmctaggart on 2009-04-16
Glad you've got it working...kind of...;)

---

