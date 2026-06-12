---
title: "I'm looking for an app that does a slideshow that will loop in a random order."
date: 2017-08-18
forum: Multimedia Software
---

### Post by kamrynborden on 2017-08-18
EOG and Shotwell both do endless loops however there is no option to put them an random order. Also, there one that'll play videos in the folder.

~ Kamryn

---

### Post by again? on 2017-08-18
```
sudo apt install gthumb
```

Open gthumb and set your slideshow preferences.
[ATTACH=CONFIG]276435[/ATTACH]

In gthumb select a directory and hit the presentation icon at top right.
or
run from command line.
```
gthumb -fs [COLOR="#808080"]/path/to/picture/directory[/COLOR]
```

If you put an mp3 song file in the target directory it will play along with slideshow.

Escape key quits slideshow.
F11 toggles fullscreen.
Space next image
Backspace previous image

Tested in UbuntuGnome 17.04.

[COLOR="#B22222"]Edit[/COLOR] For EOG you can install eog-plugins and enable the "Slideshow Shuffle" plugin in preferences>plugins.

---

### Post by kamrynborden on 2017-08-20
Thank you. It works great. :)

~ Kamryn

---

