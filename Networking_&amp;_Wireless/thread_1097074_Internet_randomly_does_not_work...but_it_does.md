---
title: "Internet randomly does not work...but it does"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by Tykin on 2009-03-15
Hi. Ever since I've had Ubuntu, I've had a problem where the Internet randomly cuts out and randomly comes back. When this happens, I am unable to search the internet using firefox (nor the epiphany browser). 

I always simply assumed that my service provider did not like linux and randomly cut it off.

However, I found out today that I * still* have the internet. I was using Pidgin for the first time today and was able to continue to chat with people while my browsers were no longer working. After a random amount of time ( 20 minutes, I think), the internet was once again working. During this time, I did not change any settings or do anything differently.

So, my internet is still technically working but the browsers don't. I've also noticed that I can receive notices of things that need updating, but I cannot download updates.

Is there anyone who can help me?

---

### Post by sanderj on 2009-03-15
Open two terminal-windows. In terminal 1, run "ping www.google.com". In terminal 2, run "mtr www.google.com". Keep them running.

As soon as your browser is not working anymore, have a look at terminal 1: is there still a ping coming back from [www.google.com?](www.google.com?) If not, check in terminal 2 where the link is broken.


And: are you using a web proxy? Check in Firefox: Edit -> Preferences -> Advanced -> Network -> Connection/Settings.

---

### Post by Tykin on 2009-03-17
Thanks for the reply. I've been pinging google for awhile now, but like most things in life, the problem seems to go away once I ask for help. 

However, I did see that the proxy was set to "Use System Settings." I changed it to auto-detect. Could this have been the problem? Just for full disclosure, my apartment provides the broadband connection.

I'll let you know if anything changes. Thank you for the help.

---

### Post by aaronLund on 2009-03-17
I've  been having this same issue (wired not wireless) and it's been driving me crazy.

Totally unpredicatble as to whether or not i'll actually get to the page I want.

The fact that there's a bug in 8.10's "network connections" icon (i.e. a constant red, exclamation point over the icon in the toolbar) does not make matters any easier.

This has just recently started happening too.  I was a happy ubuntu user a week ago.

---

