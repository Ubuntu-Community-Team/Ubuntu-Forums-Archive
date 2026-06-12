---
title: "XMLTV Error 256 (Not what you might think)"
date: 2008-09-08
forum: Mythbuntu
---

### Post by bergqvistjl on 2008-09-08
Hi, im trying to setup mythtv with xmltv uk_grab_rt (the radio times one) im uptodate (.53) yet when i mythfilldatabase (including with --manual), it hangs for about 10 mins after 'setting up db connection, total 3. after this it says failed xmltv error 256 but then updates the guide data as normal but says some program data may not be availiable. ive searched on the net and the only solution i can find is that it cant detect that im connected to the internet, but this is obviously not the case as it downloads the data (or at least some of it anyway). heres the most recent mythfilldatabase i did. the quotes from it above are not exact, see the code for the correct ones. im running a single combined front + backend system with a single tuner card set up, and im using freeview. 

```
john@john-desktop:~$ sudo mythfilldatabase
[sudo] password for john: 
2008-09-08 12:57:57.898 Using runtime prefix = /usr
2008-09-08 12:57:57.900 Empty LocalHostName.
2008-09-08 12:57:57.900 Using localhost value of john-desktop
2008-09-08 12:57:57.917 New DB connection, total: 1
2008-09-08 12:57:57.924 Connected to database 'mythconverg' at host: localhost
2008-09-08 12:57:57.925 Closing DB connection named 'DBManager0'
2008-09-08 12:57:57.929 Connected to database 'mythconverg' at host: localhost
2008-09-08 12:57:57.935 New DB connection, total: 2
2008-09-08 12:57:57.935 Connected to database 'mythconverg' at host: localhost
2008-09-08 12:57:57.989 Updating source #1 (BBC XMLTV) with grabber tv_grab_uk_rt
2008-09-08 12:57:57.992 Found 38 channels for source 1 which use grabber
2008-09-08 12:57:58.635 Grabber has capabilities: baseline manualconfig cache preferredmethod tkconfig apiconfig 
2008-09-08 12:57:58.985 Grabber prefers method: allatonce
2008-09-08 12:57:58.985 New DB connection, total: 3
2008-09-08 12:57:58.986 Connected to database 'mythconverg' at host: localhost
2008-09-08 13:06:38.923 FAILED: xmltv returned error code 256.
2008-09-08 13:06:41.878 New DB connection, total: 4
2008-09-08 13:06:41.879 Connected to database 'mythconverg' at host: localhost
2008-09-08 13:06:44.107 New DB DataDirect connection
2008-09-08 13:06:44.108 Connected to database 'mythconverg' at host: localhost
2008-09-08 13:06:44.110 New DB connection, total: 5
2008-09-08 13:06:44.110 Connected to database 'mythconverg' at host: localhost
2008-09-08 13:06:44.151 Updating icons for sourceid: 1
2008-09-08 13:07:12.383 Updated programs: 556 Unchanged programs: 13057
2008-09-08 13:07:12.514 Failed to fetch some program info
2008-09-08 13:07:12.515 Adjusting program database end times.
2008-09-08 13:07:12.661     0 replacements made
2008-09-08 13:07:12.661 Marking generic episodes.
2008-09-08 13:07:12.792     Found 6
2008-09-08 13:07:12.792 Marking repeats.
2008-09-08 13:07:12.838     Found 0
2008-09-08 13:07:12.838 Unmarking new episode rebroadcast repeats.
2008-09-08 13:07:12.853     Found 0
2008-09-08 13:07:12.988 Marking episode first showings.
2008-09-08 13:07:16.502     Found 5787
2008-09-08 13:07:16.502 Marking episode last showings.
2008-09-08 13:07:19.810     Found 5787
2008-09-08 13:07:19.812 
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2008-09-08 13:07:19.816 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-09-08 13:07:19.817 Using protocol version 40
2008-09-08 13:07:19.966 Received a remote 'Clear Cache' request
2008-09-08 13:07:19.973 mythfilldatabase run complete.
2008-09-08 13:07:19.973 DataDirect: Deleting temporary files

```

---

### Post by wizgnome on 2008-11-17
I get the same error message, everything appears to work OK and I don't notice any listings missing. Did you find out what causes the message to appear?

---

### Post by EasyRiderOnTheStorm on 2008-11-18
I'm not sure why you would get that error, hopefully it's not that important if everything seems OK otherwise. Still, you might want to try running: ```
mythfilldatabase --graboptions "--debug"
```Yes, with the quotes. That runs the grabber with the debug option, it might tell you some extra details...

---

### Post by Captain_Bodge on 2008-11-22
I'm seeing the same problem. Just posting here so I get subscribed in case anyone finds a solution. If I find one, I'll reply

---

### Post by ian dobson on 2008-11-23
Hi,

Sounds like a permissions problem. How do you run mythfilldatabase (cron,mythtvbackend)?

I saw that the first poster was doing a sudo, which means that the process runs as root, which isn't the best idea.

If your running mythfilldatabase through the backend then try:-

sudo "Mythtv User"
mythfilldatabase 

So that the process runs as the myth user.

Regards
Ian Dobson

---

### Post by Chunder on 2008-11-23
Mine comes up with the same message even though it's run as the usual mythtv user; haven't tried the debug option as I'm gradually losing the will to live getting the right channels and listings to show up properly. Maybe when I've calmed down a bit... :)

---

### Post by EasyRiderOnTheStorm on 2008-11-23
I still don't know what the cause might be, but I briefly ran into the same error message ("FAILED: xmltv returned error code 256." and "Failed to fetch some program info"), except in my case it was a total grabber failure (no guide fetched at all) caused by having the grabber's config file in the wrong place (under the wrong user's home folder). The error went away immediately after moving the file to the right user. 

Still, there's something deeply fishy here, as in my case the mixup was caused by mythfilldatabase prompting me to do a manual grabber config (which obviously ran under my **logged-in** user, not "mythtv"), then next time complaining that the file is not to be found, when the system presumably tried to run the grabber as "mythtv". And don't even get me going on the stupidity of suddenly expecting user input in the mythbackend console, without bringing it to the front, while the user stares dumbly at the hung myhtbackend progress bar, if the grabber is switched and the mythbackend-config GUI tries to run it in manual config mode...

---

### Post by brendankehoe on 2009-02-02
I found the same thing, and discovered the ~mythtv/.xmltv/cache directory had some files owned by root, others by mythtv.  When I got rid of everything in the cache and started mythfilldatabase again (as mythtv), all went well.

---

### Post by wayfarer_boy on 2010-01-15
This is an old post, I know, but I thought I'd add my own thoughts on the matter.  I was also having the 256 error occur when running mythfilldatabase.  I checked the settings on the 'videosource' table in mysql, and found that the xml grabber wasn't set correctly.  I'm in the UK and the bleb grabber has never worked properly, so I prefer to use the radio times one.

So my problem was solved by changing the xmltvgrabber field from 'tv_grab_uk_bleb' to 'tv_grab_uk_rt'.  Hope that helps someone.

---

