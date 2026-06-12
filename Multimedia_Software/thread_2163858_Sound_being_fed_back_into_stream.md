---
title: "Sound being fed back into stream?"
date: 2013-07-19
forum: Multimedia Software
---

### Post by papillion on 2013-07-19
When I am on VoIP, everything going through my sound card is being fed back into the audio stream. For example: I can be on a Skype call or an XMPP call and mute my mic. If I play music while my mic is muted, the other end will still hear the music. I've got no idea how to fix this.

Can anyone help?

---

### Post by tgalati4 on 2013-07-19
Open a terminal:  ```
alsamixer
```

Look through the channels and mute the one that is causing the problem.

---

