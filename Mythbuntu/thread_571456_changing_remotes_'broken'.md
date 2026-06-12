---
title: "changing remotes 'broken'"
date: 2007-10-09
forum: Mythbuntu
---

### Post by rusty0101 on 2007-10-09
For some reason if you decide after the install to reconfigure the remote, it seems to hang at the end of generating the lircrc file. I don't know if this is a permissions issue, or if it is having problems with the fact that there is already such a file. It does seem to get the correct lircrc file in /etc, just not in ~/.mythtv/

I'll try to get a bug reported in launchpad as well, but since it does not 'break' anything at this time, or generate any errors that I can see, I'm not sure how much attention it can get right now.

Where this will end up causing a problem is when someone builds a back end, has lots of content on their system, and decides 'OK, I'm tired of sitting right at the computer with a wired remote, time to get an IR or wireless one.' Obviously it would be better if there were some way to detect when a remote was plugged into a USB port, or if a ir receiver was built some place, then figure out how to detect and dynamically configure the remote for the user, but I know that's outside of the scope of the project at this time.

Looks like the launchpad bug in question is #144361, and I have added my notes, but it is crunch time.

---

### Post by davemorris on 2007-10-23
In the mean time, to manually reconfigure the remote you can use

```
sudo  dpkg-reconfigure lirc
```

---

