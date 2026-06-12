---
title: "basic alsa question"
date: 2010-07-10
forum: Multimedia Software
---

### Post by methodtwo on 2010-07-10
Hi
It was recommended to me that I remove pulseaudio and re-install alsa.All the howtos on reinstalling alsa had instructions for re-installing alsa from the source.Is it possible to re-install alsa from the repos?.If so what are the necessary packages that I need to install, for a complete re-install of alsa?.

---

### Post by benerivo on 2010-07-10
You can reinstall any part of the os from the repos. I think alsa is reinstalled with alsa-base.

```
sudo apt-get --reinstall install alsa-base
```

---

