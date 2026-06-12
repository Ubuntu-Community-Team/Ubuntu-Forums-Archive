---
title: "Is it normal to have to run myth setup after every restart?"
date: 2007-12-16
forum: Mythbuntu
---

### Post by butthash on 2007-12-16
After every restart when I go to watch tv I get an error that all inputs are used for current channel. If I rerun mythtv setup, don't change anything, and let it run mythfilldatabase then I can watch channels again. Is this normal?

---

### Post by milhouse on 2007-12-17
> After every restart when I go to watch tv I get an error that all inputs are used for current channel. If I rerun mythtv setup, don't change anything, and let it run mythfilldatabase then I can watch channels again. Is this normal?

As you probably suspect. No.

Hopefully someone can give you some more information to go on so you can track down the issue.

---

### Post by superm1 on 2007-12-17
Start out by looking over your logs upon a fresh reboot.  /var/log/mythtv/* is where we want to see.

---

### Post by hkazemi on 2007-12-18
Are you using an HDHomeRun tuner?  If so, there is a problem with how mythbackend looks for it after a reboot.  I ran across this problem with Mythbuntu 7.10 and found that it is not limited to Mythbuntu in particular, but to many current MythTV distros.

I posted this in the silentpcreview.com forums:
HDHomeRun and MythTV had some timing issues preventing mythtv-backend from seeing the HDHomeRun after rebooting. This may be resolved by lengthening the delay between Linux activating the network and the launching of the mythtv-backend script (in /etc/init.d/). I edited the mythtv-backend script to add a 'sleep 10' after the DESC= line. I also used 'update-rc.d' to move mythtv-backend from S24 to S90 using the commands:
Code:
sudo update-rc.d -f mythtv-backend remove
sudo update-rc.d mythtv-backend defaults 90 16

Adding a sleep 5 or sleep 10 command to mythtv-backend script can also give the system more time to find the HDHomeRun.

More on this issue here:
[http://www.silicondust.com/forum/viewtopic.php?t=4571](http://www.silicondust.com/forum/viewtopic.php?t=4571) 
[http://www.gossamer-threads.com/lists/mythtv/users/298891](http://www.gossamer-threads.com/lists/mythtv/users/298891) 
[http://www.mythtvtalk.com/forum/viewtopic.php?t=6898](http://www.mythtvtalk.com/forum/viewtopic.php?t=6898)

---

### Post by butthash on 2007-12-18
I do have the HDHomeRun. I will try your suggestion. Thanks.

---

### Post by butthash on 2007-12-18
I added a 10 sec delay in the init script and used update-rc.d to move the load time and everything seems to work fine right after start up.

Thanks for your help.

---

### Post by poerschr on 2008-01-04
I have this same problem.  I have attempted to follow the advice of the users here, but with no luck.

It seems like there are three solutions:

SOLUTION #1
Looking at the threads in the other forums, I noticed that sections of the mythtv-backend were rewritten with different code.

Such as here: [http://www.silicondust.com/forum/viewtopic.php?p=25925&sid=5ab44d152c66bea6fe6d6ac45639bea5](http://www.silicondust.com/forum/viewtopic.php?p=25925&sid=5ab44d152c66bea6fe6d6ac45639bea5)

SOLUTION #2
In this thread it was simply recommended to add 'sleep 10' after the DESC= line.  

SOLUTION #3
Changing the the order of the mythtv-backend script to a later order, such as S90.

For solution #1, could someone also explain more detailed exactly where to add the 'sleep 10' command?

For solution #2, could someone explain exactly where to add the new code?  Should I rewrite it over the code is already there?

Thank You

---

### Post by poerschr on 2008-01-06
Anyone willing to chime in?  I simply need a bit more guidance..

---

### Post by PacketBoy on 2008-02-29
> **hkazemi said:**
> Are you using an HDHomeRun tuner?  If so, there is a problem with how mythbackend looks for it after a reboot.  I ran across this problem with Mythbuntu 7.10 and found that it is not limited to Mythbuntu in particular, but to many current MythTV distros.

I posted this in the silentpcreview.com forums:
HDHomeRun and MythTV had some timing issues preventing mythtv-backend from seeing the HDHomeRun after rebooting. This may be resolved by lengthening the delay between Linux activating the network and the launching of the mythtv-backend script (in /etc/init.d/). I edited the mythtv-backend script to add a 'sleep 10' after the DESC= line. I also used 'update-rc.d' to move mythtv-backend from S24 to S90 using the commands:
Code:
sudo update-rc.d -f mythtv-backend remove
sudo update-rc.d mythtv-backend defaults 90 16

Adding a sleep 5 or sleep 10 command to mythtv-backend script can also give the system more time to find the HDHomeRun.

More on this issue here:
[http://www.silicondust.com/forum/viewtopic.php?t=4571](http://www.silicondust.com/forum/viewtopic.php?t=4571) 
[http://www.gossamer-threads.com/lists/mythtv/users/298891](http://www.gossamer-threads.com/lists/mythtv/users/298891) 
[http://www.mythtvtalk.com/forum/viewtopic.php?t=6898](http://www.mythtvtalk.com/forum/viewtopic.php?t=6898)

Thanx butthash! Fixed my problem quick. I love this HDHomeRun box!

---

### Post by jason456 on 2008-03-17
I've been scratching my head on this for a while.  Glad I found this post.  Instructions above worked great.  Thanks.

---

