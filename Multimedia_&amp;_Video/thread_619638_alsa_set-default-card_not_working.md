---
title: "alsa set-default-card not working???"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by jeremija on 2007-11-21
i have two sound cards on my laptop, internal (HDA Intel) and a Sound Blaster MP3+.
i recenty upgraded from to gutsy and i am finally able to play multiple sounds at one time on my MP3 card.
however, when i disconnect the usb card, i have to manually edit  the ~/.asoundrc.asoundconf file and change two lines from:
```
!defaults.pcm.card MP3
defaults.ctl.card MP3

```
to 
```
!defaults.pcm.card Intel
defaults.ctl.card Intel
```
and it works!
But I used to use a command "asoundconf set-default-card Intel" to set the Intel card as the default one back in Fiesty, but when i use it in Gutsy, nothing changes... 
Does anybody know why? :(

p.s. back in fiesty, when i disconnected the usb card, HDA Intel automatically became the default one, but now alsa gives an error: could not open resource for writing, and when i run gstreamer-properties and try to test the sound, it gives the error in command line: "playback error on device 'default': No such device" (this is when the usb card is disconnected, which is the default one). If I manually edit the file mentioned above, everything is fine...

Is there any way to make linux automatically set the Intel card as the default one if MP3 card is not connected?
Thanks...


EDIT:
i realized that i need to use the command sudo before asoundconf and then setting the default card works (i don't remember that i needed to do this in Fiesty), but then it gives a warning:
```
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.
```
:/
so, i'm asking again, is there any way to do this automatically (if there is no usb card connected, make hda intel default one)?

---

