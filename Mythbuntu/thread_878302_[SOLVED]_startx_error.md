---
title: "[SOLVED] startx error"
date: 2008-08-02
forum: Mythbuntu
---

### Post by dmdbdd on 2008-08-02
Good afternoon:

Booting Mythbuntu I get the following error:

   "No resume image, doing normal boot...."

So I login and try to launch mythtv from the command line and I get the following error:

    "mythtv: cannot connect to x server:   

When I tried to run startx from the command line I get several pages of errors mostly like the following:

     "Cannot create /dev/null: Permission denied"
     "-Bash: /dev/null: Permission denied"
     "/usr/bin/startx: Line 176 /dev/null: Permission denied"

I've done several clean installs, all with the same result!

So..., what do I do now?

Regards,

dmdbdd

---

### Post by prshah on 2008-08-02
> **dmdbdd said:**
> 
Booting Mythbuntu I get the following error:
   "No resume image, doing normal boot...."


That's not an error, it's a normal startup message.

> **dmdbdd said:**
> 

When I tried to run startx from the command line I get several pages of errors 

can you post your /var/log/Xorg.0.log file if it's available?

---

### Post by dmdbdd on 2008-08-04
Good afternoon prshah:

Sorry for taking so long to get back to you. I'm new to Linux and it took me a while to figure out how to get this log file on to a floppy so I could send it to you. I still don't have access to the internet on by Mythbuntu machine yet(one step at a time).

I have attached the 'Xorg.0.log' file as 'Xorg.0.log.zip'. I tried opening it with Notepad (forgive me, I'm a windows guy) and it was not formatted correctly and therefore very hard to read, but opening it with Wordpad is was formatted correctly. I'm sure that you Linux guys have your own text readers.

Regards,

dmdbdd

---

### Post by dmdbdd on 2008-08-08
This issue has been resolved - thanks to those who tried to help :)

Regards,

dmdbdd

---

