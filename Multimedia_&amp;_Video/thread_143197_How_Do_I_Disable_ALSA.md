---
title: "How Do I Disable ALSA???"
date: 2006-03-12
forum: Multimedia &amp; Video
---

### Post by Torrance on 2006-03-12
So basically after much trouble we've worked out that iMac G5's are crashing on GDM startup, at the login screen, because of a conflict with the ALSA sound driver.

**To stop the system freezing we need to disable ALSA (and all sound).** And due to the freezes, we can only do this with the rescue CD - ie. in a command line without any ability to execute files, just modify config files.

Has anyone got any bright ideas how to work this one out?

---

### Post by hw-tph on 2006-03-12
[b]sudo update-rc.d -f alsa remove
sudo update-rc.d -f alsa-utils remove[/b]


Håkan

---

