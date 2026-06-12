---
title: "Can't get Mythbuntu to install correctly"
date: 2013-11-24
forum: Mythbuntu
---

### Post by bigjohn992 on 2013-11-24
I'm a newbie to Mythbuntu.  I downloaded Mythbuntu 12.04.3 to a DVD and then installed it in the simplest configuration: front end and back end on same machine.  I followed the "MythTV Quick Start Guide" instructions.  The entire disc was dedicated to it (no partitioning).  After loading the front end with no problems, I went to load the back end and saw that there were numerous updates available. I decided to load all of the updates before proceeding with the back end.  My machine hung up when it was installing the updates.  I tried reloading a second time with the same results.  I even let it run overnight with no luck.  I then tried to exit the process and got a message saying that it was only able to do a partial install.  I tried to continue and then got a message: "Unable to get exclusive lock.  This usually means that another management application (like apt-get or aptitude) is already running.  Please close that application first".  I have no idea what this message meant or what to do about it, so I just continued setting up the back end.  I have a Hauppage 950Q tuner stick (nothing weird).  For some reason the back end won't recognize it.  I have re-booted the machine with no luck.  I'm trying to figure out where to go from here.  I would appreciate any help I can get.

---

### Post by GaryP2 on 2013-11-24
I used to use the Update Manager GUI to do all my updates – until I installed 12.04 about a year ago. I had similar issues to what you’re describing and have since switched over to using command lines to apply updates. If you do some searching you’ll find others will recommend applying updates through the command line as well.

The process is to open a terminal session, and then issue these commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by bigjohn992 on 2013-11-26
Thanks - I did as you instructed and everything works now.

---

