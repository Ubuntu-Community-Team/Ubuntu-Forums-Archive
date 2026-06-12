---
title: "Audio working for one user, not working for another."
date: 2008-06-30
forum: Multimedia Software
---

### Post by steltho on 2008-06-30
I am using Kubuntu 8.04, sound has always worked on my machine, but a few days ago, while I was logged in as user A, I was trying to do some recording with audacity, and I seemed to have messed up my audio.  I was using alsamixer, and also KMix to adjust the volume for my recording.  Now whenever I log in as user A, none of my applications will play audio.  However, if I log in as another user, the audio works fine.  Does any one have any suggestions to help me fix this problem?

---

### Post by jpkotta on 2008-06-30
Maybe try cleaning out /tmp (and maybe /var/tmp) and rebooting.  After that, try cleaning out ~/.kde, but you will probably want a backup of that one.

---

### Post by h6w on 2008-07-01
Could also be a permissions problem.

Check that your /dev/audio* files are part of the 'audio' group and also that they are rw by that group. e.g.
$ls -la /dev/audio*
crw-rw----+ 1 root audio 14,  4 2008-07-01 15:29 /dev/audio
crw-rw----+ 1 root audio 14, 20 2008-07-01 15:29 /dev/audio1

Then check that both users are members of the 'audio' group.  
$groups
user adm dialout cdrom floppy audio......

---

