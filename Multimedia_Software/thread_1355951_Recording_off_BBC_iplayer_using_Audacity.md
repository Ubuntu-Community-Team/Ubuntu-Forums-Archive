---
title: "Recording off BBC iplayer using Audacity"
date: 2009-12-15
forum: Multimedia Software
---

### Post by hamstermoon on 2009-12-15
I have done this in Vista but was wondering if it was possible to do it in Ubuntu? What do I set the variouus dropdown menus to do to this (please don't ask me to stick something in the terminal - I am a newbie on that front! :confused:).

---

### Post by Sin@Sin-Sacrifice on 2009-12-15
Never used BBC iplayer but I know you can use youtube-dl (might need a few tweaks) to download videos. I use it for sites other than youtube. If it's audio streams you're after then mplayer can do that with a command like ```
mplayer mms://site-streaming-audio.com -ao pcm:file=/home/username -vc dummy -vo null
``` Assuming the audio stream is an mms site and you want to copy it to your home folder.

---

