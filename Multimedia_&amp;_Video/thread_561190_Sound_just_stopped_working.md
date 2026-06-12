---
title: "Sound just stopped working"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by m0sand on 2007-09-27
Hello, I was using my computer yesterday just fine. Played music and video etc but suddenly later on in the day when I got back my sound was gone. The first messages I got when I went into preferences -> sound was that the "Resource is busy" etc. I do not what happen but perhaps firefox is guilty? I don't know cus firefox just stopped responding so I had to force an shutdown of firefox.

Anyways, here's some info:

cat /proc/asound/cards
 0 [CK8S           ]: NFORCE - NVidia CK8S
                      NVidia CK8S with ALC850 at irq 18

I also attached a strace log from when I tried playing an mp3 with mplayer

edit; I tried shutting down all applications that might be 'blocking', nothing has worked. I have rebooted several times, nothing has worked.

---

