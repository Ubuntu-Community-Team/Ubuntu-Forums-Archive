---
title: "FUPPES autostart?"
date: 2008-06-28
forum: Multimedia Software
---

### Post by fghj. on 2008-06-28
Is there anyway to make fuppes start, when i start the computer? I tried to put the commando "sudo /etc/init.d/fuppes start" in the sessions thing in System, but that didn't work.

---

### Post by thomascrabs on 2008-07-22
Sorry if this is hijacking your post but I am having a similarish problem. I have added a script in /etc/init.d (see attached) called 'fuppesd' and then used the following command to add it to start up:

sudo update-rc.d fuppesd defaults

No expert on this but this adds copies of the above script to start and stop when the system starts and shuts down respectively. 

Have a look at this...

[http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)


My problem is that even though the service is running I cannot get onto the webservice that runs and my PS3 can't see it. If I start the service myself when logged on it works. Anyone any thoughts? :confused:

---

### Post by thomascrabs on 2008-07-24
Any luck... have you tried just adding the command 'fuppes' to you sessions preference instead of using init.d scripts?


Turned out my problem was that my wireless card wasn't getting an IP address during boot as it was in roaming profile. Used a static address and it worked fine.

---

