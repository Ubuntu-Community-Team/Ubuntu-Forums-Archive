---
title: "netbeans (java?) system logout"
date: 2011-03-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by daemonk on 2011-03-26
Hi all,

Since today’s update I have a strange thing happening when I do a subversion action through netbeans.

Each time I right click a file in netbeans go to subversion and click update or commit the system immediately logs out and I have to log in again.

All running applications are closed and connections reset, looks like I have just booted when looking at the processlist.

I am pretty sure there has been no netbeans update, so I am confident this is something ubuntu that is causing this. Seeing as netbeans is running on java I am heading towards that as a cause.

I have and can successfully use SVN command from the terminal so am sure it is not the SVN actions that cause it. 

The whole log out is very fast, I am surprised even that all the applications I was running could terminate that fast.

If you could please give me some idea on how to better debug this, I will gladly work with you to see if this is an alpha issue.

Many thanks
D

---

### Post by r-senior on 2011-03-26
Just tried working with Subversion through Netbeans here and all is well.

Do you have any log files from a JVM crash in your home directory?

Have you looked at the logs in /var/log to see if there are any clues?

Failing that I'd try running Netbeans from a terminal. Make it blow up and see if it produces any error messages.

---

