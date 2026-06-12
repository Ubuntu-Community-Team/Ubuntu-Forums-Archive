---
title: "workaround to get win xp (home) client to remember network password for samba shares"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by eudemus on 2009-09-03
This is the ugliest workaround, but it's probably safe within a home network. I'd be interested in a better solution, though.

PROBLEM:
Having set up samba shares on my Linux box, I found that although Windows XP (Home) could map these shares as network drives, and authenticate using a specified id/password (different from that used to log in to XP), it would not remember the password or id from one session to the next.

[LIST]
[*]I didn't want to dispense with all the nice *nix permissions, nor did I want to have to have 777 permissions for all shared folders.
[*]I didn't want to have to match manually the id/password combinations on both machines.
[*]I wanted to be able to use a valid linux/samba id/password to access the samba shares as a particular user, wanted to be able to set this up once and for all in XP and have the id/password stored and used for accessing those network shares.
[/LIST]

I believe that XP Pro and other versions of XP can store network passwords, but having tried everything (I think!), I'm now pretty sure that XP Home will not. No doubt, another scam to get you to buy the more expensive M$ product ....

WORKAROUND:
I wrote a batch script which had in it one line such as the following for each of the drive mappings I wanted:

```
NET USE X: \\computername\sharename /USER:domainname\username password
```
(where X: is the drive letter you want to map to in XP)
Save this with a .bat extension and put it in 
C:\Documents and Settings\[User]\Start Menu\Programs\Startup\
so it runs whenever you log in as that user.

The big ugliness of this solution is that I have the password stored in plain text in a bat file. Probably ok at home on a very small scale, but not really a great way to go.

I'd be interested in suggestions about better ways to go, preferably retaining the use of samba.

Cheers, Eudemus

---

