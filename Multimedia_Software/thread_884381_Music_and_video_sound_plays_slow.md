---
title: "Music and video sound plays slow"
date: 2008-08-08
forum: Multimedia Software
---

### Post by freakzilla on 2008-08-08
Sometimes my sound plays slow.  Occasionally, I'll play a mp3 (i use banshee) or play a video file (via totem) and the sound for some reason is slow.  I usually just reboot and it works well for a few days and will be slow.  Its not a big problem but kinda annoying.
I use a chaintech av710 sound card.
Any ideas to the problem?

---

### Post by funkz on 2008-10-11
I have the same problem but I haven't noticed it go away. I have a Chaintech AV710 too, using S/PDIF output. I'm on Xubuntu 8.04 amd64 (intel E8400, 4GB, 8800GTS).

Symptom is literally 'slow-motion' sound. Just did a test with Beat It by Michael Jackson, started playing it on my ipod and on Rhythmbox on this PC at the same time, and by the time the music on my ipod got to the lyrics, it took another 3-4 seconds for my PC music playback to reach the same point. I just noticed the frequency of all the music is lower than normal. Also find that video playback with Totem is a bit slow.

Any suggestions? Have been searching but not finding the hugest amount.

**UPDATE:** Ok I kinda fixed it. I removed the ~/.asoundrc and /var/lib/alsa/asound.state and started again using:

/etc/asound.conf: [http://ubuntuforums.org/showthread.php?t=187920](http://ubuntuforums.org/showthread.php?t=187920)
and
/var/lib/alsa/asound.state: [http://ubuntuforums.org/showthread.php?p=4359626#post4359626](http://ubuntuforums.org/showthread.php?p=4359626#post4359626)

But only with VLC media player! haha. Using ALSA Output and device hw:0.0. Seems the XFCE/Gnome backend doesn't work but I mainly use VLC anyway so I don't really care. I'm sure it's a matter of changing the device or something anyway.

---

