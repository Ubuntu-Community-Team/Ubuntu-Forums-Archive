---
title: "HowTo: pulseaudio and pysol or any sdl game in hardy"
date: 2008-05-24
forum: Multimedia Software
---

### Post by jeffus_il on 2008-05-24
Install libsdl1.2debian-pulseaudio
Add this line to your .bashrc file or other startup script:
> export SDL_AUDIODRIVER=pulseor do this in a terminal to test before making changes:
```
export SDL_AUDIODRIVER=pulse
pysol
```

---

