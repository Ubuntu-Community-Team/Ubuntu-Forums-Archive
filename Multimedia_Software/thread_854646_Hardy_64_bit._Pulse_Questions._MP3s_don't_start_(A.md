---
title: "Hardy 64 bit. Pulse Questions. MP3s don't start (ALSA)."
date: 2008-07-09
forum: Multimedia Software
---

### Post by Roasted on 2008-07-09
I'm running Ubuntu Hardy Heron 64 bit.

I've been sticking to Alsa lately cause I just had a ton of sound issues previously, and it was Pulse that was actually giving me the piss poor audio feedback. Alsa proved to be superior.

Now that I got everything set up (which is simply medibuntu package + gstreamer plugins + ubuntu restricted extras) I was trying to play an mp3. Twice now, they randomly don't start.

Example - I double click an mp3, set to open with Audacious. Audacious opens, then sits there, not playing a thing. Out of curiosity, I ended the pulseaudio process. Double clicked the mp3 again, bam, it started.

What do you folks suggest I do? Is Pulse really that superior? It gave me nothing but trouble. Should I install it? Or is there a way I can disable it so it won't be a hinderence to my Alsa-listening?

---

### Post by markbuntu on 2008-07-11
Did you try the comprehensive sound soultions guide at the top of the forum?
It really fixes a lot of people's problems.

Anyway, I got around a lot of my pulse-alsa conflicts by forcing pulse to use alsa sound manager and alsa/oss/xmms apps to use pulse. Now everything plays all at once, all the time and stream volumes can be individually controlled in pulse audio manager, even OSS apps and xmms work through PA via the alsa wrappers and plugins.

This works on both 64 bit and 32 bit Hardy and is how I have my sound set up on both installs. It really took a long time to figure this out.

Edit etc/libao.conf:

default_driver=alsa

Get asoundconf.gtk 
Use it to set the alsa default sound card to pulse audio.

Get all the alsa plugins.
ESD is important, it is the enlightened sound demon and allows multiple audio streams for alsa and oss.
Get all the pulseaudio apps and plugins.

paman is the Pulse Audio Manager. It is critical for figuring out what is going on with PA.

Set all Sound and Multimedia Selector settings to ALSA, device to default.

In System/Preferences/Sessions disable the Pulse Audio Session Management. In System/Adminstration/Services make sure Audio settings management(alsa utils) is checked.

Obviously there is some more to this like setting your Volume Control default device to 

"your sound card" (alsa) 

and your apps to the default device, etc. But now all my PA and ALSA and OSS apps play nice together and share the sound card.

---

