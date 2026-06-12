---
title: "starting SWAT as ROOT in FIrefox - can't"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by gilch on 2008-12-07
I have tried and tried to use SWAT, but whenever I put in [http://localhost:901](http://localhost:901) 
Firefox immediately goes to SWAT (without asking user and passwd) and displays SWAT with only the four capabilities.

It tells me that I am signed in as 'gilles' (my username)

I read that it needs to start as root. They said to use
sudo passwd root
That didn't work either.

So my question: how to I force Firefox to start [http://localhost:901](http://localhost:901) as root?

Gilles

---

### Post by Iowan on 2008-12-08
I don't have/use SWAT. Otherwise, I'd check **man** page to see if there are options to log in as a specific user.

---

### Post by gilch on 2008-12-08
I finally got SWAT to ask for user and passwd. I tried root, and my username, and only my username worked, but only gave standard 4 options.
Does my root have a username?

---

### Post by jonobr on 2008-12-09
info on root with Ubuntu
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by bab1 on 2008-12-09
Boy that is a problem.  I just tried SWAT and indeed it needs the system root and password.  I have set up root to have a known password ( in other words I have a root account).  Invoking SWAT in Firebird brings up the dialog for me and since I have a valid root account it works.

I don't know what other Ubuntu people do.  I also tried running FIrefox as root but it still asked for a login to SWAT.  Foiled again.

---

### Post by hundred1906 on 2009-04-18
I have the same problem. I assume the fix is simple because others seem to be using SWAT without problems.

Help please.:(

---

### Post by lfaraone on 2009-04-18
I don't think you are understanding what they are saying. 

It doens't matter which user you *access* the web page as, but rather which user under which you start SWAT with. 

You arn't starting anything when you visit the site. 

See [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html#xinetd](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/SWAT.html#xinetd) for how to set it up to start as the proper user.

---

