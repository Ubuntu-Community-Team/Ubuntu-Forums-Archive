---
title: "gnome-alsamixer applet for panel!?"
date: 2012-09-25
forum: Multimedia Software
---

### Post by Jordiston on 2012-09-25
i have uninstalled pulseaudio and got rid of all the audio problems i've been having. although it also got rid of my audio indicator on the top panel. i use alsa now with gnome-alsamixer. got it to work with my audio hotkeys. but i would still like to have that indicator back. i searched around the web and couldnt find anything but if anybody knows how or has gotten an indicator to work with alsa id be quite happy to know how to do that!

---

### Post by GreenWhite on 2012-09-26
If volume indicator not showing;

go to Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: volumeicon  OR (point to /usr/bin/volumeicon)
Comment: Show desktop volume control

Restart.

---

### Post by Jordiston on 2012-09-27
It doesn't work, I'm pretty sure it's because I deleted pulseaudio.
Don't think their is a sound indicator made for people who only use alsa. I despise pulseaudio but I love indicators, so Im going to make my own using python (hopefully). It's going pretty good so far. Just need to know how I can save the terminals response to a command like "amixer get Master".
Ima also start a new thread in a more appropriate category for this question.

---

### Post by Jordiston on 2012-09-27
finally got it! thanks to spjackson who answered my other post!
it would be

volume =  subprocess.check_output("amixer get Master", shell=True)
print(volume)

---

### Post by Wolfram23 on 2012-10-04
I've done the same thing (remove pulseaudio) and now I have no sound whatsover. Gnome-alsamixer doesn't show any sound device, and neither does the default sound menu anymore. Before removing pulse, it showed my GPU - I've got a G210 HDMI output. I've installed all the alsa stuff I found following 2 separate guides, but no dice.

Anyway, thought at the least I could get the sound icon back, but I don't have the foggiest clue what your code means/how to input it.

Help?

---

### Post by olspookishmagus on 2012-10-06
> **Jordiston said:**
> ...
i searched around the web and couldnt find anything but if anybody knows how or has gotten an indicator to work with alsa id be quite happy to know how to do that!

How about this?
[http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/)

---

