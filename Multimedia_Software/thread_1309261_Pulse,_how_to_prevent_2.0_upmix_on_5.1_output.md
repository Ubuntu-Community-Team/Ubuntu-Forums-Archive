---
title: "Pulse, how to prevent 2.0 upmix on 5.1 output?"
date: 2009-11-01
forum: Multimedia Software
---

### Post by Sam Stone on 2009-11-01
Hi all!

When i set profile to *analog 5.1 output + something* on my audigy2 value all stereo sounds (music, youtube, etc) plays through all speakers.
On *analog stereo + something* surround sound from movies downmixes to 2.0

With alsa on jaunty all works fine: surround 5.1 through all speakers, stereo music - through front speakers only.

---

### Post by Sam Stone on 2009-11-06
Fixed
[http://ubuntuforums.org/showpost.php?p=8170860&postcount=15](http://ubuntuforums.org/showpost.php?p=8170860&postcount=15)
and  ```
enable-remixing = no
``` in /etc/pulse/daemon.conf

---

