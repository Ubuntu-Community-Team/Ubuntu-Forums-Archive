---
title: "Remote shell login through web browser?"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by norman_ on 2006-07-02
Hi everyone! 

I have been reading quite a bit recently about different ways to access my home Xubuntu installation from my restricted pc at work (WinXP can't install anything or run any .exe), vnc, ssh, webmin, etc. Now my wife thinks I'm spending too much time with the pc and not enough with her so I'm turning to you to cut a bit on the reading and get some guidance and ideas on how I could achieve the following goals:

1- Use internet explorer at work to connect to some kind of server I have set up on my home computer.

2- Log in to a dedicated user with stripped-down permissions

3- Use terminal to issue commands and launch programs

4- Being able to leave selected programs running even after I am not logged in anymore from the work pc.

Note: I don't necessarily need a graphical interface. I would be happy just doing shell stuff...

So if any of you have any ideas on the subject or any links to how-tos, I would really greatly appreciate!

Thanks very much for your time and trouble!

Norm

---

### Post by Delkster on 2006-07-02
There are some kinds of SSH clients written as Java applets. If you can run those in your browser, perhaps you could use one to connect to your Linux box.

As for leaving (console) programs running on the remote Linux machine even between logins, check out GNU Screen (in the `screen' package). It's a little tricky but can be quite useful.

---

### Post by sumadartsan on 2007-12-20
If you set up a Web server on your computer, you can install PHPShell in one of your web accessible locations.  It's not nearly as pretty or effective as a regular shell, but it is useful.

---

