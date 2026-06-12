---
title: "I have sound, she doesn't, 12.04 LTS, Nvidia"
date: 2012-05-26
forum: Multimedia Software
---

### Post by Hwy120 on 2012-05-26
This is a new install of 12.04 LTS, with MythTV frontend.  2 users.  Analog audio worked for both users in MythTV and Firefox.

For user number 2, in MythTV, used the keyboard (Windows) keys to adjust the volume and mute. Everything seemed to work. Pressed the keys a few times and suddenly no audio. The mute shows going on and off and the volume going up and down. Now there is no sound in Firefox, and no bong bong at the user/password screen if user 2 was the last one to log out.

For User number 1 there is a sound in Firefox, MythTV, and at the user/password screen if user 1 was the last one to log out.  The offending keyboard keys have not been pressed by user 1.

Something changed in the software for user 2 after pressing the keys. I have not been able to identify any differences between the two users. I must not be looking in the right places.  Any help would be greatly appreciated.

Thanks

---

### Post by Hwy120 on 2012-05-27
Installed gnome-alsamixer.  Logged into the user without audio. Un-muted everything.  Both users now have audio.

---

### Post by mmesantos1 on 2012-05-28
Thank you for the info on this.

---

### Post by Ubu_Fester on 2012-09-26
Installing the gnome-alsamixer did the trick for my mythtv installation.  I'm running mythbuntu 12.04, and using the command line for alsamixer did not provide enough control of all the audio options available to me.  I am not using hdmi (digital) audio -- I simply need analog audio OUT of my mythtv box and into my stereo.

I needed to unmuted PCM, and that is very easy via the gnome-alsamixer.  If there was another way to unmute PCM -- I didn't know it...

---

