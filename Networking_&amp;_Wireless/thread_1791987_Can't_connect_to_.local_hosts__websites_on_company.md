---
title: "Can't connect to .local hosts / websites on company network (DNS issue)"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by dcrooke on 2011-06-27
Problem:

Your company network has internal only hosts / websites with names that end in .local, e.g. [http://intranet.new-york.local/](http://intranet.new-york.local/) 

Your freshly installed Ubuntu machine works fine on the network, has internet access, etc. but cannot connect to these particular systems. 

Testing DNS with tools like dig / nslookup works fine, but normal name resolution with ping / telnet / browsers does not work.


Solution:

1. Open a terminal window
2. Enter the command [FONT="Courier New"]**sudo nano /etc/nsswitch.conf**[/FONT]
3. Change the following line:

[FONT="Courier New"]hosts: files mdns4_minimal [notfound=RETURN] dns mdns4
[/FONT]
to this:

[FONT="Courier New"]hosts: files dns[/FONT]

4. Press Ctrl-X, Y, Enter to save


Explanation:

Ubuntu ships configured to do name lookups for self-configuring networks, based on the AppleTalk / mDNS / Bonjour protocol. In the configuration shipped for the resolver, this protocol is considered the final aurhority for the ".local" top level domain, and DNS will not be checked. The above configuration change eliminates this and restricts lookups to (a) /etc/hosts file, followed by (b) DNS

---

### Post by Iowan on 2011-06-27
FWIW (For What It's Worth) - it's always a good idea to make a backup copy of a config file before editing it.  You can always delete it if you don't need it - or rename it if you do (need it).

---

