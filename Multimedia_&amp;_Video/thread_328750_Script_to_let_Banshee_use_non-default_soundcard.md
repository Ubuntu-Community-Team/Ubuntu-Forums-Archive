---
title: "Script to let Banshee use non-default soundcard"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by KenSentMe on 2006-12-31
I have two soundcards in my system, both work right and i can switch between devices properly. I want to use the non-default card for playing music with Banshee/Rhythmbox and the default device for all other sounds. 

To make Banshee use the second device i got to System - Preferences - Sound, then to the Sounds tab and at Default Soundcard select the second device (Intel ICH5). Then i open Banshee, start the music and do the same steps to switch to my default card for other applications.

Is there a way to make a script that does this automaticly: switch to second soundcard, open banshee, switch back to default card. Or is there some other way to get this working without having to change devices every time i want to play music?

---

### Post by KenSentMe on 2007-01-01
Is there anyone that can get me on the right track?

---

### Post by aay on 2007-01-08
> **KenSentMe said:**
> Is there anyone that can get me on the right track?

I'd like to be able to do the same thing.  Anyone have any luck?  Or know of a way to do this with a different music manager?

---

### Post by aay on 2007-01-09
To answer my own question, I've found out that Amarok can do this.

Just go:

Settings/Configure Amarok/Engine/ALSA Device Configuration/

Change Mono and Stereo to the device you want to play through.  You should plug in something like this: "hw:0" or "hw:1" or "hw:2"

To see what your devices are and what number they are assigned open a terminal and do "aplay -l"

In my case I see:

[INDENT]card 0: I82801BAICH2 [Intel 82801BA-ICH2], device 0: Intel ICH [Intel 82801BA-ICH2]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: NX [SB Audigy 2 NX], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/INDENT]

So I would use either "hw:0" or "hw:2"

I don't know of a script that will switch back and forth between cards quickly, but if you look here

[http://amarok.kde.org/wiki/FAQ#How_can_I_change_where_the_audio_is_output_to.3F](http://amarok.kde.org/wiki/FAQ#How_can_I_change_where_the_audio_is_output_to.3F)

A method is outlined to play to all your cards at once.  Then you could just mute or increase/decrease volume on the device(s) you want.  Nice!

Hope this helps.  I'd love to see any other tips about this kind of stuff if anyone knows any.

Adam

---

