---
title: "No Sound Intel High Definition Audio ALC883"
date: 2008-10-29
forum: Multimedia Software
---

### Post by lch503 on 2008-10-29
Hey
I have just installed ubuntu 8.0.4 and have been unable to get my sound to work. I have used various forum websites and found the details of my sound card. It is a Intel High Definition with a Realtek ALC883 chipset. I am a newbie at ubuntu so if you need me to post anything would you mind telling me the code necessary to give the details.
Thank you very much in advanced.

Leon

---

### Post by cozmicharlie on 2008-10-29
I am sorry that I can't help you directly but I can point you to this thread that may help ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)).  If you still have problems you should post to that thread - the OP is very good about helping people with sound problems.

Good luck

---

### Post by lch503 on 2008-11-01
Thank you. I managed to find that it was 1 line of /etc/modprobe.d/alsa-base, specifically
options snd-hda-intel model=laptop-eapd
added that and on restart sound started working.

Thank you

---

