---
title: "Wifi manager requests my login password"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Brynster on 2009-12-03
Everytime I log in network manager has to access my keyring manager for the password to log into my wifi connection.

Is there a way of setting it to not require or automate the process. In Keyring manager i have given Network full read write permission, but its still the same.

Any further suggestions please. 

PS this is on 9.10 all previous versions of Ubuntu never required this and was a clean install.


Ta in advance all.

---

### Post by quixote on 2009-12-04
If you enable automatic logon at bootup, network manager will insist on the keyring authentication.  If you go through the login rigamarole, then you can set the network connection to automatic.  You can't do both.  This is the gnome developers' concept of security.  They know what you should be doing much better than you do.  And they can't even be bothered to tell us that, so some of us spend a lot of time trying to figure out why this doesn't work.

(Who, me?  Cross?  What gives you that idea?  I spent *days* trying to figure out what was wrong before finding out it wasn't a bug.  It was a feature.)

---

### Post by Brynster on 2009-12-04
Thanks for the reply. Glad I am not the only one suffering from an undocumented security feature. Seems silly though, if somebody can come and sit at my pc with full access to anything on there that they need to enter my password to surf the web. Not that anything important is on there I mean seriously would anybody auto login on something that keeps personal info on.?

It's this kind of we know better attitude and you'll use your pc how we want you too that drove me to Linux based freedom. Looks like the party is coming to an end. Wonder if it is the for Kubuntu anybody know?

---

### Post by quixote on 2009-12-04
No, the whole idea behind Kubuntu is opposed to that.  They had, shall we say, issues (as in Issues) with kde 4.  That was when I had to switch to the gnome side.  I think they're actually resolved at this point.  Worth a look, for sure.

---

