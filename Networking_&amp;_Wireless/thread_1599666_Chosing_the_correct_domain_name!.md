---
title: "Chosing the correct domain name!?"
date: 2010-10-18
forum: Networking &amp; Wireless
---

### Post by gewone on 2010-10-18
Hi!

I'm just curious on what domain name to use for my home server. By default, there is no one set, but only the host name that I gave the computer during first install ('RAZKO').

Now, imagine the following. My computer is on LAN, connected against Internet through NAT/DHCP. Local IP is 192.168.0.11, whereas dhcp- and nameserver is 192.168.0.1 (my router).

External IP is dynip12451.kngst.myisp.com

I have also attached a DynDNS.org adress (mycoolbox59.mine.nu) to my external (Internet) IP. As this was not enough, I have _also_ purchased a domain name (candybanana.com), that I have made a A-record for, pointing at my Internet IP.

So now, what should I enter for domain name?

My /etc/hosts files looks like this:

```
127.0.0.1       localhost
127.0.1.1       RAZKO
# 127.0.1.1 razko razko.local

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Nothing complicated, only default values. And all the services I host over tcp/ip from this box seems to work really fine. There's only one thing that bothered me, the 'sudo apache2ctl restart' gave me this annoying message:

*'Restarting web server apache2 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName'*

This is what first got me even thinking about actually setting a domain name, since there had not been any reason before, since everything had worked just fine.

But now, could some of you true enthusiasts slash network gurus out there tell me what would be the correct domain name value in my case, with the scenario described above?

And hey, listen to this. For the time being, I seem to have find a descent workaround. I entered the following line in the bottom of *'/etc/apache2/apache2.conf'* :

```
servername candybanana.com
```

Since that it doesn't complaint on restart, but acts all silent and dandy, i.e. desired behavior :) It also responds to all hosts, i.e. [http://internetip](http://internetip), [http://mycoolbox59.mine.nu](http://mycoolbox59.mine.nu), [http://crazybananas.com](http://crazybananas.com), and also [http://192.168.0.11](http://192.168.0.11) (from within the local network). So, everything is to my pleasure really, just want to make sure I didn't pull *'an ugly one'* by adding that line in the bottom of apache2.conf. My goal is to try to act serious and go *'by the book'*.

I hope I've described my situation well. Would be awesome if someone out there could (in words assigned to the simple user's ear) explain what my ideal *'/etc/hosts'* would look like, and/or if any entry at all in *'apache2.conf'*.

Finally, worth noticing that all host names are assumed (for integrity), no ping replies will (probably) come from either of the hosts above.

Ty in adv for looking into my little newbie question. 

Thank you!

---

