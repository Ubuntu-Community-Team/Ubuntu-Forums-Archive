---
title: "Using pulseaudio with jack"
date: 2009-11-19
forum: Multimedia Software
---

### Post by oddhyena on 2009-11-19
I have been trying to use pulseaudio with jack so that I can record audio that most applications play. Nothing I do works. I cannot get pulseaudio compiled from source with jack support because of some "No package 'sndfile' found" error even after I installed it. Is there some kind of way to have pulseaudio become available in jack's connections so that I can use it like a jack program and connect it to various applications? I searched the forums and googled around and nothing works that I try. Does ubuntu studio have this kind of functionality? Pulseaudio right now is working fine for me, so is jack, it's just getting them to work together that's my problem. I'm using ubuntu 9.10

---

### Post by markbuntu on 2009-11-20
motin has a thread about that around here somewhere.

---

### Post by border on 2009-12-12
maybe stupid, but did you install libsndfile-dev, and not (only) libsndfile?

something like:

```
sudo apt-get build-dep pulseaudio

```
should install the necessary dependencies

cheers

---

