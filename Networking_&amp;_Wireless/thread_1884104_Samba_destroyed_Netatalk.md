---
title: "Samba destroyed Netatalk"
date: 2011-11-20
forum: Networking &amp; Wireless
---

### Post by danielwinter on 2011-11-20
Hey there!
I'm a pretty Ubuntu Noob and set up my Ubuntu 11.10 64bit on my little HP ProLiant to use it with my OSX 10.7 MBP along with timemachine.

I set it up with netatalk 2.2.1 and did a pretty well job, it worked now for 4 weeks without any problems.

2 days ago I installed SAMBA to use file sharing along with my bluray player. As it turned out, the player can't access my samba share, although a win7 pc and my osx could find it and had access onto it. anyway, I gave up the idea with the player and forgot that thought.

Today I wanted to connect with my OSX again, but there was this little shocking message: While the avahi daemon brought my netatalk volume and the sambashare onto my macbook, i couldn't access the netatalk share. It simply said "not connected", if i tried to connect anyway, it says "There was a problem connecting to the server “TMServer”. Check the server name or IP address, and then try again. If you continue to have problems, contact your system administrator.".
But I could still connect to the samba share!

Now here are the steps I took:
-checked IP adress
-tried to connect onto the AFP-share from ubuntu itself without success
-apt-get remove samba
-checked all the conf files of netatalk, all are still ok
-tried via "connect to server" instead of using the avahi shortcut
-rebooted the server for a about a hundred times
-restart netatalk service after boot
-restart avahi daemon after boot

everything with no success or being ok (the check of the files)
any idea what is wrong or what I could do?
Oh yeah, and one more thing: If I type in a wrong password in OSX, the window shakes (meaning the usr/pwd is wrong, for the non-OSX guys out there :) ), but if I enter the correct usr/pwd, I get the error message mentioned above.

And sorry if this is the wrong forum or if the question was asked before, but I couldn't find any answers within my 2 hour search.

Hope to hear from you guys!
Daniel

---

### Post by danielwinter on 2011-11-21
has noone an idea? :/

---

### Post by danielwinter on 2011-11-21
found the solution!!!


1. Format the partition with ubuntu
2. Install openSUSE


TATATAAAAA!
There you have it!


Thanks for the millions of users out there who helped me, I really appreciate that :)

---

