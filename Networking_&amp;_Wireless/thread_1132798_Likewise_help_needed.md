---
title: "Likewise help needed"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by bpickel on 2009-04-22
Alright so i hope someone has seen this before.   I have searched and tried what I found but no luck.  I have joined my Ubuntu machine to my Windows domain at work and have successfully logged in with my domain account. 

  I can sudo but if I try and system configuration I get "you are not allowed to access the system configuration"  . i am fairly certain that this is a problem with local group membership. I have tried editing /etc/group to add my domain account to local groups but I cannot get it to work.

I have tried addin the domain user to the same groups as my standard ubuntu user but no luck. I have tried adding in the following formats 

DOMAIN\User

DOMAIN+User

[EMAIL="user@domain.net"]user@domain.net[/EMAIL]

None of these will work.  Can anyone help  ?

---

### Post by bpickel on 2009-04-22
No Help ?

---

