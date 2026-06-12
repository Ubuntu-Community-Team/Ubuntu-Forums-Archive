---
title: "no way to access OSS playback in Audacity"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by ubukool on 2007-06-24
Hi everyone,

I'm having some problems with Audacity.  

in the 'preferences', there is an option to select what kind of playback device you want.  I find that audacity only works with OSS, but it's not always given as as option on my system.  For example, if I use Amarok, when I come to play and edit files in Audacity, it won't play the file I'm trying to edit, giving an error message.  When I go into preferences to change the playback to OSS, it isn't given as an option, only ALSA is,  but at other times it is!    There doesn't seem to be rhyme or reason to why sometimes I can select it and sometimes I can't.  It's quite maddening, because then you have to reboot the computer to get it work.

Does anyone know why Audacity does this and what I can do to get back the ability to select OSS without having to reboot my system?  Thanks for your help!

---

### Post by doyenguy on 2007-06-27
There is an ALSA compatibility layer that allows some OSS applications to still run...for example:

'aoss audacity'

Should pull up audacity for you, and it should be able to play sound.

---

