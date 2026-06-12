---
title: "cubert.itri.brighton.ac.uk entry in mySQL privileges database"
date: 2007-10-24
forum: Mythbuntu
---

### Post by uconnkoala on 2007-10-24
So I just set up my new Mythbuntu 7.10 box, and installed phpmyadmin

I check out the privileges page, and see an entry that looks like this:


root  	
cubert.itri.brighton.ac.uk  	
No  	 
ALL PRIVILEGES    
No



Does that strike anybody else as being a little odd ?

---

### Post by superm1 on 2007-10-24
This is inevitably a consequence from the machine it was built on.  It appears to have been overlooked on our parts.  Can you please file a bug on this?

---

### Post by uconnkoala on 2007-10-24
sure - the Red Sox are playing tonight, but hopefully I'll get around to it soon


just making sure it wasn't a security breach or something, since it required no password for access

that red [COLOR="Red"]No[/COLOR] always makes my toes curl a little bit

---

### Post by superm1 on 2007-10-24
Yeah, i double checked and that is our amd64 build host.  Feel free to delete that entry.

---

### Post by pasta514 on 2007-11-13
could you be so kind as to give the instruction on how to delete it?

TIA

---

### Post by uconnkoala on 2007-11-13
I just used phpmyadmin to delete the row from the Privileges screen

Command line SQL is just so messy :)

---

### Post by pasta514 on 2007-11-13
oh dear, another tool to install and learn.  Was hoping to not have to do that :( 

Sounds to me like not a security risk?

---

### Post by uopjohnson on 2007-11-13
I think the sql would be:
```
REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'root'@'cubert.itri.brighton.ac.uk'

```
It is a security risk if you have allowed access to your mysql install from the internet and someone from cubert.itri.brighton.ac.uk decides they don't like you.

---

### Post by uconnkoala on 2007-11-13
definitely learn about phpmyadmin after you have mastered command line SQL

it makes working with mySQL so much easier


and yeah, its not a huge security risk, but its enough of one (no root password) that the loophole should be closed

your mySQL shouldn't be open to the Internet anyways, and I don't believe it is by default

---

### Post by pasta514 on 2007-11-13
> **uconnkoala said:**
> definitely learn about phpmyadmin after you have mastered command line SQL

it makes working with mySQL so much easier

I was hoping to not learn mySQL at all.

---

### Post by uopjohnson on 2007-11-13
> **pasta514 said:**
> I was hoping to not learn mySQL at all.
How is that fun? :) 
You should probably go ahead and install phpmyadmin.  I'm sure there is plenty of help in the main forum for that.

---

