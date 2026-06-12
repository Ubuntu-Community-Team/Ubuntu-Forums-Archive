---
title: "More than one application playing sound using S/PDIF"
date: 2009-09-02
forum: Multimedia Software
---

### Post by Mononofu on 2009-09-02
Since I recently upgraded my audio setup to a brand new AV-Receiver and a surround system, I of course wanted them to use with Ubuntu.
As connection between my laptop and my receiver I use S/PDIF, since this gives me better quality and surround support.

At first, I couldn't get this to work with Ubuntu at all - sometimes it would play sound, sometimes it wouldn't, and there was never any particular reason why it did what it was doing . . .

Then I found some post somewhere around the web, recommending to create a file '/etc/asound.conf' with this content:
```
pcm.!default {
  type plug
  slave {
    pcm "spdif"
    rate 48000
    format S16_LE
  }
}

```

Since then, audio output worked, but only for one application - the one first trying to play audio, all other would stay mute.
If I wanted audio in another app, I would have to kill the app where audio was currently working and then, and only then, start the app where I wanted audio.

Needless to say, this is still a pain in the *** - everytime I want to play music or watch a movie I have to exit my browser, start the player and then restart my browser. 

Selecting ALSA doesn't change anything - in fact Ubuntu ignored all the changes I made in the GUI, only the file above managed to change the output type. Is there any way to get it to work as it should?

(This is one of the view times were I like the Windows approach better (at least in Windows 7) - there you just plug the cable in, select S/PDIF as output in the mixer and it works. You don't have to configure every app you want to play sound with, and you have one central place to adjust the output volume of each application. Why can't something like this be done for linux?)

---

