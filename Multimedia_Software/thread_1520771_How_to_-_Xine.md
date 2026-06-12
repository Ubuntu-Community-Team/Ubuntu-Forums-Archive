---
title: "How to - Xine"
date: 2010-06-30
forum: Multimedia Software
---

### Post by slyblade900 on 2010-06-30
First off its just 3 days i'm using Ubuntu or for that matter linux. I got a perfectly working system with ALSA sound engine . But then i needed to sync my ipod so i installed amarok which (i think) changed the sound card or sound engine or whatever to Xine. Now no matter how i adjust the volume control on top of my desktop . Xine is always at maximum volume . Every song i play will be at maximum volume. Even in the internet youtube plays with maximum volume. But i can control the volume with amarok though when i play songs in amarok. But i need a way to control the over all system volume. I.e i need to change the sound engine back to ALSA. Help please. Ihave no idea what i did wrong ( other than install amarok ).

---

### Post by cchhrriiss121212 on 2010-06-30
Xine is a media player so it should not have control over your whole system sound. Run alsamixer in a terminal and adjust the volume for your card there, if you don't like terminals there is an alsamixer gui in the repos.

---

### Post by gandaran on 2010-06-30
have you tried the sound preferences? lift click sound icon in panel » preferences.

---

### Post by slyblade900 on 2010-06-30
THanks guys i did something really funny and it works now . I upgraded my ALSA version ( although it was at the latest version already) so now i think every thing is fine now . and althought i like gui, like all advanced users i WANT to learn the terminal.

---

