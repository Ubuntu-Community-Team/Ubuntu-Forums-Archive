---
title: "Mythtv instantly freezes when started 12.04"
date: 2013-01-27
forum: Mythbuntu
---

### Post by pollywog on 2013-01-27
I recently installed mythtv on an existing 64bit 12.04 system. Seemed to be running nicely for a couple of days, but suddenly began freezing up when the frontend was started. It freezes hard and requires a force quit to get it off the screen. Even after a force quit the frontend executable continues to run (I can't see it) and must be killed through the system monitor. I notice that before it malfunctioned I had changed to the mythbuntu theme, and upgraded it to the latest version. Since I can't access the GUI settings to switch to another theme, I don't know if that is the cause, but it sure seemed to have happened on the next startup after the upgrade. In frustration I have tried completely uninstalling everything that comes up with “mythtv” in its name via synaptic, and deleting anything remaing with “mythtv” in its name from the filesystem. After reinstalling mythtv the backend setup freezes instantly when started with the same symptoms as were experienced with the previous frontend freezes (force quit & needs to be killed with system monitor). Interestingly, I see that the theme is still the mythbuntu theme, and not the default theme that I would expect to see on a fresh install. Obviously there is some remnants being left behind after uninstalling which I suspect to be causing me problems. I'm OK with uninstalling again and starting from scratch, but how do I get rid of everything?

---

### Post by steeldriver on 2013-01-27
I've had a funny front end freeze like that after editing something - can't remember what (it wasn't the theme - something to do with the codec iirc) - the only way I could get out of it was to edit the mythconverg database directly in mysql and restore the previous value

---

### Post by pollywog on 2013-01-27
I think that you are correct about the database thing. I found the solution (hopefully) here :[http://ubuntuforums.org/showthread.php?t=1394594]("http://ubuntuforums.org/showthread.php?t=1394594")
Thanks!

---

