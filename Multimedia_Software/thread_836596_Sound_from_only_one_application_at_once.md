---
title: "Sound from only one application at once"
date: 2008-06-21
forum: Multimedia Software
---

### Post by TurboFreak on 2008-06-21
Hello
I switched to Hardy a few days ago.
First i updated but then had to reinstall completely due to another problem.
However in both cases i never got sound from more then one application at once.

For example:
I first start Firefox and watch a Youtube video (it plays sound and all).
Then i load a mp3 in Totem but the mp3 does not start to play.
Or, if i first load a mp3 in Totem and start Firefox later for a video, the mp3 plays fine but the video plays without sound.

That problem never occurred with Feisty or Gusty.
I have no idea what to do about it.
Hope someone can help me with that.

---

### Post by M4rotku on 2008-06-21
I have this same problem.  I have to close my online game in Firefox and start my Amarok to be able to listen to my music.  It's like only 1 app can use the sound driver at a time.

---

### Post by benerivo on 2008-06-21
I'm only guessing here, but it may be a problem with using pulseaudio which has been included by default in 8.04. If you can remove it from the startup programs in System>Preferences>Sessions, or uninstall it, then it might be okay again.

---

### Post by TurboFreak on 2008-06-21
Just tested a game together with Totem and Rhythmbox. There is no problem playing sounds at the same time with those.
Only Firefox is mute when starting it with a video after the other apps.
The other way around the other apps are all mute and Firefox plays the Video with sound.
So it seems to be a problem only with Firefox.

@M4rotku: Is it the same for you, too?

Maybe then it's the flash extension used in Firefox?

I tried playing sound from Firefox in other ways than with flash, but only came up with a wav file. This is then played by Totem within Firefox, which i now already know works with other applications and it does in this case, too.

I'd like to uninstall the flash player plugin, to get the same message again when trying to play a flash video, which then would give me the option to install another plugin instead.
Unfortunately i was not able to uninstall but only to deactivate it, which is not enough to get the message back.
Tried to delete it manually from the extensions folder too but there was nothing in there.

---

### Post by magnus0 on 2008-06-21
just install libfhaslsupport and then firefox and other players can have sound at the same time

```
sudo apt-get install libflashsupport
```

---

### Post by benerivo on 2008-06-21
here's the official mention of the flash/pulseaudio problem (scroll down slightly) including a fix.

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)


EDIT - the 'fix' is exactly what magnus0 says.

---

### Post by TurboFreak on 2008-06-21
Yes, it works now.
Thank you two very much! ^^

---

### Post by M4rotku on 2008-06-21
Yah, it was the same problem for me, Firefox only.

I installed the thing and if it worked for you then it sounds good to me :popcorn:

---

