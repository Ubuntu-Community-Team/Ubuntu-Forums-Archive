---
title: "Random upload failures via SFTP to headless ubuntu machine."
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by Aacron on 2013-07-13
I used to never have this problem, and I'm not quite sure where it started.  I was running Ubuntu 12.04 LTS Server, and I'm guessing that during one of the updates, this started happening.  I've since done a release upgrade, and the issue persists.

I can connect and transfer to and from the Ubuntu machine fine, except a random wierd error that keeps occurring where the file size reaches a certain point, and I get this in FileZilla:

Command:    open "user@lanaddress" 22
Error:    Server unexpectedly closed network connection
Error:    Could not connect to server

Filezilla asks if I should overwrite (which I do), and it will succeed after some number of retries.  The issue is that this happens from outside the network as well, and since the 'net is much slower than Gb-LAN, this can be quite frustrating for when I'm out and about.

Odd thing is that the file transfers tend to fail at binary numbers.  65535 bytes/kilobytes seems to be the common ones, but there have been other failures that are along other x^2 sizes and such.

Previously this never really happened so I'm guessing something changed in an update.  I've tried the only option I've seen searching on google, which is to reduce to MTU to 1490, but that has not helped any at all.

Does anyone have any ideas on how to diagnose this, or how to resolve it?

Keep in mind that while I did install Ubuntu, I'm generally a "Google 'how to X'" type, and generally while I can edit files, run some fairly basic tools, and in one case edit an init script (with help), I'm still very un-geek when it comes to linux.  I know just enough (with Google behind me) to get a headless server running and serving its purpose, but that is about the limit.

---

### Post by Cheesehead on 2013-07-15
Check /var/log/syslog and /var/log/auth.log on the server around the time of disconnection for clues.
Check /var/log/dmesg on the server for hardware hiccup messages.

---

