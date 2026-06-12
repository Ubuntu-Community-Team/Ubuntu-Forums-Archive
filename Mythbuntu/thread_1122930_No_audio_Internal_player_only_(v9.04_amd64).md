---
title: "No audio Internal player only (v9.04 amd64)"
date: 2009-04-11
forum: Mythbuntu
---

### Post by muffinito on 2009-04-11
Hello, I made a new mythbuntu box to replace my old one.
Everything works fine except the audio on live tv and recorded tv. It actually records audio fine because I can just open mplayer and plays with sound anything on /var/lib/mythtv/recordings.

I believe that is an issue with the internal player or maybe an pulseaudio.

mythvideo, apple trailers, even firefox (youtube) plays ok.

Any help will be appreciated.

Intel D945GCLF2 with
 PVR-500.
Mythbuntu 9.05 beta amd64.
Testing launchpad reps on sources

---

### Post by muffinito on 2009-04-15
Ok I just figure it out. It was set to ALSA:Analog. just changing it to ALSA:Default made it work.

---

