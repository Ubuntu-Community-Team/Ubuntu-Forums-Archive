---
title: "Install issue with S-1500"
date: 2008-01-30
forum: Mythbuntu
---

### Post by nunrgguy on 2008-01-30
I seem to be having an issue with install and Technotrend S-1500. When installing from the live CD with Myth there's an error message right before the end of install re some part being corrupted (this happens every time). The install finished then I go into setup. I@ve checked the CD and it scans fine.
During initial setup the Technotrend card cannot be found. However, after re-booting it can and I can scan for channels. However the mySQL database is then also corrupted with the 'cannot find card on channel 0' message. 
I tried the fix last night where all sources etc are removed and the database reset but the system could find no database.

Is this an issue with the current build?

---

### Post by stdPikachu on 2008-01-30
I ran into a minor issue that the Nova-T in my combo secondary frontend/backend wasn't detected correctly by the live CD; I worked around this by waiting until the system had been installed and rebooted before I tried configuring any of the myth stuff (which, TTBOMK, can all be done through the mythbuntu manager anyway...?); is this a doable workaround?

---

### Post by nunrgguy on 2008-01-30
That's pretty much what I did to get the card working. It scans OK. But the backend doesn't seem to set up right. The card doesn't register with the database and when you try to locate the database it doesn't seem to exist.

---

### Post by stdPikachu on 2008-01-30
What does your mythtv log say (/var/log/mythtv/mythbackend.log)? Is the backend set up with a static IP?

---

### Post by nunrgguy on 2008-01-31
I'll get back to you on that. I'm having another go today.
Setup with Static IP.

---

### Post by nunrgguy on 2008-01-31
I've got it sorted The solutino is to not run any of the setup at stage 15 but to finish, reboot and then setup.
All up and running now as a front-end backend machine. Just got to configure a few other bits such as LVM and get xbmc to myth working. Can't conect to the db with that at the moment.

---

