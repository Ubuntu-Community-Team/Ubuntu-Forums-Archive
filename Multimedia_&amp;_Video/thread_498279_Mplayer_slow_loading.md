---
title: "Mplayer slow loading"
date: 2007-07-11
forum: Multimedia &amp; Video
---

### Post by Jexel on 2007-07-11
I installed mplayer and it was running fine, however, recently it just slowed down tremendously when I try opening it up especially when double clicking a video file.

I'm using the x11 driver...

Sorry but i'm not sure what details I need to provide but i've searched around and can't seem to find a solution...

---

### Post by thespinesplitter on 2007-07-12
if you use gnome i suggest you just use the good 'ol Totem player, if anything try installing the mplayer-nogui package for those videos that just dont seem to work under totem, rightclick the file and select open with then look for your mplayer after that everytime you doubleclick the file should start to play in a window, there arent any button controls but you can fastforward and rewind with the arrow keys and fullscreen with the F key, Spacebar pauses the playback

EDIT: also you might want to change the configuration in /etc/mplayer/mplayer.conf, modify vo= to read vo=gl or gl2 but only IF you have 3d acceleration
remember to uninstall the current mplayer package

---

### Post by thespinesplitter on 2007-07-12
i guess i should have added that mplayer has died on me that way several times, so i chose to use the gui-less package "et tabula rasa"

---

