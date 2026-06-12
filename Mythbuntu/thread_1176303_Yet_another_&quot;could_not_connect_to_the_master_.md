---
title: "Yet another &quot;could not connect to the master backend server&quot;  error"
date: 2009-06-02
forum: Mythbuntu
---

### Post by zaprat on 2009-06-02
I managed to get ACPI working with myhwelcome however I now get error "could not connect to the master backend server" on mythbuntu 9.04. AfterI hit OK it the Mythwelcome starts OK.
 
I am using mythwelcome ie.  MYTHWELCOME=true in the /etc/mythtv/session-settings file.
 
I tried adding "sleep 5" in front of the Exec=mythfrontend in the mythtv.desktop but this did not help as in the instructions in [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)
for 8.04 but this did not work. 
 
I believe the issue may be that the front end it attempting to connect before the backend is ready.
 
Any suggestions on how to resolve this in 9.04

---

### Post by zaprat on 2009-06-02
Solved:
 
ammended the mythtv.desktop
replaced 
exec=mythfrontend --service
with
exec=/usr/bin/MythStart
 
then created executable script MythStart in /usr/bin/
!#bin/sh
#put this script in /usr/bin/MythStart
# wait 10 sec whilst backend starts
sleep 10
# run the mythwelcome &/or mythfrontend 
mythfrontend --service &

---

