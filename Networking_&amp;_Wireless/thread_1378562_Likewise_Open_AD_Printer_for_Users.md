---
title: "Likewise Open AD Printer for Users"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by Greslore on 2010-01-11
Greetings,

I set up a client machine to utilize AD Authentication using Likewise Open.  Works great.

The problem I now face is getting AD domain users to be able to print to windows shared printers.  We use print stations where users need to swipe an ID to release their print job.  Ideally, they would log into the machine and the printers would just map with no user intervention, IE - avoid the need to type in login credentials again just to map printers.  

I can script something with lpadmin, but don't want the users to have to interactively type their passwords in.  I am able to add domain users into the lpadmin group, so perms on that level is not an issue.  

Any ideas on this?

---

### Post by Greslore on 2010-01-13
I found that I over complicated things.  All I needed to do was log in with a sudo account, add printer via LPD as //servername/printer and it was present to all users who logged in to the machine with their authenticated AD credentials on the print server side.

---

