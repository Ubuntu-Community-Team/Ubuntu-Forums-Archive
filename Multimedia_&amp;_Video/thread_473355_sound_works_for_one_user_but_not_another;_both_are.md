---
title: "sound works for one user but not another; both are in audio group"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by bcrowell on 2007-06-13
I have a fresh install of fiesty, with two users, A and B. User A was the first user created, and was therefore automatically in the audio group. Sound worked for user A, but not for user B. After a little googling, I realized that the problem might be that B was not in the audio group. So I added B to the audio group, but that didn't help. In GNOME, user B gets an icon for the sound controls that shows that the controls are inoperable, and when she right-clicks on the icon, she gets the message "No volume control Gstreamer plugins and/or devices found."

I have read the material at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) , and the only part that seems relevant is adding user B to the audio group, which I've already done.

Any suggestions? TIA!

-Ben

---

### Post by bcrowell on 2007-06-14
OK, I figured out the problem. Adding the user to the audio group didn't have any immediate effect, but after rebooting, the problem was fixed.

---

