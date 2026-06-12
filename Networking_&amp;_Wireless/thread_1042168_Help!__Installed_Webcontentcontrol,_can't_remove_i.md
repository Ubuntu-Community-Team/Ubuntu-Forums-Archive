---
title: "Help!  Installed Webcontentcontrol, can't remove it, now port 5500 is blocked!"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-01-17
Doing a little research for a client of mine who has an autistic kid, I went hunting for a web content filter for firefox and decided to download a program called webcontentcontrol, per the suggestions of [this thread]("http://ubuntuforums.org/showthread.php?t=1039557").  I didn't spend more than a couple minutes testing it to determine that I like how quick and painless the installation of the program was.

But I don't personally want a content filter on my PC.  Removing the software has been anything but painless.  In fact it's still stuck on my machine.  Following the instructions given at the same thread above, this is the output I got:

```
user@userpc:~$ sudo dpkg -r webcontentcontrol
(Reading database ... 137435 files and directories currently installed.)
Removing webcontentcontrol ...
prerm remove|deconfigure called
Unconfiguring dansguardian+firehol+tinyproxy
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
 * Stopping Firewall firehol                                             [ OK ] 
Stopping tinyproxy: tinyproxy.
 * Stopping DansGuardian dansguardian                                    [ OK ] 
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
All OK! Everything was stopped
Running from /home/user
===>importing /usr/share/webcontentcontrol/backup.dgs.full
tar: /usr/share/webcontentcontrol/backup.dgs.full: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dpkg: error processing webcontentcontrol (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 webcontentcontrol
user@userpc:~$
```

Now I'm attempting to VNC into my system from another PC and I can't.  I have a gut feeling this software (likely the firehol firewall, maybe the tinyproxy) is either blocking access or has modified my iptables to reject incoming packets for port 5500.  This is just a theory at this point.  I'll be taking my laptop home to port forward to it instead of my PC as usual so I can be 100% certain about whether or not installing this software that doesn't want to be removed is causing this problem.

I was wondering if anyone knows about dansguardian, tinyproxy or firehol and know of any other method to work around this short of successfully pulling the webcontentcontrol package (and it's aforementioned dependencies) off.

---

### Post by diablo75 on 2009-01-17
Just wanted to add that I took my laptop home and changed my port forwarding setting to point to the laptop instead of the PC, and then retrying a connect over the Internet worked.  So I'm now 100% certain it's this software that's blocking my access on my PC.

---

