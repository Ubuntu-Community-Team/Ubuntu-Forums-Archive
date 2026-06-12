---
title: "[SOLVED] thinkpad volume controls no longer work"
date: 2008-11-16
forum: Multimedia Software
---

### Post by JebusWankel on 2008-11-16
I have a T61 and the volume controls worked under Hardy and Intrepid by default, but when trying to get an external mic to work, I opened volume control and flipped around in the preferences. Now when I use the volume controls the pop up shows that they are working, but they don't work, the volume doesn't change. The volume control applet works fine. When I upgraded to Intrepid the situation didn't change didn't change.

---

### Post by JebusWankel on 2008-11-16
Bump. To clarify, when I upgraded I left my /home partition untouched, so I figure there is some config file that I could replace during a livecd session. I looked at the files in .pulse and i don't think they're it. I put in a livecd and all the volume preferences are the same as the default. All I did to mess this up is toggle the volume prefences, so this is pretty messed up that this happened. I have no problem popping in a livecd and replacing config files, I just don't know which ones would help.

---

### Post by JebusWankel on 2008-11-16
Problem solved. I just had to go to System > Preferences > Sound and set the default mixer track from HDA Intel to either of the other options not labeled capture. I hate when I underestimate this stuff.

---

