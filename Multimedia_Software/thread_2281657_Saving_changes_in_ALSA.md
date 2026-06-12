---
title: "Saving changes in ALSA"
date: 2015-06-08
forum: Multimedia Software
---

### Post by Toci on 2015-06-08
Hello, I want to save my settings for alsamixer.

What I'm chaning is Unmuting Speakers, turning up the volume for Speaker+LO and Disabling Auto-Mude Mode because what I want is to hear speakers and headphones at the same time.

So far, after making the changes,I tried 
```
sudo alsactl store
```

Also, I tried editing /usr/share/pulseaudio/alsamixer/path/analog-output-speaker.conf by chaning the volume to “merge” for headphones 

And editing /usr/share/pulseaudio/alsa-mixer/paths/analog-output-headphones.conf to change the element speaker to on and merge.

So far, no luck.  I have to change it manually every time after restarting.
Any ideas?

---

