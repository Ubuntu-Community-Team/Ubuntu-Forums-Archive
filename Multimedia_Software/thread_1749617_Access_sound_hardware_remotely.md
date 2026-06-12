---
title: "Access sound hardware remotely"
date: 2011-05-04
forum: Multimedia Software
---

### Post by davidsm49 on 2011-05-04
Hello, I've installed Ubuntu 11.04 on a Zotac and I'm setting up to allow remote access from a Vista machine using NoMachine (NX) and PuTTy (SSH) tools. I'm having a problem with the Zotac's USB microphone/Headphones hardware just disappearing from view on the Vista machine. When I'm directly logged in on the Zotac's system console, I can use a Vista machine to remotely connect (either NX or PuTTY) and bring up the gnome-sound-recorder and see the two pieces of sound hardware (USB microphone and the onboard soundcard). It's part of a security system for when I'm traveling and the place is emply. I'm not trying to spy on someone. The IP cameras don't have a microphone. Anyway, everything works fine remotely (on the Vista machine) until I log off the Zotac's system console. When I do that, the soundcards are no longer seen remotely on the Vista machine. If I log back onto the Zotac's console, then the soundcards are magically back at the remote computer showing up within the gnome-sound-recorder utility. It doesn't appear to be pulseaudio (I could be wrong).  I guessing some X11 environment setting is getting wacked when I logoff Zotac's console and I lose it remotely on Vista. I could just stay logged onto the console, but that's not even a decent hack. Thanks.

---

