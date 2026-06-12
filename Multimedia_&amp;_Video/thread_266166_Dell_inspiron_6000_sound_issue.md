---
title: "Dell inspiron 6000 sound issue"
date: 2006-09-26
forum: Multimedia &amp; Video
---

### Post by Furious_joe on 2006-09-26
I did a fresh kubuntu install a few days ago, and when I did it then the sound worked well. I must have done something (but i don't know what) because now Kmix does'nt detect any mixer, and sound has stoped working. Is there any way to fix this, other than a reinstall (which I obviously dont want to do.)

---

### Post by Mr Frosti on 2006-09-26
As with most troubleshooting, the key is in isolating the problem. Ask yourself what the last thing that was done to the machine before the sound stopped. Specifically, was any software installed, upgraded, or removed from the machine?

To test and see if you have ANY sound, press the key sequence "Ctl+Alt+F1" to switch to a virtual terminal. Login as your user, then run the command "sudo /etc/init.d/kdm stop" and enter in the password. This will stop the X server (and any sound daemons) from running. We can be guaranteed a clean running environment after this step.

Browse to a sound file (use "cd" to change into a directory). Once you have located a file, type in "artsplay <sound filename>". If you hear music, then the issue is with a resource locking the sound card. 

BTW, you can switch back to the X server by running "sudo /etc/init.d/kdm start". 

Please post the results (and any messages) from this experiment.

---

