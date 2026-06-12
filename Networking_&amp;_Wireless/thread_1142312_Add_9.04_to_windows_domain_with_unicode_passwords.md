---
title: "Add 9.04 to windows domain with unicode passwords"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by lucvdv on 2009-04-29
I'm trying to join a Ubuntu machine to an Active Directory domain where all accounts with administrator rights have unicode characters in their passwords (non-keyboard characters entered through Alt+(number) in windows or Shift-Ctrl-U(hex number) in Linux, hex number is 4 hex digits so it's really unicode and not an 8-bit ASCII code).

likewise-open is installed and nsswitch.conf was modified to make name resolution in the local domain work, as described in other threads.

I can access network shares using those domain accounts and passwords, although logging on to them seems to be slow.

But when I try to add the machine to the domain, it won't work.  The error message seems to mean that the password is where it fails.

(Replaced the domain name by 'mydomain.local' and the account name by 'Administator' here, real names used are different.)

```
lucvdv@ubuntu:~$ sudo domainjoin-cli join mydomain.local Administrator
Joining to AD Domain: mydomain.local
With Computer DNS Name: ubuntu.mydomain.local

Administrator@MYDOMAIN.LOCAL's password:
[2009/04/28 07:35:00,  0] libads/kerberos.c:ads_kinit_password(356)
  kerberos_kinit_password Administrator@MYDOMAIN.LOCAL failed: Preauthentication failed

Error: Unable to join domain [code 0x0008000e]

Domain join operation failed to create the computer account in Active Directory.
Common causes are a bad administrator password, a bad OU name, or an existing
computer account without modification permissions.
```

Any ideas?

---

### Post by Rendawg on 2009-06-03
Same issue here.  Any help would be appreciated.

---

### Post by lucvdv on 2010-12-22
Ubuntu 10.10, a year and a half later: still the same.

I created a domain administrator account with nothing but standard alphanumeric characters in its password, especially for joining this machine to the domain.  It worked.

I can now log on (locally and ssh) to the ubuntu machine with domain accounts, except for those with unicode characters in their passwords.
I can access shared folders on the ubuntu machine with all domain accounts, including those with unicode passwords.

---

