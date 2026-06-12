---
title: "Cannot initiate sound -no sound error after reboot"
date: 2008-06-04
forum: Multimedia Software
---

### Post by D.Sync on 2008-06-04
After installed MPD and GMPC yesterday, my laptop cannot output sound anymore after reboot.

When I try to open/play music from Rhythmbox, the app just hang then I need to force quit. Any attempt to play movie file also result in the similar case, where the video can be rendered/output with no sound output.

However, when I try to playback music using GMPC, the sound can be output. Login system sound also working fine.

Any ideas on how to rectify this problem?

---

### Post by mridkash on 2008-06-04
Though I don't have any idea about MPD or GMPC, but from the symptoms I can guess something is grabbing your sound card and not letting others to use it. It is a common problem.
Try configuring the System>Prefs>Sound settings, set them all to ALSA and try to test sound. Post the errors that you get.

---

