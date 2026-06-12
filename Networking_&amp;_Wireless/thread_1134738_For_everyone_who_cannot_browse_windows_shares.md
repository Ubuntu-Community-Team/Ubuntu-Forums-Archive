---
title: "For everyone who cannot browse windows shares"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by conorturton on 2009-04-23
(Please indicate if this works for you. If the percentage is high enough, could the maintainers add the fix?)

FOR EVERYONE WHO CANNOT BROWSE WINDOWS NETWORK SHARES....

OK, while trying to find out why smbtree listed an external IP address then came up with a NT Authentication error after it, I think I may have stumbled on the fix for the windows network share browsing.

OK....

Open up /etc/nsswitch.conf

Look for the line...

hosts:          files (etc)

If yours is like mine was when it didn't work, it'll read something like:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

..although what is there will vary but files and dns will be there.
What is missing is an entry for wins.

You need to add wins after files so it looks like (alter as required):

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4


Since I did that, the moment I rebooted and went to Places, Network, my Windows desktop showed up straight away with the WORKGROUP next to it. When I click on the computer, the password dialogue box comes up and once entered, all the shares are listed. I can now add a printer as well.

WOOOOOHOOOOOOOOOOO

---

### Post by Ariful on 2009-04-23
ill try to test to see if this works... once i get 9.04

---

### Post by keithce on 2009-04-24
I am using a 9.04 (Official Release)

I am able to connect to my Windows Server 2008 just fine because I've created the samba/NFS shares and it allows to be do that.

However I am still unable to connect to my Windows 7 Build 7068 desktop.

Thanks for trying though.

---

### Post by Deamos on 2009-04-24
I have been having this issue for more than just Jaunty.  I appreciate the help!

---

### Post by Kaisersoze on 2009-04-24
Unfortunately it doesnt work with me...

Using Ubuntu 9.04 now...

---

### Post by conorturton on 2009-04-24
Sorry everyone...forgot to add that you need to install winbind


sudo apt-get install winbind

---

### Post by Dirigo on 2009-04-25
I NEED A TAKE-BACK !!!!

When I 1st saw this solution, I tried it, but nothing, so I answered sorry, but no...

Just for the heck of it, I re-tried going in through Nautilus again.  

I'm now happily listening to Santana from my Windows XP box, changed my desktop background to a vacation picture in my shared pictures folder and I successfully printed a test page to my printer!!

I haven't been able to do this for a few upgrades (I think since 7.10).

THANKS VERY MUCH!!

---

### Post by conorturton on 2009-04-25
You're welcome. Takes a couple of minutes for the changes to register in Nautilus for some reason. I just logged out and back in again whenever I made a change to the /etc/nsswitch.conf file.

---

### Post by ElEdwards on 2009-04-25
YAY!!!!  It works!

---

### Post by Sef on 2009-04-25
Locked.  [Duplicate Thread]("http://ubuntuforums.org/showthread.php?p=7137547#post7137547").

---

