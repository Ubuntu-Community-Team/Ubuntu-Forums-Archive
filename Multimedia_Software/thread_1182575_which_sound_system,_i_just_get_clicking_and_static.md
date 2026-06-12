---
title: "which sound system, i just get clicking and static"
date: 2009-06-09
forum: Multimedia Software
---

### Post by jezjones on 2009-06-09
A few years ago i replied to an invite by Mark Shuttleworth to discuss things we would like to see in the next version of Ubuntu, at the time i think the next version was Dapper Drake.

My point was that since version 6 of redhat (when i started playing with linux), sound was always something that needed work, never configured out of the box no matter what the hardware i used, nor how standard it was.

His reply was that was what Jack was for, to sort out audio problems and make a final solution.

Today, now on 9.04, I still have sound issues and instead of OSS and ALSA, i also have JACK and PULSE AUDIO, none of which appear to work.

SO, my question is this, i want my sound to work, do i need all this rubbish or can i remove some stuff.

Secondly where is the guide for audio.. the one at the top of this forum is dated 2006, which is a little out of date for 9.04

Thanks.

---

### Post by markbuntu on 2009-06-09
There is the quick and easy guide for 9.04 here

[http://ubuntuforums.org/showthread.php?t=1182575](http://ubuntuforums.org/showthread.php?t=1182575)

If that does not work for you then you need to use the long and painful guide here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Jack is not really necessary unless you do audio production. You can read about jack in the second link.

---

### Post by jezjones on 2009-06-09
Thanks,

I did manage to find the link you posted, after i had posted this thread.
I did the first few steps...

> 

vlc-plugin-pulse -this also pulls in a lot of libs that vlc will need
xmms2-plugin-pulse -this also pulls in the xmms2 core
pulseaudio-module-lirc - this is to use lirc and your infrared remote with pulse
libsdl1.2debian-all -this wil replace the alsa version with all available drivers
lib32asound2-this is the 32 bit library for 64 bit installs
lib32asound2-plugins -this is the 32 bit plugins for 32 bit apps
libao2 - you need this for apps using the libao cross platform library
asoundconf-gtk -applet for default alsa sound card
audacious-plugins-extra -plugins for audacious for many codecs like MP3, aac, FLAC, WMA, etc




except i did not do any of the 64 bit stuff (i have intel core 2 duo).

It did not seem to make a difference and i was at work, so planned to go through the rest now i am home.

BUT.

I have booted up to find all is working in terms of sound.

In my multimedia system selector i have default out set to Pulse audio, and default in ALSA.
In my mixer i have the first option selected which is HDA Nvidia (ALSA Mixer)

I hope this remains working, but i think that grabbing the packages listed above has filled in some blanks in the audio process.

It seems like this would the stuff covered by Automatix in previous versions, so maybe i will google that and see what became of it...

Thanks for the help and suggestions.


Jez

---

