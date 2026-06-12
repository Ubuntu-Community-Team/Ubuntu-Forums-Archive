---
title: "SMB question"
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by nevyndweomer on 2006-03-04
I have just installed my Ubuntu  and added Samba 

It has all installed ok but I have a small problem I can see the 'doze machines on the lan but they cannot connect to me  

how do I set this up ? 

when I browse  or put the name in I dont see the machine, but when I put in the IP I get a login prompt but the user login does not get me in 
I guess I need to set this up but I am a complete noob and need some pointers  

Many thanks in advance  
Nevyn

---

### Post by el3ktro on 2006-03-04
You have to setup user names for Samba first. For example, when the user name you use on your Linux box is "john" then it's as simple as doing an

sudo smbpasswd -a john

in the Terminal. Enter a password for john twice, and then you'll be able to login as user "john". When you add a new user to Samba, this user must also exist on the Linux box itself.


Tom

---

### Post by woedend on 2006-03-04
interesting.  When I did mine I went as far as to create a whole new ubuntu user account.  I'll try it this way next time.

---

