---
title: "Nt_status_connection_refused"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by karmic-koala on 2010-08-21
Hi all, I am sharing a folder on my external drive using Samba. Others are unable to access it so I ran a few debug tests. 

Whilst trying to connect from my own machine, I get...

smbclient -L my_ip
Enter user password:
Connection to my_ip failed (NT_STATUS_CONNECTION_REFUSED)

I use UFW as my firewall
sudo ufw status
Samba    ALLOW    Anywhere

So there shouldn't be a problem. Any thoughts?

---

### Post by karmic-koala on 2010-08-21
Update - this is only true for when I connect to my ip (eth0) same command but to localhost lists valid samba shares

smbclient -L localhost -N
Domain = etc OS = etc Server = etc

which I guess means samba is failing to bind to eth0 but I have interfaces = eth0 lo .

---

### Post by karmic-koala on 2010-08-21
Update -

Solved this one, just updating with solution for rest of the community :)

lsof -ni:139 and 445 revealed samba was only binding to lo, 

set [bind to interfaces only] line in smb.conf to FALSE and reload samba, done the trick :)

---

### Post by copyhold on 2011-02-03
> **karmic-koala said:**
> Update -

Solved this one, just updating with solution for rest of the community :)

lsof -ni:139 and 445 revealed samba was only binding to lo, 

set [bind to interfaces only] line in smb.conf to FALSE and reload samba, done the trick :)
did the trick for me as well

---

### Post by jimww on 2011-09-24
this works for me as well, after a few days trying without luck to diagnose the problem. the language is different in my smb.conf file:    bind interfaces only = no ( default was set to 'yes' )

everything works now, so i can get back to work too. thanks!

---

### Post by capscrew on 2011-09-24
> **jimww said:**
> this works for me as well, after a few days trying without luck to diagnose the problem. the language is different in my smb.conf file:    bind interfaces only = no ( default was set to 'yes' )

everything works now, so i can get back to work too. thanks!

The default is ** bind interfaces only = no**.  

If a parameter is not listed, then the default is applied.  If you found this in the smb.conf file it was set it that way.  See [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://samba.org/samba/docs/man/manpages-3/smb.conf.5.html") -- this is a complete listing of all the parameters.

---

