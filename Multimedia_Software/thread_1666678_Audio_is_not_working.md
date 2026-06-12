---
title: "Audio is not working"
date: 2011-01-14
forum: Multimedia Software
---

### Post by bhubi2020 on 2011-01-14
Hi,

        When I play the audio songs, sound does not come but song is running.
After few seconds I got an error.

" Pa_stream_writable_size() failed: connection terminated. " 

Please help me how to solve this...

---

### Post by lidex on 2011-01-16
Try this, removing prior pulseaudio config settings.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

