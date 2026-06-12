---
title: "No audio in Flash player or for system sounds or effects under user account"
date: 2009-08-19
forum: Multimedia Software
---

### Post by figneutron on 2009-08-19
Dating from installation of 9.04, I have had no audio for system sounds or effects and no audio for Flash 9 or 10. I have great audio for everything else: music cds, internet radio, dvd movies. On the other hand, what is wierd to me is that the Guest account does not have this problem. If I log on as Guest, I get perfect audio! I found out that for Guest Firefox does not use Flash Player to play videos on YouTube; rather swfdec 0.8.2 is running the flash content. What is going on here? I have no idea how to fix this.

---

### Post by Yellow Pasque on 2009-08-19
Sounds like a possible asound configuration issue. The apps you're having issues with (Flash, libcanberra) use ALSA directly in Jaunty.

Take a look at the .asoundrc file in each user's home directory and see if you can figure anything out.

---

