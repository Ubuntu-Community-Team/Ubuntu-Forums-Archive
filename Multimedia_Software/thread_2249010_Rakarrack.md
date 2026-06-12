---
title: "Rakarrack"
date: 2014-10-18
forum: Multimedia Software
---

### Post by blahman179 on 2014-10-18
Sorry ahead of time if this isn't an appropriate place to post for help with this program.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I found an old 1/4' to 3.5mm adapter, and thought it would be fun to connect my guitar to my PC.

I connect my guitar to my soundcard's line in, set the sound options to recieve the sound from said port, ant it works perfectly, a nice clean guitar sound, no latency whatsoever; it's 1:1.

At this point I'm pretty lost though, I can't figure out how to get Rakarrack to work.

The main site says to use the JACK Audio Connection Kit, but I have no idea what to connect:

[IMG]http://i.imgur.com/NUS4LId.jpg?1[/IMG]

I'm using, as you can see, a Sound Blaster LIVE! Value sound card, and it has from right to left:

 a MIDI/Game port, a Line Out 1 and 2 (I'm using Line Out 1 to connect to my stereo,) Mic In and Line In ports, (I'm using the Line In form the guitar.)

Thanks in advance for any help or direction to other references.

---

### Post by deadflowr on 2014-10-18
Moved to Multimedia sub-forum

---

### Post by blahman179 on 2014-10-18
> **deadflowr said:**
> Moved to Multimedia sub-forum

Thank you :P

I wasn't sure if this was the right place to post.

---

### Post by CantankRus on 2014-10-19
It's been a while since I used ubuntu-studio but from what I remember you had to start jack control first.
[**_[COLOR="#B22222"]HowToJACKConfiguration[/COLOR]_**]("https://help.ubuntu.com/community/HowToJACKConfiguration")
[**_[COLOR="#B22222"]HowToQjackCtlConnections[/COLOR]_**]("https://help.ubuntu.com/community/HowToQjackCtlConnections")

and from an old screenshot, I made connections through the audio tab.
Disregard the ffmpeg connection because I was making a video recording.

---

### Post by blahman179 on 2014-10-19
I followed the second link to the letter, and I didn't get any sound coming out of my speakers from the Virtual Keyboard.

One thing I noticed was the MIDI tab never has any options, yet the ALSA tab has the options the MIDI tab SHOULD have in the tutorial.

I followed the MIDI instructions for the ALSA tab, still didn't do anyhting.

---

### Post by CantankRus on 2014-10-19
Yeah my memory is a bit vague on all this.
There is a dedicated ubuntu-studio support section.
[http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)

---

