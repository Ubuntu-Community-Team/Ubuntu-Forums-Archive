---
title: "ALSA = fine, ALSA via SDL = awful"
date: 2009-12-12
forum: Multimedia Software
---

### Post by Listerofsmeg01 on 2009-12-12
Hi folks,
 
Can anyone suggest why SDL apps sound so bad on my Revo?
 
I am running audio over HDMI, and have set up ALSA ok. Native ALSA apps sound absolutely fine. (my default ALSA device is HW:0,3 if that makes any difference, I tried using plug but it sounded speeded up and crackly)
 
However, any SDL apps have awful sound. constantly stuttering and crackling. I have set the SDL_AUDIODRIVER=alsa.
 
eg. 
"Mplayer" sounds fine.
"Mplayer -ao sdl" sounds atrocious
 
xmame sounds fine
sdlmame sounds atrocious.
 
Any suggestions, as some apps are SDL only. :(

---

### Post by Listerofsmeg01 on 2010-01-04
Thought I would update this since I've finally fixed the crackling sound on sdlmame, and thought it might put someone else out of their misery.

I am using an Aspire Revo, so all sound it digital out at 48000hz. Originally I set all my apps to output at 48000hz to accomodate this, but some stuff couldn't do this, or output in 8bit samples (Stella), so I would get no sound.

I changed my ALSA setup to use the plug plugin to upsample everything to 48000hz, and changed sdlmame sound output to 22050hz, and lo and behold, perfect sound! HALLELUJAH!

44100Hz also stops the crackling, but I do get drop outs, so 22050 is fine for me.

48000Hz also caused issues in mupen64 (N64 emulator) - sound would drop out for a moment every couple of seconds. 44100Hz fixed this too. :D

(ps. for info,  other people have reported that using OpenGL as your display driver in sdlmame will stop crackling sound, but I was already using that)

Hope that is some use to someone.

---

