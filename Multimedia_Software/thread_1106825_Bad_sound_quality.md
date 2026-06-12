---
title: "Bad sound quality"
date: 2009-03-26
forum: Multimedia Software
---

### Post by IvanInsa on 2009-03-26
Good day

Im new to Ubuntu, just switched from Windows to Ubuntu 8.10 Desktop Edition about a week, everything works great except for the SOUND.It has very bad quality sound,can some1 please help, im using an TOSHIBA SATELLITE P100 Laptop

Thanks 

Ivan Insa

---

### Post by IvanInsa on 2009-03-26
Anyone?

---

### Post by Reeman on 2009-03-26
> **IvanInsa said:**
> Anyone?

Try the command in a terminal. *Found under accessories in Ubuntu...just like Windows.. yuck!*:lol: 

alsamixer -c 0

Alsamixer is really easy to use ...just use the side arrow key to navigate and the up-down to set the controls. To mute or activate a device just press m ...there are options to save your mixer settings with commands after you exit alsamixer with the command.... alsactl -store  

If you have your mike pre amp up or something else up at 100% it might just be that you are distorting things. The reason why you need to use the old ncurses terminal app is that Gnome Mixer which is using the pulse audio server will not show all the device controls.   

You can try to change your pulse/gnome desktop mixer preferences, but sometimes you might need to do more than that if the pulse server is not friendly with your device. Here's hoping that is not the case!

All devices and controls that are available in the alsa device controls will show up with the native alsamixer. But with some sound chips this can be a problem with the pulse audio server! 

If you open the Gnome mixer most likely all you will see is one slider. So to see more devices you need to re-set your mixer preferences. 

If there are more controls you will have to make them visible to the pulse audio server. This problem is quite common and should be easy to fix.:-k

---

### Post by IvanInsa on 2009-03-27
Reeman, i managed to change the settings in Alsamixer, seems that PCM was in full volume, but im having troubles saving with the command you gave me i think something is missing , maybe i need to specify the sound card?

BTW does WINAMP works in Linux?


Tks

---

