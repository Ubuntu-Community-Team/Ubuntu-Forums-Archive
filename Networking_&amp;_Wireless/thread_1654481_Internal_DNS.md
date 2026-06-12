---
title: "Internal DNS"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by deviant01 on 2010-12-28
Okay I've seen a couple of post about this but nobody seems to have covered this.

If I try ping a host on my internal lan from my ubuntu notebook the host name never resolves, but if i ping [www.domainname.xxx](www.domainname.xxx) it will resolve because our dhcp server is setup as the dns server too.
If I use the connect to server tool and select samba share and specify host by name, it can resolve that and the shares show up... same dns server, same machine, but different interface/program. I don't quite know what's going on here


my real reason behind this is because my synergy+ keeps falling over whenever the synergy servers dhcp lease expires and it gets a new I have to then specify the new address and change configs

---

### Post by headvampyre@hotmail.co.uk on 2010-12-28
what address are you tryng to ping? make sure you dont uase a web adress e.g. [www.mybox.com](www.mybox.com), use ping mybox or if you have a DNS suffix add that to it e.g. mybox.lan
hope this helps :)

---

### Post by deviant01 on 2011-01-01
I'm not sure if I've made this clear but consider the following example:

On a Windows network PC A and PC B are configured using DHCP...

after 8 days(my network) their DHCP leases expire then they get a new address.
so previously A address = 10.0.0.1
              B address = 10.0.0.2
today B might have an address of 10.0.0.10

so when A looks for B and it finds out the B no longer lives at 10.0.0.2 it phones the internal DNS server and asks where is computer B now lives, the DNS server then resolves this and tells computer A that his friend now lives at 10.0.0.10 that way when you ping B it will automatically resolve to whatever its 
present address is... 

but in ubuntu you have to add this **** manually to your hosts file... but you dont need to do this with the internet?

Strangely enough if your go to places and look in networks, all the hostnames are there... why can nautilus use internal DNS resolution but not the terminal

---

### Post by PatchesTheCaveman on 2011-01-01
Are you sure your DNS server is returning results for the machine on your local network?  *Connect to Server* will work even if DNS doesn't point to your local machines because Samba also uses the Windows Network Neighborhood protocols to find computers on your network.

If you want to test it out, run
```
dig other-internal-hostname
```
replacing other-internal-hostname with a local hostname.  If your local DNS server is returning results for your local machines, that should display an A record with that computer's IP address.

---

