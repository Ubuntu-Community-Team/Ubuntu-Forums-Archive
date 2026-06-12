---
title: "Multi-VNC user script trying to put everyone on :1 after 13.04 upgrade"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by marvelty on 2013-04-27
I have a computer that is set up to start several vncserver instances on boot (following the scripts [here]("http://ubuntuforums.org/showthread.php?t=1073892")). Under 12.10 it worked fine, but somehow in 13.04 it no longer works correctly. It still tries to run on boot, but stalls on the second user, and the first vncserver is inaccessible. If I do* /etc/init.d/vncservers restart*, I can see from the output that it is starting the first server correctly on :1, then trying to start the second user also on :1, which locks up the script and apparently breaks the first instance. 

The script I am using is exactly copied from the one in the link, except obviously I have changed the usernames in the /etc/default/vncservers file to match the real users. It does still identify the users using different numbers that *should* be used as different displays by the script in intit.d. I haven't found any error output from this so far that might help. 

If I run *vncserver* manually, it takes all arguments fine and I can open multiple users on different displays as each user individually, so that's OK, but I would like to have the multiple sessions going at boot as before. 

Does anyone have any ideas on a cause or a fix I could try? 

For reference, although I did have this working under 12.10, it is actually a fresh install of 13.04, not an upgrade. I copied the scripts back over after setup.

---

### Post by nachwaal3ab on 2013-04-28
tank youuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuuu

---

