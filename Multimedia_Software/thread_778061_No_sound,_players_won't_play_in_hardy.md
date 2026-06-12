---
title: "No sound, players won't play in hardy"
date: 2008-05-01
forum: Multimedia Software
---

### Post by zachthejones on 2008-05-01
Whenever I try to play something in Amarok or Rhythmbox, it signifies it is playing the mp3 or podcast, but it doesn't show on the time chart thingy that it is actually making any progress through the song. When I tried to play a song in VLC, it acted like it was playing just fine, but I have no sound.

I have every volume I can find turned up(from the function keys of the laptop, to the master volume on the panel, to the volume in the media player) - no noise whatsoever.

when I run "aplay -l", this is what I get:
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
so it is detecting my sound card.

When I first installed Hardy (I did a fresh install), I did have sound from the login screens and as it logged me in, but then I used the laptop controls to mute the volume (teachers aren't real big on laptop sounds during lectures...)

I'm sure it's something simple, but I've used up all I could figure out from the different forums to see what's wrong here...

any suggestions would be more than welcome!!! -thanks!

---

### Post by docpepin on 2008-05-01
I have reset the rhythmbox or exaile audio settings to ALSA to get them working again after upgrading my Feisty to Hardy Heron.

---

### Post by zachthejones on 2008-05-03
how do you do that?

Also, I think it has more to do with mp3 compatibility. I was able to listen to podcasts, but when I switch over to mp3s it won't play (in either Amarok or Rhythmbox). The ironic part is that these are tracks I burnt onto my laptop using the same Rhythmbox to encode the mp3s which now won't play them.

the mp3s aren't bad, because I cut a CD of 'em (as mp3s) and are listening to 'em on my mp3 player in my truck.

any ideas?

---

### Post by StitchedChin on 2008-05-03
I went to System --> Preferences --> Sound and changed everything to ALSA - Advanced Linux Sound Architecture.  I had something else listed under Music and Movies in there, and couldn't play MP3s.  Now RhthymBox is working fine for me.
Good luck.

---

### Post by Zorael on 2008-05-04
I had to add a line to **/etc/modprobe.d/alsa-base** to get my Intel HDA sound to work properly. See [http://ubuntuforums.org/showthread.php?p=4869649#post4869649](http://ubuntuforums.org/showthread.php?p=4869649#post4869649) for some more details. (not a howto but contains pointers as to how you might get started in troubleshooting)

---

### Post by UnknownFear on 2008-05-04
I too need help. Everything is at the latest version, I am running Ubuntu 7.10 (will update sooner or later to 8.04). I went to System -> Preferences -> Sound and everything is set to "Auto detect" and I tested each one and they do play sound. But I can't play any music or anything in Rhythem. Some help?

---

### Post by zachthejones on 2008-05-17
UnknownFear, you might want to try playing stuff in other players first, just to make sure there's nothing wrong with Rhythmbox (though I would think that would be the most stable of the players available). Try Amarok, VLC, even Totem.

Also, open up terminal and type "alsamixer" and make sure everything is up that should be.

Other than that, not sure I can help. My problem ended up just being something random. My sound is working great now with no problems. I'm guessing some update patched something up.

---

