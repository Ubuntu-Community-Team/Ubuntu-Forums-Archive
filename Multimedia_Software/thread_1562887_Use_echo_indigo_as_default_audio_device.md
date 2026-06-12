---
title: "Use echo indigo as default audio device"
date: 2010-08-28
forum: Multimedia Software
---

### Post by baltazar3 on 2010-08-28
I use an echo indigo audio card. When I do aplay -l I see this card, and I can ouput audio through it by specifically telling mplayer to use this (alsa) device. Now I want to use this card as default for all audio. At the moment the default is pulseaudio through the built in soundcard. How can I change this? Im running Ubuntu 10.04. Thanks

---

### Post by kostkon on 2010-08-28
Did you try in System &#8594; Preferences &#8594; Sound?

---

### Post by baltazar3 on 2010-08-28
Yes I did. At least I tried to change the device under the hardware tab. There are two devices there, but system sounds get routed trough internal audio no matter which of them I choose.

---

### Post by kostkon on 2010-08-28
> **baltazar3 said:**
> Yes I did. At least I tried to change the device under the hardware tab. There are two devices there, but system sounds get routed trough internal audio no matter which of them I choose.
You can set a default device in the *Output* tab.

---

### Post by baltazar3 on 2010-08-28
Yes, that works. Thanks.

---

