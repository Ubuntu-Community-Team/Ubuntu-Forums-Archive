---
title: "eth0 won't enable"
date: 2006-02-03
forum: Networking &amp; Wireless
---

### Post by Hushpuppy on 2006-02-03
Hi,
Ubuntu noob here.  23 years working on UNIX, 8 years or so on Linux.

...So I've installed Ubuntu (5.10) but basically skipped over the networking part because I'm behind a firewall and don't expect it to work, I'm thinking I'll go home and do it but lo and behold as part of the install I discover apt-get works through a proxy &ct &ct.

Bottom line is, I didn't set my networking, but I DID use the network to install Ubuntu because I exited to a shell and started it up manually at some point in the installation process.  (just before I realized I was going to be apt-get'ing).

In any event, when I am using the KDE Systems Settings applet, and clicking on Network Settings, my eth0 device comes up Disabled.  I click on Enabled and it shows enabled for about 5 seconds, then it shows disabled again and stays there.

/etc/network/interfaces is essentially empty.  I don't know what application I can use to  fill it up.  I can do it by hand, I suppose, but doesn't Ubuntu have the capability to set the network device up during install?  (Yes it does).  So how could I do it?  (Without writing my own network script in /etc/init.d).

BTW, the network card is some Intel thing.  I've been using it for years in Redhat and Suse Linuces.  It works under Windows (dual-boot).  There are no strange errors under dmesg or /var/log/messages.  I can configure it manually with ifconfig and route commands; so the card is fine.

Thanks for the help.

---

### Post by GTvulse on 2006-02-03
Hi,

well you will need to do it by hand AFAIK, but the procedure is pretty well documented in interfaces(5) and ifconfig( 8 ). :-)

---

### Post by Hushpuppy on 2006-02-03
With all due respect, why?  If Ubuntu has a utility that configures eth0 upon startup, why do I need to go in with vi/emacs/whatnot and edit files?  Is there no utility for doing so once the machine is up and running?  I'd like to use Ubuntu and not have to administrate it (ie, learn about things like /etc/network/interfaces).  That's my day job :-).

---

