---
title: "No sound in profile?"
date: 2012-01-21
forum: Multimedia Software
---

### Post by adrinkrahene on 2012-01-21
I started getting this error now the sound in my profile has stopped working.
If however I go into another profile I have on the system the sound is working
I have not made any changes to the hardware (and as far as I can remember 
the software is unchanged also) so this is kinda strange to me..
One more thing I should mention I am using GDM not KDE,
but I do think I have some programs that were made for KDE

error follows:

KDE detected that one or more internal sound devices were removed.
 Do you want KDE to permanently forget about these devices?
 This is the list of devices KDE thinks can be removed:
 
[LIST]
[*]Capture: HDA Intel, ALC888 Analog (Direct hardware device without any conversions)
[*]Capture: HDA Intel, ALC888 Analog (Direct sample snooping device)
[*]Capture: HDA Intel, ALC888 Analog (Hardware device with all software conversions)
[*]Output: HDA Intel, ALC888 Analog (Direct hardware device without any conversions)
[*]Output: HDA Intel, ALC888 Analog (Direct sample mixing device)
[*]Output: HDA Intel, ALC888 Analog (Hardware device with all software conversions)
[*]Output: HDA Intel, ALC888 Digital (Direct hardware device without any conversions)
[*]Output: HDA Intel, ALC888 Digital (Direct sample mixing device)
[*]Output: HDA Intel, ALC888 Digital (Hardware device with all software conversions)
[/LIST]

---

### Post by adrinkrahene on 2012-01-26
I'm still at a lost in understanding what is happening. I have notice that some things that I setup with sound still have sound. ie: I have an alarm that I have set to go off at random
using kalarm. if you have anything like this happen to you and you worked it out a little help would be nice! I don't see the Audio Controller (analog) that I had. Anyone know how I can install it again in this profile, seeing that it is working good in the rest.

[I][B]4 DAYS NO REPLY, IS THIS THING WORKING? :(
[/B][/I]

---

### Post by adrinkrahene on 2012-02-03
Well I got so many reply I knew one of them would work! :lolflag:
Anyway I found that after [reinstalling the alsa drivers]("https://help.ubuntu.com/community/SoundTroubleshooting")
the sound came back up. Not sure but seem to sound better too.
That maybe because I didnt have any sound for so long.
It was like being the last living cell in a dead body...

---

