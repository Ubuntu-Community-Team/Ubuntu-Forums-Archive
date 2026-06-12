---
title: "Lost internet connection after upgrade to Jaunty"
date: 2009-04-28
forum: Networking &amp; Wireless
---

### Post by wgscott on 2009-04-28
I upgraded (using apt-get) to Jaunty and lost the ability to connect to the internet upon booting.

Booting off of a Jaunty demo CD doesn't cause this problem, and I eventually found I could restore internet connections until reboot using  the "ifconfig" and "router" commands, so I don't think it is a driver issue (I could be very wrong since I don't know anything about this).  When I try to use the network config gui, the fields accept input but nothing gets saved, and there is no prior information.

Everything just worked on upgrade from breezy through all the other releases until now, fwiw.

I could put the ifconfig and router commands in the startup script, but would rather not mess things up.

I have a static IP address, but normally it would be acquired through the dns upon booting.

Suggestions?  What file should correspond to the Network preferences gui? Maybe that got corrupted.

---

### Post by adampope on 2009-04-29
Bump! This issue has been reported by a number of users and no easy solution is available. :popcorn: until one arrives!

There must be many more who give up and don't post since they ...err... can't without a network connection!

---

### Post by lunanueva on 2009-04-29
I'm having a similar problem after upgrading to jaunty from ibex.  I have an internet connection and can install things from the repositories and download upgrades, but firefox and evolution aren't responding.  I installed 'firefox launchpad' from the add/remove list and it got firefox running, but incredibly slow.  So slow that that web pages won't even load all the way, then eventually expire.  ?????

I'm thinking of doing a fresh jaunty install, since I've been unable to find any answers in the forums.  I'll post my results.

---

### Post by Mugsy323 on 2009-05-08
> **lunanueva said:**
> I'm thinking of doing a fresh jaunty install,
Just to let you know, I installed Jaunty with a full reformat and it made no difference.

I was able to connect once using pppoeconf, then never again (tried "pon dsl-provider" as well).

I configured my DSL connection under the "Network Connections" app, but it made no difference (and it refuses to save my settings if I check "Available to all users" box).

I'm more likely to reinstall Ubu8 until someone finally posts a fix that works. :(

---

### Post by lunanueva on 2009-05-10
Decided to go back to Ibex for now.  Hopefully i'll be able to upgrade to Jaunty when there is a solution to this problem.  

Thanks for your responses.

---

### Post by Mugsy323 on 2009-05-13
I was able to get my DSL connection working only after reinstalling Jaunty and doing the following:

*******************
Notes:
1) The word "never" that appears after your connection in the Connections manager describes "the last time you were connected". When you are connected, it will change to "Now". When you disconnect, it will report how long it has been since you last connected.

2) Jaunty now uses a built-in "Network Connections" app on the toolbar to manage your network (presumably so you can now have more than one), so if you used "pppoeconf" to setup your DSL, you're already doomed (they conflict). But before you go through the pain of reinstalling, try deleting the config file pppoeconf creates before going through the extreme step of reinstalling Ubu9 from scratch. Then set up your DSL the "proper" way via the NC app (on the toolbar). If that works, let us know.
********************

Upon reinstalling Ubu, right-click the "Network Connection" icon (toolbar) and then "Edit connection". Click the DSL tab and enter your username and password (I don't know if it matters, but I entered my ISP's .com name on the "Service" line.) Check "Connect automatically" and change the name of the connection to something you'll recognize. Close the app.

Left-click the "Network Connection" icon and the name you gave your connection should now be listed. Click it to get online. The icon should change to show two rotating arrows while it tries to connect. Once it does, the icon will change to the standard small "double monitor" connection icon you're familiar with.

I'm typing this from memory, so let me know if I've forgotten/missed anything.

Addendum: Oh, I just remembered, Jaunty uses this new method so it can store your Inet password in it's "keyring", so when you reboot and it tries to connect, Jaunty will prompt you for your (keyring) password. Currently, there is no fix for this annoyance, but the issue has been reported and escalated.

---

### Post by extremizt on 2009-05-14
I had this same problem. Was not able to connect to internet after upgrade to Jaunty, eventhough i was getting ping replies from router. I got it back when i did the follwing.

```
sudo dhclient -r
```   It releases ip back to the pool.

```
sudo dhclient
```      Restarts dhcp

I have to do this every time to get the net connection. Hope it works for you as well.

---

### Post by Andre_3608 on 2009-09-02
Sincere thanks for your system-saving tip.  Thought I qwas done for in Ubuntu!

---

### Post by bayvista on 2009-10-28
Many thanks for this. I did not neet to reload Jaunty. However, my Network Manager shows no connection. However, I am now connected to the Internet and my local network. I do wish the developers of Ubuntu would warn us of these changes. I have just wasted a day searching and trying all suggestions to find your fix, Losing the Internet is like having a car accident. Many days of anguish.

Thanks again.

:p  :popcorn:  :p

---

