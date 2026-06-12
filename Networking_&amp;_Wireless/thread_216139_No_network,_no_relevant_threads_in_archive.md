---
title: "No network, no relevant threads in archive"
date: 2006-07-15
forum: Networking &amp; Wireless
---

### Post by chocolatetoothpaste on 2006-07-15
Wow, I need some help.  I have NO network connection.  I put in the disc, and it went to the live desktop, and the internet works perfect.  I didn't actually check the whole network, but if I have internet, good odds I have network.  But when I get the os completely installed, I have no network at all, I can't ping anything.  I have a realtek card, but I cannot remember which one exactly.  I think the driver is 8139too or something like that.  Just for information, my internet comes through this way:

DSL modem->Devil Linux Firewall->Whole network

So all computers (Linux for me, windows for the rest of the fam) get internet sharing through Devil-Linux firewall.  As a result, all computers have 192.168.1.XXX addresses.  I have rules setup on my firewall, so the computer in question has the ip 192.168.1.7.  It is static, but every other computer on the network is dynamic.  Please, give me some guidance.  I am sorry if the solution is elsewhere in the forums, but I have searched for some time and cannot find anything that got me on the right track.  Thanks!

---

### Post by XAsmodeanX on 2006-07-15
Make sure the nameserver in your /etc/resolv.conf file is NOT the ip address to your DSL modem.  If it is, erase that line and save the file.  Then see if you can get to websites.  If this doesn't work, can you ping things?  Can you ping IP addresses outside of your local network?  Within?

---

### Post by chocolatetoothpaste on 2006-07-15
resolv.conf looks fine.  I can't ping ANYTHING in the network, so I know it is something to do with my setup in Dapper, I just don't know what to change.  I have 0 network connection, but ifconfig looks fine, looks normal.

---

### Post by maethor on 2006-07-15
When you were running the live desktop, was that using a dynamic or static address?

---

### Post by mips on 2006-07-15
Do a search for '8139' here and you will find lots of threads seeing there are known issues with that chipset.

---

### Post by chocolatetoothpaste on 2006-07-16
> **maethor said:**
> When you were running the live desktop, was that using a dynamic or static address?
I just put the disc in to install dapper.  Whatever was running as default for the live session is what worked.  I just opened a browser to test that the net was working, then I installed dapper.  That is it.  The internet just worked, but now the os is installed, nothing.

---

