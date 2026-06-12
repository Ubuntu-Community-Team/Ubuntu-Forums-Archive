---
title: "No Sound in Firefox"
date: 2009-07-17
forum: Multimedia Software
---

### Post by Tyrfing on 2009-07-17
I recently fixed a problem where no sound on my cpu worked. I installed some PulseAudio libraries that didn't come with my 9.10 upgrade, and all the sound works, except in Firefox.

Every app seems to work perfectly with sound, but I am consistently getting no sound from Firefox.

Does anyone have any ideas on how to troubleshoot this problem? I have been looking around, but haven't found much.


   Thanks!
      -Tyrfing

---

### Post by Tyrfing on 2009-07-18
bump

---

### Post by Tyrfing on 2009-07-19
bump

---

### Post by Tyrfing on 2009-07-19
bump


Just adding that my sound also does not work in Konqueror...

---

### Post by lswb on 2009-07-19
Look for a volume control on the specific player in firefox that should be playing the sound, i.e. if it is a flash video, there will be a speaker icon or similar to control volume for that specific source.

Another thing is check your home directory for a .pulse directory or a file named .pulse-cookie. If they exist, remove them and restart firefox. These can prevent sound from other apps also. I'm considering putting these commands in my .profile

rm .pulse-cookie
rm -r .pulse

---

### Post by zepita on 2009-07-19
by no sound in firefox you mean that FLASH does not have sound? You may want to check if ALSA or Pulse is selected under sytem>preferences>sound since the flash plugin works with those servers as far as I know. I did not get it to work with OSS
Other thing you can try is to install the .deb directly from adobe. That solved a few issues I had with sound and youtube for example.

---

