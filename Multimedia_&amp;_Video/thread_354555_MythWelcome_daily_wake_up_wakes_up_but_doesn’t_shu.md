---
title: "MythWelcome daily wake up: wakes up but doesn’t shut down"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by Roebi on 2007-02-06
Hello, 

I have recently set up a frontend/backend combined system, based on Ubuntu 6.10 and build from the available official Ubuntu repositories. 

I am using automatic shutdown and wake up based on nvram-wakeup and MythWelcome for scheduled recordings. 
Automatic wake up and shutdown works perfectly – no problem there. When the PC boots up automatically to record a show, it will only launch MythWelcome; when I boot it up manually, it will boot up to MythWelcome and automatically start MythFrontend – all as it should be. When in MythWelcome and idle, the system will start the countdown and shutdown after having set the next wake up time. 

Since I live in Belgium, I collect all data for the EPG via an external script. It runs the JXMLTV grabber and then updates the database with a ‘mythfilldatabase --file’ command. For this I have configured MythWelcome to wake up at 3:00AM, and then a cron job with my script starts at 3:10. MythWelcome is set to shutdown at 3:45. 

But every morning I find my PC still running. It indicates that it is idle, but is not shutting down. When I look into the logfiles of the EPG script, it has run successfully and all data is fed into the MythTV database. The backend status confirms this.  
So I don’t know what is going wrong. 

Can someone point me into any direction in order to find out what is going wrong? 

I just learned that the command ‘mythshutdown –s’ returns the current status of the system. I have not checked this when I get up in the morning, but I suppose it will indicate “64”, i.e. in a daily wakeup/shutdown period. Can I set/change that status via the command line? I know I can (un)lock it. I could include a line in the EPG script to change the status to “0” (idle) at the end of the script. I realise this can be dangerous, but I am fairly confident that around 3:00AM the machine is normally not doing anything else. 

Otherwise, one of the entrees in the MythWelcome menu is ‘Run mythfilldatabase’. Can the code of this command be changed in order to point to the script? Remember I installed from packages, not from source. 
I wouldn’t mind updating the EPG this way, if the problem above cannot be solved. 

Thank you in advance for your input. 


Roebi

---

### Post by kingborel on 2007-06-13
Just had the same problem, although it might be a bit late ;) The reason it doesn't shutdown is because it has a frontend connected to it. You need to checkout MythWelcome 

[http://www.mythtv.org/wiki/index.php/Mythwelcome](http://www.mythtv.org/wiki/index.php/Mythwelcome)

---

