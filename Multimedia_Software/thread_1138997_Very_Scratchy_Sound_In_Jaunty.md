---
title: "Very Scratchy Sound In Jaunty"
date: 2009-04-26
forum: Multimedia Software
---

### Post by Sgtblades275 on 2009-04-26
I upgraded to jaunty a couple days ago and am just now noticing that anyhting with sound plays with a really annoying scratchy noise. I first noticed this after I added medibuntu Jaunty packages. adding those helped with a video problem I was having. they also possibly did this. but, I'm unsure. Sound card: Intel (ICH5) AC'97 and I'm using the alsa mixer.

---

### Post by kostkon on 2009-04-27
For a start you could check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by Sgtblades275 on 2009-04-28
hah, dude thanks a lot for that link. helped me loads
Ok, I fixed the scratchy sound in all programs EXCEPT for Firefox audio. It still sounds scratchy whenever I play anything through it and the pulse audio mixer says it's running through Alsa Plugin Firefox: Alsa Playback. How do I change that to pusleaudio?
Note: previously everything on here I had run through OSS and it was crystal clear. After upgrading to Jaunty it gives me an error everytime I try using OSS. Just a note. Not that it really matters much anymore. Just got to figure out the firefox deal...

---

### Post by markbuntu on 2009-04-28
flash still does not have a native pulse plugin so it uses the alsa plugin. At least that finally mostly works. Hopefully they will have a pulse plugin someday.

Check the PCM volume in the gnome-alsamixer. Some people have fixed their scratchy alsa sound by turning it up all the way.

---

### Post by cjxc92 on 2009-04-29
I'm having a similar problem as the OP: after a clean install of Jaunty, the sound out of both my laptop's speakers and my headphones sounds really scratchy and gross.  I tried the suggestions on the link ([http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)) to install Pulse Audio stuff, but to no avail.  Any help would be greatly appreciated.  Thanks

---

### Post by cjxc92 on 2009-04-29
Oh and I forgot to mention that I tried editing the /etc/pulse/daemon.conf file as was mentioned in another forum with no luck.

---

### Post by heatpumpcontrol on 2009-06-14
I found that by either muting or turning the volume off on my PC Speaker in the Volume Control Preferences, it made the scratchiness all go away! Woo hoo. Fixed! Now, of course, I don't have pc speakers so this is what fixed my issue.

Hope this helps someone........ :p

---

