---
title: "How do I find out whether the database has been upgraded to 0.22?"
date: 2009-11-13
forum: Mythbuntu
---

### Post by Johan73 on 2009-11-13
Hi,
 
Until a couple of days ago, I was happily running Mythbuntu 9.04 with mythtv 0.21 and the VDPAU packages enabled. However, things strated going wrong a couple of days ago when I did a standard system update which caused neither the front-end, nor the mythweb interface to come up. I have to admit that I did not pay close attention to what was being updated and should noticed the change.
 
After some checking, I noticed that mythbuntu had been upgraded from 0.21 to 0.22. As I didn't immediately know how to resolve the problem, I decided to make the leap and upgrade the entire system to 9.10 through a network upgrade in the hope that this would fix the problem.
 

The upgrade itself went very smoothly, but I am still having the same problems. 
[LIST]
[*]Mythfrontend is not loading - when starting mythfrontend it shows a background for a while, but does not have any progress bar and eventually mythfrontend exits / appears to crash
[*]The Mythbackend log shows many database-related errors. Interesting enough, though, it did properly record a scheduled show last night.
[*]Mythweb gives an errormessage that the data directory is not readable, even though I did not change any file permissions
[/LIST]In addition to the above, the system looks very different - the mythfrontend background and mythbackend have a very greenish color (previously was blue on my system) and the Desktop has diagonal white strips on it (previously it was just black). I am not sure if that is normal or if there is something wrong?
 
I am at a loss on what is causing these problems and how to resolve them. Seen the fact that there are so many database-related errors in the mythbackend log, I suspect there is a problem with the database. How do I verify whether the tables have been upgraded properly to 0.22 tables? Is there anyway to safely rerun the database migration scripts to migrate from 0.21 to 0.22?
 
I could reinstall mythbuntu 9.10, but am concerned that my backup, which I only took after the update, but before the upgrade, may also have the same problems and therefore doubt this will resolve anything.
 
Any other advise on how to proceed is appreciated. Also, are these colours I am getting normal behavior?
 
I attached the relevant parts of my mythbackend.log and mythfrontend.log files.
 
Thank you much for your help!
 
Johan

---

### Post by Johan73 on 2009-11-14
I eventually managed to get this to work.

I compared an old backup I had with a recent backup to check whether the database structure had changed, which it had, and therefore I assumed the database upgrade had worked. I then follwed Nerver's instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1302135") to reload the database.  

This solved the problem with all the back-end errors. The front-end still did not start up properly, though. I found out in Synaptic that I still had one of the 0.21 plug-ins installed which I fully removed. After that, the front-end started fine.

I also had another problem with Webmyth, which I resolved following the instructions in [this thread.]("http://ubuntuforums.org/showthread.php?p=8315034#post8315034")

---

