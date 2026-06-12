---
title: "Sound does not work under intrepid"
date: 2008-11-20
forum: Multimedia Software
---

### Post by mmasroorali on 2008-11-20
From the day I got this computer (for my office use), sound did not work under Ubuntu. Sound was working under Windows XP. I was hoping that things will improve with newer versions. But still this persists under intrepid.

Output from [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) can be found at [http://www.alsa-project.org/db/?f=e4fcc440c10d2a147aa8572b47bfe7b6f56136ff](http://www.alsa-project.org/db/?f=e4fcc440c10d2a147aa8572b47bfe7b6f56136ff)

Other symptoms,

             System beeps work
             Output of gnome-alsamixer attached (none is muted)
             User has sound privilege

Your help will mean a lot to me, since the Windows users are having a field day. They are laughing at me since I can not make sound to work.

---

### Post by psyke83 on 2008-11-20
> **mmasroorali said:**
> From the day I got this computer (for my office use), sound did not work under Ubuntu. Sound was working under Windows XP. I was hoping that things will improve with newer versions. But still this persists under intrepid.

Output from [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) can be found at [http://www.alsa-project.org/db/?f=e4fcc440c10d2a147aa8572b47bfe7b6f56136ff](http://www.alsa-project.org/db/?f=e4fcc440c10d2a147aa8572b47bfe7b6f56136ff)

Other symptoms,

             System beeps work
             Output of gnome-alsamixer attached (none is muted)
             User has sound privilege

Your help will mean a lot to me, since the Windows users are having a field day. They are laughing at me since I can not make sound to work.

Intrepid uses PulseAudio by default, which I bet is not configured properly on your system.

Follow the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide, and pay attention to Part A, Step 5 (to set the default playback device).

---

### Post by mmasroorali on 2008-11-22
I followed the instructions to the letter. But alas my computer still does not want to speak.

---

