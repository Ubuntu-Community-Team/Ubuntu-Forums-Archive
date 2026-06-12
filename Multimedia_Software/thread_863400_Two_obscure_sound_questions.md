---
title: "Two obscure sound questions"
date: 2008-07-18
forum: Multimedia Software
---

### Post by valadil on 2008-07-18
I have a couple sound related questions that google can't seem to answer.

The first is that I have 2 sound cards and a USB guitar amp that thinks its a soundcard.  Whenever I boot up, sound plays through the correct device, but I have to change the default through preferences>sound if I'm going to get my multimedia keys to work.  How can I get this change to stick?  I've already tried asoundconf set-default-card.

The second question may end up being more of a GDM question.  My GF and I have separate accounts on my machine.  If I leave rhythmbox open the music still plays in her session.  Each session controls the same volume though, so if she switches to her X session and adjusts the volume on her gnome panel, the audio that's still playing will get louder or softer.  I'd like for sound streams to be tied to a specific X session, and when that session isn't on screen for the sound to not play.  Any way to accomplish this? 

Thanks in advance.

---

### Post by markbuntu on 2008-07-19
Asoundconfig.gtk only sets the default for ALSA. If you want to set the default for Pulseaudio you must do so in the Pulse Audio Manager.

If you want different sessions to have different defaults just get things set up the way you want and tell System/Perferences/Sessions to remember the setup as it is. You can figure that out when you get into it.

---

