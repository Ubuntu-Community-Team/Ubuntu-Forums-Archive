---
title: "[SOLVED] No audio with Alsa and Pulseaudio"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by jfernyhough on 2007-11-03
Randomly my audio stopped working properly. I'd previously fixed it after installing Pulseaudio ([http://ubuntuforums.org/showthread.php?t=570436](http://ubuntuforums.org/showthread.php?t=570436) ) with asoundconf set-pulseaudio but now everything was being routed through OSS. Not ideal.

Took me a while to work out why before I saw a reference to a group called pulse-rt when running a commend in a terminal. And that was the key: group membership. This is odd, as it all used to work.

Anyhow, I ran System->Administration->Users and Groups, Manage Groups, and added myself to pulse and pulse-access. Logged out and in, and as if by magic, my sound is working again.

---

### Post by mrvertigo on 2007-11-03
Great!

---

### Post by Glowing Fish on 2007-11-03
This seems like it might work for me.

The only problem is, this is quite an old thread, and in Gutsy, it doesn't seem like there is this option under System->Administration.

---

### Post by Hhkmac on 2007-11-17
Worked fine for me, there was another option under System - Administration - Users and groups - Manage Groups

I had to select all pulse groups then add myself to gdm group.

Works fine, cheers!  :guitar:

---

