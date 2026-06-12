---
title: "can ubuntu 9.10 register his name with a microsoft dns secure only?"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by kokanidja on 2010-02-19
as i sad in the question...can he? i know that kerberos was or still is :) the problem but using kinit and klist i get correct response...that means kerberos is working. but there is no record on dns that points to my comp...why?

---

### Post by Iowan on 2010-02-19
Kerberos is way outside my realm...
If machine gets IP address via DHCP, there's an option in */etc/dhcp3/dhclient.conf* to send hostname. Probably doesn't apply at all, but thought I'd mention it.
Winbind is another term that comes to mind...

---

### Post by ant2ne on 2010-02-19
Man, that is a good question. I noticed that with my linux servers on the windows network (windows DNS server too) I had to manually specify the DNS record because the name wasn't resolving. This wasn't a big deal because they were static IPs anyway. I recently put an ubuntu box on the doman (using likewise) so that it authenticated user logins to Active Directory. I would assume that it had to play kerbose and DNS friendly, but I didn't examine it any closer and I moved on to another project. I do plan to pick up that project again. Try likewise out and see if it updates DNS. LMK what you find out.

[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/")

---

### Post by kokanidja on 2010-02-20
yes i did use likewise-open5 and it did make a comp account on DC but not on DNS and whats more important i cant logon with an AD account...
i know that before kerberos was the problem and if it where set to secure only linux could not update dns record...but now it shouldnt be a problem. kerberos is working...what now?
it seems like likewise-open5 dont use winbind servis...there is lsass, and it dont start samba. i joined my comp to domain but, no dns record, not able to authenticate and no samba working...
and i did try to put fqdn name in dhclient.conf but nothing happened

---

