---
title: "[SOLVED] Amarok: how to add songs from radiostream"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by dihfg on 2007-12-07
I use amarok for listening to radiostreams. Can anyone tell me if it is possible to continuously add the titles of the songs to the playlist?
When I open the radiostream the title of the song playing appears on the list, but is replaced as soon as the next song starts.
I would like to record the songs (unattended) using audacity and look at the playlist from time to time if there had been a title which was worth to save. Any ideas how to proceed?
Hubert

---

### Post by tgalati4 on 2007-12-07
>sudo apt-get install streamripper

Go into your /home/youruser/Music directory

>streamripper 192.168.1.1:3000  (whatever the address is of the radio stream)

>exaile &

Import music from /Music and set preferences to update library every 10 minutes.

---

### Post by dihfg on 2007-12-07
Thankyou tgalati4 for your assistance. This is exactly what I was looking for!:guitar:

---

### Post by tgalati4 on 2007-12-08
Rock on!

---

