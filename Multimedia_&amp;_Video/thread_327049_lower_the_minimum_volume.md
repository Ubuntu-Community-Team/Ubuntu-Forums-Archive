---
title: "lower the minimum volume?"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by tracer on 2006-12-28
I bought a USD sounds driver (the Creative Xmod device), which works well, except that the quietest volume setting brings the volume a bit louder than I would like to listen to it through headphones.  Turning it up to 25% or so would be way too loud, and 100% would shatter your ear drums.

I would like to lower the lowest volume level so that it's inaudible, then turning it up will bring it to a normal listening range, then turning it up more will make it loud.

alsamixer and amixer work to control the volume.  The lowest possible setting is 1, which corresponds to 2%:

amixer set 'PCM' 1

This still make the volume just a bit too loud.  Turning it down to 0 mutes the sound completely, which obviously doesn't work.

Is there anyway to adjust the sound range of a device, either through a kernel setting or through some sort of software control?

---

### Post by deadgobby on 2006-12-28
There is GNOME ALSA Mixer that is easy to install through synaptic. All so if you have head phones with a volume control, you may want to check the setting. Yes, believe it or not there is head phones with a volume control knob. It is some thing that makes things easy than dig out the Ipod out of your pocket. 
Gobby

---

### Post by tracer on 2006-12-28
headphones with an analog volume control would be one way to deal with it, but I'd rather not have to go that route if there's some software control that can reduce the lowest volume.

---

### Post by deadgobby on 2006-12-28
As I said try installing the graphic version GNOME ALSA and see if that punches the right one.
GObby
 OH of you are recording sound or inputing sound through the sound card. Like a 4 track player. You need to adjust the input. Like line in for a 4 track player or mic in for a mic or record player.

---

### Post by mesmerize on 2007-02-26
I have a creative xmod too but it doesn't work.What did you do? I'm running Kubuntu 6.10

---

### Post by mesmerize on 2007-03-04
Fixed.Works fine on Ubuntu Dapper.

---

### Post by diebels on 2007-03-27
Works on edgy, feisty too: [http://ubuntuforums.org/showthread.php?p=2360690](http://ubuntuforums.org/showthread.php?p=2360690)

---

