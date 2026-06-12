---
title: "Hardy Heron: no sound in browser"
date: 2008-05-24
forum: Multimedia Software
---

### Post by Chr0mis on 2008-05-24
I've got a rather common problem, but can't seem to fix it nonetheless. 

Firefox (2 and 3) and konqueror won't give me any sound on youtube movies or other flash movies. I'm using logitech Z-10 usb speakers and have got sound in the general system, but not in browsers. The system sound preferences (gnome) are set to the usb speaker, I turn up and down the volume using alsamixer and I have tried every solution I could find: 
Installing  libflashsupport, removing it, changing the /etc/firefox/firefoxrc ro aoss, auto and none. 

When i try to get konqueror or firefox to play the sound, I close all the other programs that might produce sounds. I have already tried creating a new user, logging into that user and trying flash with that account. No success. 

I have tried the solutions mentioned in these threads: 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 [http://ubuntuforums.org/showthread.php?t=710641](http://ubuntuforums.org/showthread.php?t=710641)
[http://ubuntuforums.org/showthread.php?t=802564](http://ubuntuforums.org/showthread.php?t=802564)


Now, I am sorry if I should not  have made a new threat for this, but I felt as though my exact problem was not mentioned before and this was the best option. 

Thanks in advance for any help on this, I've been at it for two hours and I'm getting desperate.

---

### Post by ederic on 2008-05-25
Same problem here.

---

### Post by gandaran on 2008-05-25
there's one thing worth trying, install adobe flash 10 beta, some people did resolve their flash sound problems this way, remove the current flash installed and also libflashsupport first.
warning: flash 10 doesn't work on every site yet, works fine on youtube, doesn't work on BBC webpage and crashes firefox on hi5.

---

### Post by Chr0mis on 2008-05-25
Omg, I have just fixed it! The Logitech Z-10 uses a separate sound card and this has to be configured somewhere. Because it's not selected default (even if you've done this in the sound preferences)

The best thing to do (especially for hardy heron users) is install pulse audio. 
run the following command: 
```
sudo aptitude install pavucontrol padevchooser paman paprefs pavumeter pulseaudio-utils
```

(If you don't have libflashsupport you might want to add that one to the list)

And then press alt+F2 and type in pavucontrol. Pavucontrol will show up and if you have a flash movie running (so open youtube before opening pavucontrol) you can rightclick on the volume bars and specify the RIGHT sound card, in my case USB 2. Screenshot can be found below: 

[IMG]http://i12.photobucket.com/albums/a238/ffolip/llama.jpg[/IMG]

So yay, my sound problem is fixed! Now I can happily check out the pi song on youtube.

---

### Post by beebelo on 2008-05-25
Hmmm... I had the same problem--which started yesterday after an update--but my solution was different.  

I had installed VLC and made it the default multimedia app in Firefox's add-ons and extensions.  In the meantime, they pushed an update which installed some g-streamer stuff.  I noticed that Firefox was trying to use both the g-streamer and the VLC plugin.  I disabled everything except the original VLC plugin, and my browser sound came back.  

All sound seems to be working now, but I haven't found good info on Pulse Audio configuration, so I'm not really comfortable about this yet...  My system has both ALSA and Pulse Audio.  Are we supposed to have both?  (Ubuntu Studio.)

---

### Post by wolfen69 on 2008-05-25
> **beebelo said:**
>  My system has both ALSA and Pulse Audio.  Are we supposed to have both?  (Ubuntu Studio.)

yes, it comes with both.

---

### Post by charlesbw on 2008-05-25
i have a problem similar to yours (That is...there is no sound on youtube), except that youtube stops playing exactly after 2 seconds.  And i tried multiple videos.

---

### Post by Chr0mis on 2008-06-04
> **charlesbw said:**
> i have a problem similar to yours (That is...there is no sound on youtube), except that youtube stops playing exactly after 2 seconds.  And i tried multiple videos.

An update and a new profile in firefox fixed that with me.

---

### Post by rcorrea on 2008-06-05
i have that exact same problem even have the z-10 speakers too lol  i did everything u told me  played a youtube video then typed pavucontrol but in the playback tab there there shows nothing   says no streams available


didnt have this problem with fedora

---

### Post by Darris on 2009-12-11
OMG
jesus christ
thank you
lol
i spent so long doing and undoing everything i found in all of the other forums

and then it was something that simple
i looked at it and i was kind of dumbfounded for about 5 minutes with my mouth hung open before i wrote this reply
xD
worked like a charm

---

