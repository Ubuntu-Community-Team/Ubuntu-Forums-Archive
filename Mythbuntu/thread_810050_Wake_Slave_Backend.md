---
title: "Wake Slave Backend?"
date: 2008-05-27
forum: Mythbuntu
---

### Post by CletusDFS on 2008-05-27
I have a master backend and one slave backend.

The master backend is a very energy efficient machine with very modest power requirements and stays active 24/7.

The slave backend is quite power hungry with it's tuners, CPUs and array of hard disks.  That being the case, I have it sleep when it is not recording, playing, or running jobs.

The setup works great with one reservation that I have been unable to conquer.  Once the slave goes to sleep, I cannot get the master to wake it back under all the conditions that would be desired.

The following are fact.

1. If the slave is sleeping and a job is scheduled to record on one of it's tuners, **the machine never wakes to record**.

2. If the slave is awake when a recording is supposed to start, the recording takes place as expected.

3. If the slave is sleeping and I reboot the master, upon reboot of the master, the slave is woken.

4. If I boot one of my front end machines, The slave will awake for me.

So anyone have any ideas for me? 

Thank you for your time.

CletusDFS

---

### Post by volkswagner on 2008-05-28
Have you followed this how to on your slave machine?

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake")

Post your MythWakeSet script.

---

### Post by DutchLoki on 2008-05-30
> **volkswagner said:**
> Have you followed this how to on your slave machine?

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake")

Post your MythWakeSet script.



Thanks... didn't now about this feature.

---

