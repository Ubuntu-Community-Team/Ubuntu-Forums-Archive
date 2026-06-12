---
title: "Amarok Audio Trouble"
date: 2010-01-11
forum: Multimedia Software
---

### Post by Fernando Hernandez on 2010-01-11
I had to reboot my computer, and when I booted back up, suddenly a message appeared telling me my audio devices weren't working.  I should have taken a screenshot of it...but I get a similar message every time I restart Amarok now.  The audio isn't working anymore.  I did manage to screenshot this message:

[IMG]http://i47.tinypic.com/30c6tes.jpg[/IMG]

Audio from other programs is still working just fine, this is only happening in Amarok.  Is there a way to fix this?  I really don't want to switch to a new media player...

If I need to do anything via the terminal, please dumb it down as much as possible.  Thanks :)

Edit: I got into the audio settings, and it seems PulseAudio gives the same message when I click 'test'.  On top of that, the other one is grayed out.  But again, I'm still getting audio from elsewhere...I tested YouTube, and I'm still getting notification sounds from Pidgin.  How can I fix this?

[IMG]http://i46.tinypic.com/168frmd.jpg[/IMG]

Edit #2: I just checked...turns out it's not just Amarok, but audio and video both aren't giving me any sound in VLC.  So I guess it's all my media players, but the internet and system sounds are fine?!  I can't go on like this!!  What do I do?!

---

### Post by Gen2ly on 2010-01-11
You could try to move PulseAudio up and it might make a difference.  I'm guessing this has to do with PulseAudio and KDE though.  PulseAudio for KDE is still very young.  Your best best will likely be to just to use ALSA by default.

---

