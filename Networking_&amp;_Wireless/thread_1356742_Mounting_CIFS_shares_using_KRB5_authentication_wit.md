---
title: "Mounting CIFS shares using KRB5 authentication without joining the domain"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by Philippe Petitcolin on 2009-12-16
Hi all,

I'm wondering if it is possible to access a CIFS share (hosted on a Win2K3 server) from an Ubuntu 9.10 client WITHOUT joining the client to the Active Directory domain...

Here's what I tried this last couple of hours :

I have installed and configured krb5, mount.cifs, keyutils. Fine.

When I try to mount the remote share with (after getting a TGT by kinit ad_user):

[FONT=Courier New]mount.cifs //winserver/share /media/cifs -o username=ad_user,domain=ad.domain,sec=krb5 --verbose[/FONT]

(with ad_user the active directory user name and ad.domain my active directory domain)

mount.cifs raise the following error :
[FONT=Courier New]
mount error(13): Permission denied[/FONT]... not so cool...

I check with klist my tickets cache :

[FONT=Courier New]Ticket cache: FILE:/tmp/krb5cc_0
Default principal: [email]ad_user@AD.DOMAIN[/email]

Valid starting     Expires            Service principal
12/16/09 17:29:37  12/17/09 03:29:35  krbtgt/AD.DOMAIN@AD.DOMAIN
    renew until 12/17/09 17:29:37
12/16/09 17:31:04  12/17/09 03:29:35  cifs/winserver@AD.DOMAIN
    renew until 12/17/09 17:29:37[/FONT]

Everything looks fine I get my TGT and session ticket for the windows server...

When I check a network capture done with wireshark, everythings works great until the SMB "Tree Connect andX Request". The windows server response is a STATUS_ACCESS_DENID and the connection is closed.

In the windows security event log I can see a successfull logon from my Ubuntu workstation followed immediately by a successfull logoff... 

My guess is :
I managed to open a connection using kerberos to the cifs server BUT when my workstation tried to access the files the windows server was unable to match my Unix account (root as I "sudo-sued" my bash)  to an Active Directory account and kicked out this infamous unknown user.

Does anybody here can provide me an other explanation and (finger crossed) a workaround to achieve my goal ?

Goal wich is I remind you :
Mounting CIFS shares on active directory members windows servers, using kerberos and an active directory user account BUT without having to join the Ubuntu workstation to the domain.

Thanks by advance.

And sorry for my rather neanderthalic english...

---

