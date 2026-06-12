---
title: "No sound in firefox/flash applications"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by sticks on 2007-04-10
When I first installed Edgy I could use Firefox to play video clips from sites like
Youtube and I got clear audio.  

After installing some packages like llibsdl1.2-debian-all, libopenal0a, alsa-oss, 
oss-compat and modifying the file asoundrc with the lines:
pcm.!default {
     type hw
     card 0
}

ctl.!default {
     type hw
     card 0
}
to improve the sound quality of some games, the audio from flash videos in
Firefox is now broken.  I can watch videos in Youtube or Google videos but
can't hear any sound anymore.

I tried the "sudo gedit /etc/firefox/firefoxrc
FIREFOX_DSP=”aoss” fix, but this didn't work.

Does anyone know a way I can once again enable sound when I watch flash 
videos in Firefox?

---

### Post by deadgobby on 2007-04-10
The problem is simple. You install ALSA. So you need to turn up the volume on the old ALSA mixer or double click on the the Speaker Icon. To install ALSA mixer you have a couple of choices. 
[http://ubuntuforums.org/showthread.php?t=405615](http://ubuntuforums.org/showthread.php?t=405615)

Gobby

---

### Post by sticks on 2007-04-10
> **deadgobby said:**
> The problem is simple. You install ALSA. So you need to turn up the volume on the old ALSA mixer or double click on the the Speaker Icon. To install ALSA mixer you have a couple of choices. 
[http://ubuntuforums.org/showthread.php?t=405615](http://ubuntuforums.org/showthread.php?t=405615)

Gobby


I already installed Alsa from the repository and adjusted the volume from
the mixer.
Do I have to install v. 1.0.13 or 1.0.14 from the Alsa website to get it to 
work properly?

---

### Post by sticks on 2007-04-14
It seems that there is no working solution for this problem
with ubuntu.
Are there any other distros that can handle the simple task
of allowing firefox to play flash videos with sound?
Gentoo, Mandriva, Mepis?
There must be some distro that can handle this very basic
task if ubuntu is not able to.

---

