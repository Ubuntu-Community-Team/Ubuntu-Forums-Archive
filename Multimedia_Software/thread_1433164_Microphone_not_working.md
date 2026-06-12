---
title: "Microphone not working"
date: 2010-03-18
forum: Multimedia Software
---

### Post by kadaitcha on 2010-03-18
Judging from the countless posts on the subject it seems a heap of users have microphone problems, however I haven't been able to locate any comprehensive information on fixing this issue. Is it the situation that microphones are simply unsupported in current versions of Ubuntu ?? If this is the case I'll know to stop tearing hair out.

---

### Post by lytithwyn on 2010-03-18
Ubuntu definitely supports microphones.  Sometimes it's just a little tricky finding the right mixer settings.  I'm not sure exactly what to do in Karmic, but I got it working by playing with the sound mixer in Jaunty.

If you're using Jaunty, try this:

Click on your sound mixer icon, then click "Volume Control..."

Here are the various channels from your sound card that ubuntu can control.  Check to make sure your microphone isn't muted (if it is, it'll have a little red x at the bottom).  Then check the switches tab to make sure there aren't any check boxes you need to change.  For instance, on mine I needed to check a box that added extra gain to the microphone before I could hear it.  Most of these should be self explanatory.

Sometimes your sound card will have channels that don't show up by default in the sound mixer.  If you think this may be the case, click on preferences.  There you'll find a list of all available channels.  The ones that are checked will show up in your mixer.  If you add one and it doesn't seem to do anything, you can always go back and uncheck it.  Before you change these, you may want to take note of which ones are checked by default.

---

### Post by iamparrot on 2010-03-31
I had no mixer or properties controls available but I was able to get KMix installed and sure enough my microphone was muted, but now it's working fine.

9.10 Karmic Koala version

---

### Post by lytithwyn on 2010-04-01
Another really good alternative mixer is alsamixer, which runs in a console.  It shows a lot of different stuff that the Karmic sound mixer under gnome doesn't; that way you don't have to install any KDE libraries.

---

