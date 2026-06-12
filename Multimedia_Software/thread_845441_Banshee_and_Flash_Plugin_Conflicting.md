---
title: "Banshee and Flash Plugin Conflicting"
date: 2008-06-30
forum: Multimedia Software
---

### Post by Doulpe on 2008-06-30
So, I'm having a problem. Whenever I have Banshee open, and then try to watch a Youtube video, it won't play the video past 2 seconds. However, if I close Banshee and then restart Firefox, the video will play. 

How can I fix this? And can you go into detail; I'm kinda a Linux noob.

---

### Post by Aifel on 2008-07-05
I'm guessing it's a PulseAudio and FF issue. If you haven't upgraded you Flash and Firefox to their latest versions, you might want to try that.

---

### Post by Danyl on 2008-07-10
I had this problem and fixed it by doing 2 things. Not sure which one actually solved it however!

(1) Uninstall Pulse: ```
sudo apt-get autoremove pulseaudio --purge
```

And/or:

(2) In System/Preferences/Sound, set all to ALSA.

Log out and back in.

Hope this helps.

---

### Post by Doulpe on 2008-07-12
It must be the code because I have already tried ALSA so hopefully the code works!:)

---

### Post by Doulpe on 2008-07-12
Sorry for the double post but it WORKS!. Thanks you so much I've been trying to fix that problem for a while now. :)

---

