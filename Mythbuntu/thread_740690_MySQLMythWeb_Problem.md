---
title: "MySQL/MythWeb Problem"
date: 2008-03-31
forum: Mythbuntu
---

### Post by tonyr1988 on 2008-03-31
I broke my MythWeb. Hopefully you guys can help me out. I get this error message for any MythWeb page:

> Database Access Denied

You are most likely receiving this message because you have failed to configure mythweb's database login info.

Please see INSTALL for instructions.

But, I'm not innocent - I was messing with a script to automatically get screenshots for videos, and I changed my mythtv user's password in MySQL to "mythtv." I think this was a bad decision. What should I do to fix it?

Everything else works fine - I had to set the MySQL password in the MythTV backend to "mythtv" from the random preset one, but it works perfectly. Is there a similar setting for MythWeb that I just can't find?

I tried uninstalling/reinstalling it, but that didn't work.

Thanks for the help.

---

### Post by mvan83 on 2008-03-31
What's in your /etc/mythtv/mysql.txt file? Make sure the password there is the same. (No guarantees this will fix the problem though.)

---

### Post by tonyr1988 on 2008-03-31
> **mvan83 said:**
> What's in your /etc/mythtv/mysql.txt file? Make sure the password there is the same. (No guarantees this will fix the problem though.)
That file has the correct username/password combination.

My MythTV works perfectly fine - frontend connects to backend, I can access all my recordings, music, videos, etc. MythWeb is the only thing having problems.

---

### Post by laga on 2008-03-31
/etc/apache2/sites-available/mythweb.conf for MythTV 0.21. 'sudo dpkg-reconfigure mythweb' might fix it, too.

---

### Post by tonyr1988 on 2008-03-31
> **laga said:**
> /etc/apache2/sites-available/mythweb.conf for MythTV 0.21. 'sudo dpkg-reconfigure mythweb' might fix it, too.

/etc/apache2/sites-available/mythweb.conf was exactly what I was looking for.

Thanks for the help - it was easy after I found that. :)

---

### Post by drubin on 2008-04-22
Just to add to this post encase some one else needs it for a reference. 

I actually tried all of the above.  But the only thing that seemed to work was to add my own user for the mysql db, and then to use that username/password in the .htaccess file

---

