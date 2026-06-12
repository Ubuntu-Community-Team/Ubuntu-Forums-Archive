---
title: "no tuner setup"
date: 2010-11-11
forum: Mythbuntu
---

### Post by kasulstyls on 2010-11-11
Hi,

  I dont have a tuner as I watch most with Hulu/netflix and dvd on pc. I up graded to .24 and the backend is unable to connect. On Mythbuntu site, it says you can setup a dummy tuner on the backend because now it needs this to start ( didn't on the previous ). I noticed a tuner called demo but it needs a file. What file can I give it? Is there a link for me to download a certain type of file for this?

Thanks in advance
Kas

---

### Post by tgm4883 on 2010-11-11
I believe you can set a blank file or set it to any video file

---

### Post by kasulstyls on 2010-11-12
tgm4883

  Thanks for the reply. I will try this when I get home and post my results.

Kas

---

### Post by kasulstyls on 2010-11-13
ok,

  I did a touch for a mpg with no luck. I also tried my ripped movies with no luck. I downloaded a mpg file from the blender website and the backend is not able to start.  

  I check my IP, changed the connections to localhost, all I get is unable to connect to host IP/localhost on port 6543.  The login and pass on mythconverge is the same for the frontend.

any ideas besides going back to .23.1

---

### Post by tgm4883 on 2010-11-13
You will have to post your backend logs, it could be a different reason that it isn't starting

---

### Post by kasulstyls on 2010-11-14
tgn4483,

   Below is my log for my backend. First line says that my backend is still on 23 fixes branch. I remember the front end saying that it needs to upgrade and I let it go through the process. I guess my next question is how to I get the backend to .24 


=== MythtV Backend Log ===
2010-11-11 17:13:18.026 mythbackend version: branches/release-0-23-fixes [24158] [www.mythtv.org](www.mythtv.org)
2010-11-11 17:13:18.112 Using runtime prefix = /usr
2010-11-11 17:13:18.210 Using configuration directory = /home/mythtv/.mythtv
2010-11-11 17:13:18.631 Empty LocalHostName.
2010-11-11 17:13:18.727 Using localhost value of gia
2010-11-11 17:13:19.851 New DB connection, total: 1
2010-11-11 17:13:20.121 Connected to database 'mythconverg' at host: localhost
2010-11-11 17:13:20.224 Closing DB connection named 'DBManager0'
2010-11-11 17:13:20.290 Connected to database 'mythconverg' at host: localhost
2010-11-11 17:13:22.100 Current MythTV Schema Version (DBSchemaVer): 1254
2010-11-11 17:13:22.320 MythBackend: Starting up as the master server.
2010-11-11 17:13:22.530 New DB connection, total: 2
2010-11-11 17:13:22.608 Connected to database 'mythconverg' at host: localhost
2010-11-11 17:13:22.771 MythBackend, Error: No valid capture cards are defined in the database.
                        Perhaps you should re-read the installation instructions?
2010-11-11 17:13:25.422 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-11-11 17:13:25.656 Enabling Upnpmedia rebuild thread.
2010-11-11 17:13:26.045 QMulticastSocket: setsockopt - IP_ADD_MEMBERSHIP Error
2010-11-11 17:13:28.089 Main::Registering HttpStatus Extension

---

### Post by tgm4883 on 2010-11-14
Enable auto-builds on the backend and select 0.24. Update as usual

---

### Post by kasulstyls on 2010-11-14
tgm4483,

  I have enabled the .24 which lead me to this issue. Just encase, I did recheck that it was selected and checked update manager for any type of updates. So far nothing.  My frontend wont work due to the backend not being of the same version. I have tried clean install from 10.04LTS /.23 to 10.04/.24 with the same results. I even used the my old machine with a tuner card and installed same 10.04LTS/.23 to .24, check the log and with same version stated. Upon starting mythfront end, it also advised of the db needing to be upgraded, I did so and now it asks " choose location & language " then fails to connect to backend. 

So, for me, i have the same issue on my laptop ( no tuner card ) and my old system ( with tuner card ) 

Any other way to force the backend to update?

I guess I could download the latest release 10.10 which will default to .23.1 and upgrade to .24. ---- I will give that a try, possible I could be doing something wrong while updating from .23 to .24

---

### Post by tgm4883 on 2010-11-14
> **kasulstyls said:**
> tgm4483,

  I have enabled the .24 which lead me to this issue. Just encase, I did recheck that it was selected and checked update manager for any type of updates. So far nothing.  My frontend wont work due to the backend not being of the same version. I have tried clean install from 10.04LTS /.23 to 10.04/.24 with the same results. I even used the my old machine with a tuner card and installed same 10.04LTS/.23 to .24, check the log and with same version stated. Upon starting mythfront end, it also advised of the db needing to be upgraded, I did so and now it asks " choose location & language " then fails to connect to backend. 

So, for me, i have the same issue on my laptop ( no tuner card ) and my old system ( with tuner card ) 

Any other way to force the backend to update?

I guess I could download the latest release 10.10 which will default to .23.1 and upgrade to .24. ---- I will give that a try, possible I could be doing something wrong while updating from .23 to .24

On the backend that won't update, post the output of this

```
dpkg -l myth*
```

---

### Post by kasulstyls on 2010-11-15
tgm4483,

   Lets chalk this one up to user error and unable to follow directions.  Upon adding it to the demo, what I didn't do was keep going as I had a regular tuner. After creating a fake video source, and fake input connection with a fake channel to start on, the connection to the db worked fine. I only thought that I had to just point the demo tuner card to a mpeg file that was it. Also, if I would have scrolled down to the very bottom of the backend log file, I would have seen that the db did update to .24 version. While it was constantly outputting to the log because of my non follow through, I had a lot to scroll through and quite before the end. 

Thanks for help and sorry for any time wasted. consider me resolved sir.

Kas

---

