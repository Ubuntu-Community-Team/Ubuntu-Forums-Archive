---
title: "Clear sound"
date: 2009-03-20
forum: Multimedia Software
---

### Post by tcwolfpack on 2009-03-20
Hey, 

New to the forums and new to ubuntu. Have spent the last couple of days frustratingly trying to get my surround sound to work and finally have been able to do so. 

However my sound clarity is really poor. 
I'm currently running pulseaudio.
if anyone could help me that would be greatly appreciated

---

### Post by mastermindg on 2009-03-20
Pulseaudio is strictly a sound server, it doesn't modify the sound from source at all. I've never heard of clarity issues, but I would imagine it would have to do with setting channels, etc.

Check out this page: [https://help.ubuntu.com/community/Sound]("https://help.ubuntu.com/community/Sound")

---

### Post by scry on 2009-03-20
You should try to lower PCM to 80% or so... It gave me much better sound.

---

### Post by markbuntu on 2009-03-20
If your sound is scratchy or stuttering you can edit these lines in the file /etc/pulse/daemon.conf to look like this
```

default-fragments = 5
default-fragment-size =25

```
There are also some sound cards/chips that can only be fixed with an ALSA upgrade so you may want to consider that if this does not work for you.

---

