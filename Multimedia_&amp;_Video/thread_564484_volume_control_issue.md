---
title: "volume control issue"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by lrdnitecon on 2007-10-01
im running gutsy on my compaq presario v5000 laptop. my no volume light on my computer is on and the icon on the top toolbar by the clock says mute, the soound from games, music, and movies are still comming on. any ideas on how to get it to stop that? thanks for any help.

---

### Post by lrdnitecon on 2007-10-01
anyone?

---

### Post by mpeters13 on 2007-12-28
I'm in the same boat. I can't control the sound with these buttons. The sliders move, but the volume doesn't actually change. Additionally, it seems that I can set the PCM device as the default slider and modify it in the tray.... but I still can't use the buttons. A fix would be very nice.

---

### Post by GrouchoMarx on 2007-12-28
> my no volume light on my computer is on and the icon on the top toolbar by the clock says mute, the soound from games, music, and movies are still comming on.

> I can't control the sound with these buttons. The sliders move, but the volume doesn't actually change.

You may need to switch the track that is being controlled by the volume control. Right-click on volume > preferences and depending on your soundcard you can select from a number of tracks. The one that controls volume on mine is "Headphone".

> I can't control the sound with these buttons. The sliders move, but the volume doesn't actually change. Additionally, it seems that I can set the PCM device as the default slider and modify it in the tray.... but I still can't use the buttons.

To get your keyboard volume keys working, you must again change the track, but this time in the gnome preferences: system > preferences > sound > Devices > Default Mixer Tracks > and then select whichever track enables functionality, for me it was "Headphones". Yes, it's strange to have to do the exact same thing in to separate places, but hopefully it gets it working.

---

### Post by Torgas Prim on 2007-12-29
I have sound, but when I try to open the volume control I get this:

Failed to start Volume Control: Failed to execute child process "gnome-volume-control" (No such file or directory)

I reinstalled Gnome packages.
I recompiled alsa just to be safe, but still no volume controls.

Anyone know where to point me for this?

Thanks

edit: nvm, I got it, I just went through all my Gnome packages and reinstalled most of them again...fixed. :)

---

