---
title: "Audigy ZS platinum problems with Gutsy."
date: 2008-10-02
forum: Multimedia Software
---

### Post by pgmer6809 on 2008-10-02
1. GNUSOUND crashes linux. I need to reboot.
2. Alsamixer from the cmd line works OK. The mixer from the gnome applications menu also works after a fashion, but some screens give errors that it does not like the directory name it is trying to use, because the directory name contains a comma.

i.e. Edit Soundcard properties gives this message:
Bad key or directory name: "/apps/gnome-alsamixer/display_sliders/SigmaTel_STAC9750,51-Master": `,' is an invalid character in key/directory names

However both mixers, and the volume control applet will let me set volume, mute/unmute etc. for all the devices.

3. The system=>preferences=>sound menu does not have any input device in it. I can TEST the sounds for all the output devices and they work fine.
THe audioConferencing section has a 'capture device' but no matter what I set it to, when I click TEST I get:

---

