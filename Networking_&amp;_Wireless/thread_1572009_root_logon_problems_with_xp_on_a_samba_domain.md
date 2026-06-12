---
title: "root logon problems with xp on a samba domain"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by jimmybarcelona on 2010-09-10
this is probably a simple fix, but I am at a loss. Been working on this for days, and would like to wrap it up.

I've setup a samba server to act as a primary domain controller on a small network. I've added a machine account with samba. when I try to join the domain on a windows xp machine, it asks for an account with permission to join the domain.

all my googling tells me that I need to logon as root the first time i join an xp machine to a samba domain. root login is disabled by default for security reasons on ubuntu. do i need to go in and enable root logon everytime I wish to add another xp machine to the domain? or is there a way to designate in samba that I want my username to be allowed to join domains? or is there a way to create a "samba root" user?

---

