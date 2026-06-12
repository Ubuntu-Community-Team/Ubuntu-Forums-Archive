---
title: "MythTV 0.28 temporarily prevent idle shutdown"
date: 2016-07-05
forum: Mythbuntu
---

### Post by waynelivingstone on 2016-07-05
I am a long time MythWelcome user having my combined backend/frontend shutdown when not in use or recording. 
I recently decided it was time for a refresh so I have done a fresh install of Mythbuntu 16.04. 

I am using the new Idle Screen in the frontend for shutdown/wake and it seems to work quite well, but I am missing a couple of features of Mythwelcome. 
My main issue is that I want to be able to prevent the system from shutting down during a specified time period (like Mythwelcome daily wake/shutdown), so that mythfilldatabase can run without interruption and because I prefer it to stay awake during the evening when I am most likely to watch TV. 

I believe this can be done with a Pre Shutdown check script, but I have no idea how to write such a script so I am hoping someone here might be able to help me. 
I am wanting to prevent shutdown between 20:30 - 01:00 every day. 

I hope someone can help me with this.

---

### Post by JasonEde on 2016-07-05
On the mythwelcome screen press I and then configure the awake times in there?

---

### Post by waynelivingstone on 2016-07-06
I am using the new Frontend Idle Screen instead of Mythwelcome. But without mythwelcome I dont have the daily wake/shutdown to prevent shutdown. 
So I want to create a pre shutdown script to temporarily lock mythshutdown which should give the same effect.

---

### Post by khPWXxF on 2016-07-06
Two suggestions.
Look at the script at the end of the wiki on mythshutdown.  Could you run a script at power up which waits for your "on" time, issue the lock then sleeps until "off" time?

Alternatively, put your maintenance code in setwakeup.  See autobackup.sh for an example.
Hth
Phil

---

### Post by waynelivingstone on 2016-07-06
The script at the end of the mythshutdown wiki is part of what I have in mind. 

Under the ACPI Wakeup wiki here:
[https://www.mythtv.org/wiki/ACPI_Wakeup#Integrate_into_MythTV](https://www.mythtv.org/wiki/ACPI_Wakeup#Integrate_into_MythTV)

In the backend Wakeup/Shutdown settings I can have a 'Pre Shutdown Check Command' (for me this is usually set to: mythshutdown --check)

A little further down on that page, under Desktop Users, there is a checklogin.sh pre shutdown script that checks to to see if a user is logged in and will prevent shutdown if this is true. 
The pre shutdown check automatically gets called whenever the the backend has been idle for the preset amount of time. 

So I would a version of the checklogin.sh script that checks for time of day instead of user login. 
I have no experience in writing scripts so that is why I need some help.

---

