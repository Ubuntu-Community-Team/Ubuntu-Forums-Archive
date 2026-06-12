---
title: "Sound problem in linux"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Epimetheus on 2007-10-19
I'm sure this is a known problem but maybe there is a solution out there somewhere. I have noticed that there is a pretty big defect in the sound system of linux/ubuntu, I can't run more then one audio application at the same time. Or rather, multiple mp3-players or such are possible but if I run, for example, Rhythmbox or firefox with flash, I can't run applications that "makes" sound, as example espeak, hydrogen and such applications. Hydrogen for example runs but doesnt produce any sound, and espeak just outputs:
```
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000

```

I've had this problem since I started using linux and ubuntu is the only dist i've run seriously so I wouldn't know if this is equal on other dists.

I'm sure there is a solution for this but i have so far not found it.

---

