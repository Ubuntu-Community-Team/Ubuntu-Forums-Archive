---
title: "Network Connection Becomes Disabled"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by tonyray on 2011-08-07
I've been searching for answers to this issue for a couple years now.  Haven't found the answer yet, and it's starting to really get annoying, so I figure I might as well ask for help.

I have Ubuntu Server set up and running with no gui, and every once in a while it appears the network connection either disconnects/disables itself/blocks all connections?  I'm not totally sure what exactly is happening (which is probably why I haven't been able to find a solution).

Here is the situation.  Whenever I am doing any sort of large file transfer to/from the server (either on my local network or remotely via ssh), the connection is dropped and I cannot reconnect to the server.  The only way to get it back is to either reboot, or (the much easier/somewhat confusing method) touch a key on the keyboard to fix it.

Lately, however, it hasn't been limited to just during large file transfers.  I will leave it sitting idle overnight, wake up and notice that I cannot connect to the server.  Once again, hitting a key on the keyboard fixes the issue.

I have tried looking in the logs to find some sort of hint as to what is going on, but no luck so far...  My biggest suspicions are either the firewall (UFW) suddenly blocks all traffic or there is some power management thing going on.

Has anybody ever heard of / experienced anything like this?

Looking for some guidance :)

Thanks
-Tony.

---

### Post by tonyray on 2011-08-23
Bump?

---

### Post by Iowan on 2011-08-23
I haven't experienced it, but it *does* sound like a power management issue - especially if hitting a key fixes it. I presume you've already checked the BIOS settings...

---

### Post by tonyray on 2011-09-03
Well, not exactly sure how I fixed it (I've tried several things so many times...), but it's been 5 days and it's been connectable the entire time. So I've marked this as closed.  Let's hope it doesn't revert...

---

