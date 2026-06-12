---
title: "Connect to a Windows share without a password"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by grantoos on 2010-05-22
Hi,

I'm wondering if I can get an answer to this one.

I'm pretty new to Ubuntu, been using it off and on for a few months now.  Right now I'm using Lucid and I have no problem connecting to the other PC's in my house that run Windows 7, however when I try to access them it asks for a password.  I disabled the password on the Windows PC, so is it possible to get into them without a pass?  If so, how?

Thanks in advance.

---

### Post by lykwydchykyn on 2010-05-22
Try "guest" for the user and no password.

---

### Post by grantoos on 2010-05-22
Thanks for the reply.

No go, didn't work. I've also tried the name of the PC and no pass, same thing.

---

### Post by therezin on 2010-07-05
I've got the same issue. I'm running 10.04 on my laptop and I've got a Win7 PC called Central in a workgroup (not a domain) called NEWSTREET. My logon on both machines is called dan, and on the Win7 PC that account is set up without a password. I've tried the following usernames and domains without any luck:

domain | user
CENTRAL | dan
CENTRAL | guest
NEWSTREET | dan
NEWSTREET | guest
NEWSTREET\CENTRAL | dan
NEWSTREET\CENTRAL | guest
NEWSTREET | CENTRAL\dan
NEWSTREET | CENTRAL\guest

Anyone out there got any thoughts on this? I'm sure there's someone out there that can access their Windows shares from their Ubuntu machine, what am I missing?

---

