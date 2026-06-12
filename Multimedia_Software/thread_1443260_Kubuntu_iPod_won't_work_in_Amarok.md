---
title: "Kubuntu iPod won't work in Amarok"
date: 2010-03-30
forum: Multimedia Software
---

### Post by 240r on 2010-03-30
It worked fine but then I didn't connect iPod to Amarok for a few months and now it doesn't work. Using Amarok 1.4.10 and 4th generation iPod. 

```
sudo mount /dev/sdc2 /media/ayumi
``` mounts the iPod so Amarok states "iPod Grayscale at /dev/sdc2 (mounted)" but clicking connect gives ```
Media Device: failed to create lockfile on iPod mounted at /media/ayumi: Permission denied
```

It doesn't list files already on iPod and I can't transfer files. Also, if it's already mounted, I shouldn't have to click connect. It's all very strange.

"ayumi" is the mount point I assigned.

EDIT: I think it works when I do sudo amarok. Which is a bad idea. Also played around with deleting the ituneslock file, fstab. So many hours spent just trying to use iPod on Kubuntu :/

---

### Post by 240r on 2010-04-27
Bump. Any ideas?

---

### Post by Mamarok on 2010-05-29
> **240r said:**
> Bump. Any ideas?
Not really, no, sorry. I don't have an iPod and I haven't used Amarok 1.4.x since quite some time, I'm quite happy with Amarok 2.3.1 beta (2.3. is release next week). If it works with sudo rights, try with a different user. If that works, you should move your config files of Amarok, likely there is some configuration causing it.

---

### Post by 240r on 2010-05-30
Thanks for the reply. I will try your suggestion.

I found Amarok 2 to be vastly inferior to Amarok 1 in... every way. I really wish there's a way for me to smack Amarok developers with giant plush Pikachus and scream why they messed up the best music player ever :/

---

### Post by 240r on 2010-05-30
Creating a new user is creating more headaches as I had never done it before. Is there a way just to wipe out my current configuration and start anew?

---

### Post by 240r on 2010-05-30
Um. Ok. This is crazy weird.

After creating and logging into the new user account and plugging in the iPod before realizing the headache, I logged off back into my main account. Upon opening Amarok and trying to connect, it said device is already locked and suggested I remove the iTunes lock, etc. I click remove in the dialogue box and... it worked!

No idea why. Let's hope I don't have to go through all these motions next time...

---

