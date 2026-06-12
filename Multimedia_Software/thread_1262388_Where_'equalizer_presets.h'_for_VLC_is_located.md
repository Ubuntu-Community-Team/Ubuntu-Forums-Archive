---
title: "Where 'equalizer_presets.h' for VLC is located?"
date: 2009-09-09
forum: Multimedia Software
---

### Post by dynamics on 2009-09-09
Hi,
This is with reference to the post in 
[http://ubuntuforums.org/showthread.php?t=1253098&highlight=vlc+equalizer](http://ubuntuforums.org/showthread.php?t=1253098&highlight=vlc+equalizer)

My VLC is working fine after setting the equalizer and I am enjoying it. But now I want to reset all the 'Presets' with my own 'gain' values. I tried to find the location of '**equalizer_presets.h**' in my system. I found the one for 'Audacious' but not for the VLC. Where that file is located in amd 64 version of Jaunty?

Thanks.

---

### Post by mc4man on 2009-09-09
Check your pm, but anyway it's in the source file.

This would only be something you could do if you're building a new vlc, not something to 'adjust' in an already compiled version

location is ( for 0.9.9a, 1.0.1, and 1.0,2
modules/audio_filter

Edit:
if your not inclined to build, or are and think you may need a little guidance then post some new preset values and names, I would be interested in giving this a go.

(could also possibly incorporate the changes into a vlc diff that could make building very easy ( source <- apply diff -> one build command and you'd get a full set of new vlc packages

---

### Post by dynamics on 2009-09-10
I do not want to build it from the source because I haven't tried to build any application from source in Linux and my skills are limited in programming.

But whats in my mind is, where the equilizer settings are loaded from in my vlc? For example if I change my settings from 'Flat' to 'Rock' the settings will change. It means that somewhere the Band Gain values for 'Rock' is specified. Which file is that and where is that located? 

Because if I get that file, I will change all the values according to my interest and save it so that when I toggle from 'Flat' to 'Rock' it really plays some good sound.

 The default settings in all the Presets (except Flat for which I have set my own band gains) is Crap. 

But let me tell you, this is the best player (in sound quality) I have ever come accross. I have tried many in Windows, Linux and Mac.... but This is the best with surround sound and two pass filter ... vlc rocks!

Thanks 


> **mc4man said:**
> Check your pm, but anyway it's in the source file.

This would only be something you could do if you're building a new vlc, not something to 'adjust' in an already compiled version

location is ( for 0.9.9a, 1.0.1, and 1.0,2
modules/audio_filter

Edit:
if your not inclined to build, or are and think you may need a little guidance then post some new preset values and names, I would be interested in giving this a go.

(could also possibly incorporate the changes into a vlc diff that could make building very easy ( source <- apply diff -> one build command and you'd get a full set of new vlc packages

---

### Post by mc4man on 2009-09-10
It becomes part of /usr/lib/vlc/audio_filter/libequalizer_plugin.so

It would be easier to build than edit a .so file (don't have a clue there

While I don't tend to use an equalizer, would agree that all the presets seem somewhat worthless. 

If you just change some values (in the source) you'd probaly be ok, if you change names and or add or remove some then you need lo also reflect that in other places in the .h

A careful look at the orig will prove informative in that regard. 
( or as i mentioned post some and I'll rewrite the file or make a diff

I still have never found out what that -1.11...... is all about ,, ??

---

### Post by dynamics on 2009-09-10
I think the -1.11E-15 is just to touch that particular band gain or frequency. Earlier I have noticed that to activate the band gains, sometimes you have to disturb the bars in the Graphic Equalizer. 
Now I don't need to do that after implementing your suggestion for customizing the 'Flat' one ... :-)

---

### Post by mc4man on 2009-09-10
Well you got me curious now, will have to go ahead and see if new presets can be built-in and what it may involve. (not anticipating any issues that can't be resovled, that .h is laid out very simply and verbose

Am assuming that each preset also has a 'preamp' value assigned as in the blue here on the orig. 'flat'

"flat", 10, [COLOR="Blue"]12.0,[/COLOR]
{ 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0 },

Are you leaving the preamp at the default level?

---

