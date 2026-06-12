---
title: "Why is Ubuntu not detecting headphones?"
date: 2016-06-13
forum: Multimedia Software
---

### Post by Sagar_B_Hathwar on 2016-06-13
Installed Ubuntu 16.04 on my Alienware 17 R3. When I plug in the headphones, Ubuntu just ignores it. 

Output of also-info is here [http://www.alsa-project.org/db/?f=eab9df3cd1fbe887705f41603d8d9cc2c2833911](http://www.alsa-project.org/db/?f=eab9df3cd1fbe887705f41603d8d9cc2c2833911)

Any help is appreciated. Thank you

---

### Post by Yellow Pasque on 2016-06-16
```
alsamixer
```

Look for these controls in alsmaixer and see if you can enable them:

Simple mixer control 'HP/Speaker',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

Simple mixer control 'HP/Speaker Auto Detect',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]

---

