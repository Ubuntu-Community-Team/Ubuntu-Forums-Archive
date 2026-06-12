---
title: "Proper OU Syntax for joining AD"
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by anthonious on 2009-02-05
Hi,

New to Linux and trying to verify that for supplying a specific OU for Likewise (sudo domainjoin-cli join fqdn.of.your.domain Administrator), the format would be:

sudo domainjoin-cli join -ou abc/def/ghi/jkl/mno example.domain Administrator_acct

Where abc-----mno is going top/bottom of OU schema

Trying to connect Ubuntu 8.10 machine to AD to allow domain users to login, no file server sharing/mounting or anything.

I believe I'm close as I'm asked for my admin password for the domain to authenticate the join and get the following error:

Could not connect to server xyz.example.domain 
The username or password was not correct.
Connection failed: NT_STATUS_LOGON_FAILURE
Failed to verify membership in domain: NT_STATUS_LOGON_FAILURE!

Error: Unable to join domain [code 0x0008000e]

Domain join operation failed to create the computer account in 
Active Directory.  Common causes are a bad administrator password, a bad OU name, or an existing computer account without modification permissions.
---------------------------------
So it seems my machine can't talk to our domain controller.  I'm certain I'm using the right account and password as I use this acct to join my OS X machines.

Thanks!

---

