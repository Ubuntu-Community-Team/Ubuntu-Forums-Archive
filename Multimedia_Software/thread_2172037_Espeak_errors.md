---
title: "Espeak errors"
date: 2013-09-02
forum: Multimedia Software
---

### Post by Herbon on 2013-09-02
I was running "espeak" and got the following errors:

> Sil@peanuttwo:~$ espeak "watt the freak main"
ALSA lib pcm_dmix.c:985:(snd_pcm_dmix_open) unable to create IPC semaphore
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:985:(snd_pcm_dmix_open) unable to create IPC semaphore
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started



How do I stop or silences these errors? Other than this the programs runs fine.

---

### Post by Herbon on 2013-09-03
up

---

### Post by sandyd on 2013-09-03
moved to multimedia and video

---

### Post by Yellow Pasque on 2013-09-03
Those errors are par for the course (it's just espeak trying different outputs until it finds a valid one). To shut them up, redirect to /dev/null
```
espeak something 2>/dev/null
```

---

### Post by kostkon on 2013-09-03
This is a known problem. You can always send the output to paplay or any other audio player of your preference, e.g.:
```
espeak --stdout "this is a test" | paplay
```

---

### Post by Herbon on 2013-09-03
Thank you both!

---

