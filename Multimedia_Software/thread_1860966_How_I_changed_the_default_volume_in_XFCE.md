---
title: "How I changed the default volume in XFCE"
date: 2011-10-15
forum: Multimedia Software
---

### Post by linuxhippy on 2011-10-15
I have the mail checker setup to play a sound when I get email.  My speakers are cheap and vibrate if the volume is set to 100% which is the default sound settings when the XFCE mixer starts and if I get email right away my neighbors know it.  So, I found that if root turns it down with alsamixer that I can then make a script that is auto-started when I log into XUbuntu.  Here's how:

sudo alsamixer 
set volume sliders to where you want them and exit with ESC key
sudo alsactl store

Now make a simple 1 line script:
nano
alsactl restore
exit and save with CTRL and X
save it to file ~/volume-level.sh

Make it executable (this may not be necessary in Ubuntu)
sudo chmod a+x ~/volume-level.sh

Now set it to auto-start at login:
Applications>Settings>Settings Manager>Session and Startup
Click on Application Autostart TAB and Add

Name: Volume-level
Command: sh /home/USERNAME/volume-level.sh
Save new application with OK and reboot

Sound setting should now not be at 100% and can be verified with:

alsamixer

---

