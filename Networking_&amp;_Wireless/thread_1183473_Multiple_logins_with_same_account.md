---
title: "Multiple logins with same account"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by Rutger7 on 2009-06-10
Hi all,

I am migrating a small Windows Active Directory environment with Windows XP clients and roaming profiles to Ubuntu. My (new) setup is as follows:

[LIST]
[*]One Ubuntu 9.04 server with:
[LIST]
[*]LDAP server slapd (with user accounts stored in its database; configured using [this howto]("https://help.ubuntu.com/community/OpenLDAPServer"))
[*]NFS server nfsd (for the roaming profiles and group shares)
[/LIST]
 
[*]Six Ubuntu 9.04 clients with:
[LIST]
[*]LDAP client connected to PAM and Name Service (to retrieve account information; configured using [this howto]("https://help.ubuntu.com/community/LDAPClientAuthentication"))
[*]NFS shares from server automatically mounted using fstab
[*]GNOME interface
[/LIST]
 
[/LIST]
On startup, the clients mount /net to /net on the server. All the home directories are located in /net/home/*[user]*. This way, users can login on each client and have their own files and profile wherever they login. This all works perfectly.

I am setting up this environment at my university rowing club. Because we are all volunteers, in the current situation people don't have their own user accounts (committee members change every year). Instead, each committee has an account.

Sometimes, for example when there is a lot of work to do, two members of a committee are logging in on two computers. So member1 logs in with account committee1 on client1. Then, member2 logs also in with account committee1, on client**2**. Generally, in Windows, this works quite well. But after a lot of searching on the internet, this seems not possible with Ubuntu, because of filesystem locks. Is this true? If yes, what would be the best solution for this problem?

One guy advised me to create personal accounts for everybody (which expire the day they are not member of a committee anymore), with access to a group/committee share on the NFS server. Is this the preferred way to do this?

Thanks very much for every help given!

Greets,
Rutger

---

### Post by Lampi on 2009-06-10
> **Rutger7 said:**
> Is this the preferred way to do this?
I second that - it's the easiest and most common way. Besides: you don't want to keep personal data of long gone employees anyway, won't you?

---

