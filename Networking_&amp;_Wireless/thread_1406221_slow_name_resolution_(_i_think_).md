---
title: "slow name resolution ( i think )"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by dragnrebrn1 on 2010-02-13
about 4 days ago my browser started lagging when loading pages.  im not sure how to fix it.  ive looked on google and found a few things but they all seem like they are shooting in the dark.  the only reason i think its name resolution is because when i loaded chrome to check another browser it said "resolving host" down at the bottom while it was lagging.

before i start trying these random "fixes" for things that dont really sound like my problem.  i was wondering if there is a way ( like a verbose mode ) to see whats going on and where it gets hung up so i can figure out what is exactly wrong before i start trying some of the random fixes i found around the net.

a couple of things of note:
other computers on the network seem fine.
a vmware fresh install works fine even with all the upgrades
ive switched to open dns in the router months ago (local dns on the machine)
firefox is my browser and chrome did the same thing.

thank you in advance
--Neil

---

### Post by Jim_in_Omaha on 2010-02-13
Same thing here too... Hmmmmmmm

---

### Post by tegryan on 2011-02-17
Same here, and it just started within the last month.  Here are some things to try, none of which have fixed my issue, but they seem to help a lot of people.

1. Disable IPv6 in Ubuntu, or just in Firefox if that's what you're using:
[http://askubuntu.com/questions/8704/slow-dns-resolution](http://askubuntu.com/questions/8704/slow-dns-resolution)

2. Ping the domain to make sure it's not general network latency

3. Change your DNS servers (use namebench ([http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)) to find fast ones).  Consider using openDNS ([http://www.opendns.com/](http://www.opendns.com/))

4.  Make sure your /etc/nsswitch.conf file has the correct order on the hosts line:

hosts:          file dns

5.  Run wireshark to see what the heck is going on

For me when I run wireshark the DNS resolution takes 6.5 seconds or so to return the correct result.

I'm going nuts, I am pretty sure something is timing out, but I don't know what or where.

Hope that helps a bit.

---

### Post by war59312 on 2011-02-17
Same, started with upgrade to Ubuntu 10.10, so looks like some package was updated and is causing this problem.

---

