---
title: "Mythtv - no desktop icons when I exit front end..."
date: 2016-12-21
forum: Multimedia Software
---

### Post by JimLS on 2016-12-21
Running Ubuntu 14.04 with myth 0.27.  I have a combined frontend/backend on the same box.  I normally run myth frontend and have it auto start.  It appears to be running ok.  Occaisionally when I exit the front end to run other other applications (such as a browser) things don't work right.  About a week ago I exited and had a desktop view that appeared ok.  I could pull down the applications menu but when I selected something nothing happened.  I was still looking at the same screen and could select it again but the selected item never started.  I rebooted and things were ok.  

I recently updated the system.  Today I exited the front end and had a screen with the session boxes (not sure if thats the proper term) that are normally at the bottom on the right side and some unusual application icons along the left side.  Nothing along the top except the background which covered the whole screen. I used ctrl-alt-T to get a command window and rebooted.  The front end looked ok (but I didn't try to do anything in it) and I exited it.  Then I had just the background image with NOTHING else.

I have considered having a regularly scheduled, periodic reboot to keep things running smoothly but a reboot doesn't resolve the latest issue.  I am not sure where to start in fixing this and need some suggestions...

---

### Post by JimLS on 2016-12-21
This seems to have something to do with the Nvidia driver.  According to my notes I previously installed nvidia 331.113.  in the gui under "advanced drivers".  It looks like 340 is being used now and only 304 and 340 are choices in gui under "advanced drivers" tab.  Apt-get install seems to install 331 and 340 or at least some of both together.  I also don't have audio output via the nvidia HDMI output.  It appears these drivers got changed in the last update.  How do I force the older version?

---

### Post by JimLS on 2016-12-23
331 has been removed and 340 has replaced it so no way that I see to go back to 331.  Should have locked it so it couldn't be updated.  I have tried 

sudo su
apt-get update 
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install --reinstall gnome-shell 
sudo apt-get install --reinstall ubuntu-gnome-desktop
and reboot

still no desktop icons.  I can get the application menu and start applications with Alt-F1.
I was able to get sound working in Mythtv by selecting the video card audio output in mythtv setup rather than the default system output

Any ideas what else to do?

---

### Post by JimLS on 2016-12-24
Upon further digging the problem isn't that the desktop isn't there, it's that it is bigger than the display and I just can't see it.  Not sure why this changes with the nvidia driver update but it and the default sound device did.  Perhaps the name of the sound device on the nvidia board is different.  Anyway, now I need to figure out how to reduce the display size.  My display is detected as 7" but is really 42".  I found lots of reports of 7" display report in error and overscan.

---

### Post by JimLS on 2016-12-24
setting underscan of 70 in nvidia configuration fixed the size so everything can be seen and going into system sound configuration and setting output to HDMI restored desired (and previous) operation.  Display is still detected as 7" but it doesn't really matter what it is called as long as it works.  Didn't expect an update to make such drastic changes though...

---

