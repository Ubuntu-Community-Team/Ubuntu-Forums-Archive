---
title: "usb midi"
date: 2009-01-11
forum: Multimedia Software
---

### Post by venumus on 2009-01-11
havin the damnedst time figuring it out. 

so im using virtualbox to run xp to try to make things smoother but i dont know if the midi keyboard is being controlled by xp or not. im pretty sure not but i havnt installed any programs that would use it. but i figured it would come up under my computer.

ive followed the other guides of editing the /etc/fstab file

---

### Post by DonnieP on 2009-01-19
> **venumus said:**
> havin the damnedst time figuring it out. 

so im using virtualbox to run xp to try to make things smoother but i dont know if the midi keyboard is being controlled by xp or not. im pretty sure not but i havnt installed any programs that would use it. but i figured it would come up under my computer.

ive followed the other guides of editing the /etc/fstab file

If you're wanting to get a midi keyboard working in Ubuntu, here's one way to do it:  try installing qjackctl, fluidsynth and fluid-soundfont-gm (you'll need all three).  To play the keyboard, first run JACK Control from the Applications | Sound & Video menu (just run it, don't set anything).  Then in a terminal run:
```
fluidsynth /usr/share/sounds/sf2/FluidR3_GM.sf2
```
This will put your terminal into a fluidsynth shell.  Now go back to JACK and click the Connect button and then the ALSA tab on the Connections dialog.  You should see your keyboard on the left and FLUID Synth on the right.  Click each of these so that they are both highlighted and then click 'Connect'.  A little line will connect the two.  You should now be able to hear your keyboard.  You may have to jiggle your system volume and/or go to the terminal fluidsynth shell and adjust the gain:
```
gain 5
```
This would set the gain to the highest setting.  Check the fluidsynth man page for how to see what the 16 channels are set to and how to change which instrument a channel is set to.  You select the channel to play from your midi keyboard, not fluidsynth.

---

