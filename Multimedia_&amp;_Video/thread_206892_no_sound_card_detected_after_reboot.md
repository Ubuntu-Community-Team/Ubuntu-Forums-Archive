---
title: "no sound card detected after reboot"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by sandook on 2006-06-30
I'm new to Ubuntu but I finally got my system to detect my soundcard with ```
sudo modprobe snd-es18xx
``` and it runs fine, however, I have to run this command after every reboot to get my soundcard to work. Is there a way I can have the system run this automatically at startup?

---

### Post by ewz on 2006-07-01
can u add your sound card to /etc/modules I had to do this once with my video card on an old debian computer i had, just adding nvidia in the list got it to load when i booted the computer hope this helps
:)

---

