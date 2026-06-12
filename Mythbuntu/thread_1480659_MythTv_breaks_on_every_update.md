---
title: "MythTv breaks on every update"
date: 2010-05-11
forum: Mythbuntu
---

### Post by sirbanks on 2010-05-11
I am curious why everytime there is an update to MythTV, backend or frontend, it breaks the connection between the two? I have a machine IP address to allow remote frontend connections to the back end and everytime there is an update through the package manager the frontend can no longer connect to the backend. I have to go through the following process.

1. Open Myth frontend (get error that it cannot connect, no uPNP).
2. Go into the frontend settings and change the hostname to localhost.
3. You are now thrown into the frontend settings again but with a different theme.
4. Change the hostname back to the original IP address I had before changing it to 'localhost'.
5. Exit the frontend.

Now everything will work again until the next update. This is not a big issue since I now know how to correct it but any ideas on how to correct this annoyance is appreciated. If nothing else, maybe this post will help someone else just experiencing the issue. Thanks in advance, guys!

---

### Post by tgm4883 on 2010-05-11
You need to break down the process and find out what is getting updated that is causing that. I haven't seen that on any other installs. Next time it happens, note what packages were updated.

---

### Post by optimusprime8 on 2010-05-13
This same thing happened to me too, but I can't get video playback to work either.

---

### Post by the_pod on 2010-05-13
I've found that the updates are more problem then they're worth.  If everything is working as desired, why open yourself up to potential issues?  Just curious.

I'm on a 9.4 system and have updates turned off.  Granted, I did this b/c I always had to recompile due to some system spec issues but I guess I've also developed the opinion to not fix what ain't broke.

---

### Post by LowSky on 2010-05-13
> **the_pod said:**
> 
I'm on a 9.4 system and have updates turned off.  Granted, I did this b/c I always had to recompile due to some system spec issues but I guess I've also developed the opinion to not fix what ain't broke.

I agree with you if the computer is only going to be used as a media center, but If its used for normal use, then you should keep it updated.

---

