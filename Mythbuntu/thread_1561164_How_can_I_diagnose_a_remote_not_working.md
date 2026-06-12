---
title: "How can I diagnose a remote not working?"
date: 2010-08-25
forum: Mythbuntu
---

### Post by bunglebungle on 2010-08-25
After getting some updates in the last week, including a kernel update, I have been having a lot of problems with my Streamzap remote.  One of the first times it stopped working I somehow thought to check the device and noticed that /dev/lirc0 was owned root:root.  Changing the group to users instantly allowed the remote to work.  I then had more problems with the remote not working, but changing the permissions no longer helped.  I have since realized that the remote can work even without the permissions changing, so that was a red herring.  When it doesn't work I try reloading the modules and restarting lircd, but irw still does not respond.  I have run out of avenues to pursue.  This last time I just had to reboot a couple of times and it started working.  When a remote isn't working what are the steps I can take to diagnose the issue?

---

