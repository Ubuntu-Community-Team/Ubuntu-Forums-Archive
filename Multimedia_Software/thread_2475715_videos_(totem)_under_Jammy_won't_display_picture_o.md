---
title: "videos (totem) under Jammy won't display picture of audio media"
date: 2022-06-06
forum: Multimedia Software
---

### Post by JamButty on 2022-06-06
Videos/Totem has always been the most reliable and convenient player of audio files for me, but since installing Jammy, it will no longer display any picture associated with each audio file (e.g. album cover or similar). VLC still can. Has anyone else had this issue and found a solution?

---

### Post by JamButty on 2022-06-14
Tried de-intalling/reinstalling via flatpak. no change.
Have searched extensively for any related references and the only ones I find are very old (2008-2010) and look no longer relevant. 
I would like to try installing a prior version of Totem, but I have found no source. The project website, wiki.gnome.org/Apps/Videos, does not offer it and I've found no sources elsewhere.
Problem reported to the package "issues" page.

---

### Post by JamButty on 2022-06-20
Per package admins:
"It's been removed by design. In 3.38 we removed associations to audio files, and during the port to OpenGL, we removed showing the audio file covers, and replaced it with an "audio only" icon (in [5e5805c5]("https://ubuntuforums.org/GNOME/totem/-/commit/5e5805c58e34b870ebc3c37114b8c70b1674cb0b"))."

---

