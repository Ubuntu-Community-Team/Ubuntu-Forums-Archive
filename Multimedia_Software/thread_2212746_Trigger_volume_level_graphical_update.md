---
title: "Trigger volume level graphical update"
date: 2014-03-22
forum: Multimedia Software
---

### Post by Michael_Cieslinski on 2014-03-22
Hello, Ubuntu community. In my first post ever, I'd like to ask an audio-based question. I have successfully installed xbindkeys and configured it to allow my Logitech Anywhere Mouse buttons to control the volume.
I'm using:
```
pactl set-sink-volume 0 -- +/-10%
```
depending on the button pressed. It works, however, it allows the volume to go above 100% and I do not wish to damage my speakers. I was wondering if there was a way I could cause the system to display the volume level update panel that shows, for example, when the Fn+Volume keys are pressed on my keyboard, after I use this command so that I can tell when I'm maxed out. I've been searching everywhere, but all I can find is terminal commands to change the volume (in a way that also doesn't show the volume level panel I'm looking for.)

Any help is appreciated!

---

### Post by grumblebum2 on 2014-03-22
You could use easystroke to simply assign your Fn+Volume key to a mouse button.
[http://sourceforge.net/apps/trac/easystroke/wiki/Documentation](http://sourceforge.net/apps/trac/easystroke/wiki/Documentation).

---

### Post by Michael_Cieslinski on 2014-03-23
I'll try this, but I was hoping to find a way to do it using what I already have. Thanks!

---

### Post by Michael_Cieslinski on 2014-03-24
Calling this solved. The solution is not exactly what I was looking for, but works exactly how I wanted it to. Thanks, grumblebum_2.

---

