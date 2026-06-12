---
title: "MythTV idle suspend WITH frontend running"
date: 2008-07-23
forum: Mythbuntu
---

### Post by slackey on 2008-07-23
I am running a combined backend/frontend and am trying to get automatic shutdown and wakeup working. I followed these steps: [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) and got it working. I modified it so that it suspends instead of shutting down (works fine).

The only problem I have now is that I have to exit the frontend for the the backend to be considered idle. Is there any way I can get around that so that the backend ignores the frontend when determining idle status? I merely want the whole system to suspend after 20 minutes of idle, and then when it wakes up I want the frontend and backend to be running.

I considered not using Myth's built in shutdown functionality and instead just using Ubuntu's power manager to suspend the machine after a while, but I'm not sure how I could use the MythWakeSet script I created to make sure that it woke up at the right time. (I have the same problem when using irxevent to make my remote put the machine in standby manually)

---

