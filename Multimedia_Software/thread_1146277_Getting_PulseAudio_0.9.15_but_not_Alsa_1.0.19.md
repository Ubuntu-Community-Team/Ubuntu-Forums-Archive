---
title: "Getting PulseAudio 0.9.15 but not Alsa 1.0.19"
date: 2009-05-02
forum: Multimedia Software
---

### Post by NoThanksM$ on 2009-05-02
After installing Jaunty and reading up on some of the benefits of PulseAudio 0.9.15, I added the PPA located here:
[https://launchpad.net/~themuso/+archive/ppa](https://launchpad.net/~themuso/+archive/ppa)
and used Update Manager to get the updates.  However, it seems that not all packages from the PPA are being detected. Most of the ones listed at the link above have been downloaded and installed (including PA 0.9.15), but my alsa version is still 1.0.18.

I've done a lot of searching and haven't found anyone else talking about this problem.  If anyone has any suggestions as to why I'm receiving some but not all of the packages from that PPA, I'd be grateful for any help.

---

### Post by Roger E Critchlow Jr on 2009-05-02
You're getting new versions of lib*asound2*, I guess those are the only parts of alsa that the new pulse needs to update.  

-- rec --

---

### Post by NoThanksM$ on 2009-05-03
Oh, I see now.  Yes, it looks like that's the case.  Thanks for clearing that up for me!

---

