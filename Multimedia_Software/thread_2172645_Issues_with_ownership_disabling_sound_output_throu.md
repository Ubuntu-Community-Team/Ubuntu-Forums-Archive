---
title: "Issues with ownership disabling sound output through PulseAudio"
date: 2013-09-05
forum: Multimedia Software
---

### Post by impinball on 2013-09-05
I already had posted a thread on this earlier, but it is about 4 weeks old. The link to it is here: [http://ubuntuforums.org/showthread.php?t=2165204](http://ubuntuforums.org/showthread.php?t=2165204). One item of note is that I didn't know what the problem really was, then and now I do. Keep in mind that 99% of my expertise is with Windows and not anything at all Linux (the shell isn't a foreign concept to me, but I'm far more used to DOS-style batch scripting than anything else).

The issue is that ownership permissions of my user folder are root, and I can't change the owner to my user name. I have also tried changing it via [FONT=courier new]sudo[/FONT] (specifying my username), but nothing happens, even with that route. The primary side effect is that no sound can work through PulseAudio, even though it works flawlessly through ALSA without even the smallest issue. That previous forum post has most of the initial details of my problem, but my last reply (2 weeks ago) has not had a response. This thread was created for two reasons: to make a thread with more of a focus on the actual issues themselves instead on figuring out the problem, and to see about getting more help on the issue (considering that this problem persisted through all that previous troubleshooting).

One thing of important mention here is that it is an NTFS partition used by both Windows and Linux for very similar reasons (and I'm also currently trying to mount it as "C:\Users" in Windows as well, which could require a start-up bash script for Ubuntu if the only solutions are temporary).

---

### Post by impinball on 2013-09-05
BTW, I tried the sound troubleshooting guides here and several other places as well, and none of them even gave a single sign of success.

---

### Post by impinball on 2013-09-06
(Note to mods/admins:) By the way, if there is a better forum place to put this, please move it there. (It regards sound, but the root is based on ownership issues, and the affected directory is mounted on an NTFS partition used similarly for Windows.)

---

