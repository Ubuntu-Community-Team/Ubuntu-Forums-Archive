---
title: "Bashing my head into the 6 domains, 256 character limit."
date: 2012-02-15
forum: Networking &amp; Wireless
---

### Post by rusty0101 on 2012-02-15
I'm working in a company that's merged with a few different companies, and I manage routers and switches, and a few other related devices for this company. While at some point devices will be migrated into common domains, there currently are more than 50 domains that devices may be in. 

Considering that users.co1.com is a different search domain string from co1.com. in that I'm not going to find r1.co1.com if the search string only has users.co1.com in it. Yet I also need to manage devices that will be in users.co1.com, perhaps sw1.users.co1.com.

I can not give the actual names of all of the domains that I support, however a list that would be similar would look like

net.corp, co1.com, co2.com, co3.com, co4.com, co1.net, co2.net, co3.net, retail.co1.com, servers.co1.com, dev.retail.co1.net, dev.servers.co1.net, mgmt.co2.com, mtmt.co2.net, retail.co2.com, sales.co3.com, sales.co3.net, hosts.co4.com, hosts.co4.net, will.co3.com, wont.co3.net, others.co3.net, net.co1.com, infra.co1.com, infra.co2.com, infra.co3.net

and so on. You can imagine my dismay at finding that the 'search' directive in resolv.conf supports a maximum of 6 domains and 256 characters.

In the past I've written my own python scripts that will take a host name, and do dns queries for each of the domains and return a fqdn for the device. (Fortunately the various host naming conventions for the companies that have merged has been different enough that end hosts have not had a significant number of collisions. There is no r1.co1.com conflicting with an r1.co2.com by the time I need to support the device, though as devices migrate from one domain to another, there are times when a single device may appear in both domains, r1.co1.com and r1.co1.net.)

The problem is that when I do that I have two different courses I can take. I can have the script update /etc/hosts with the "IPaddress, hostname, hostname.fqdn # dateAdded" results, which requires that the script have authorization to the hosts file, which I don't think is a good idea to just grant wholesale access to. The alternative is to write wrappers for all the tools (ssh, etc.) that uses the python script to get the fqdn, then call the actual tool to do the work with that result.

Additionally in the past I have cached the results in a separate file, and would use the dateAdded entry to purge entries over a week or two old. The cache would be checked before the script would do an exhaustive search in DNS.

All of that was lost when my system went through a hard drive failure, without a recent backup, and at best it was a kludge.

My experience is that the man page for resolv.conf is partially wrong for the 'search' line. Along with other elements it has the note "The search list is currently limited to six domains with a total of 256 characters." My experience is that more than 6 domains are searchable, but the 256 characters does seem to be honored. I'll also note that while that note is in the Debian man page for resolv.conf, neither restriction seems to be a problem for debian. Debian systems I've encountered seem to be able to search through the more than 50 domains we've got without a problem.

Does anyone know of a workable system level alternative that provides for a search domain of more than 500 characters? (The re-domaining is taking time and I've no confidence that we won't see another merger.) Recommending an ubuntu variation is acceptable, but before I rebuild this box on a different ubuntu variation, I would prefer knowing that it's a tested solution. If worst comes to worst, I may go to Debian, but I'd prefer not to do that either. Under Ubuntu I am also asking that we limit it to LTS releases as I'm not looking for 'bleeding edge' solutions to work from.

Thank you,

Rusty

---

