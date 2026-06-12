---
title: "True gapless playback not"
date: 2009-12-04
forum: Multimedia Software
---

### Post by Nick Payne on 2009-12-04
I ripped Act 1 of Tristan and Isolde with Sound Juicer to ogg format and tested playback where it switches from track to track while the music is continuous. Results:

Banshee: hopeless. Marked gap in playback
Rhythmbox with crossfade plugin and zero second crossfade duration: probably the best result, but the track change is still audible between most tracks - like the recording engineer has done a bad tape edit.
Quod Libet: not as good as Rhythmbox - sounds like a couple of hundred milliseconds pause between tracks.

By comparision, if I rip the same CD on Windows using WMP and either MP3 or WMA format, the track changes are completely inaudible.

As suggestions for a better result than what I've managed so far?

---

### Post by I_can_see_the_light on 2009-12-04
Have you tried increasing the buffer size in rhythmbox? [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=8425547#post8425547[/COLOR]]("http://ubuntuforums.org/showthread.php?p=8425547#post8425547")

---

### Post by cascade9 on 2009-12-04
Possibly its the pre-gaps on the tracks. 

> **[FONT=Verdana, Arial, Helvetica][SIZE=3][COLOR=#002b8b]Can cdparanoia detect pregaps? Can it remove the two second gaps between tracks[/COLOR][/SIZE][/FONT]**

  [FONT=Verdana, Arial, Helvetica][SIZE=3][COLOR=#002b8b]Not yet.  This feature is slated to appear in Paranoia IV.[/COLOR][/SIZE][/FONT]

[http://www.xiph.org/paranoia/faq.html#toc](http://www.xiph.org/paranoia/faq.html#toc)

---

### Post by polki@mac.com on 2009-12-04
I was very surprised by this thread because I tried the same not very long ago. With Tristan and Isolde! :D

Same result here though... :(

I haven't tried the buffering, but I will.

---

### Post by Nick Payne on 2009-12-04
Well, after further experimentation, I have found that the best result is achieved by using the WMA files ripped in Windows. Listening to the Tristan files ripped in Windows and played with Rhythmbox using the crossfade plugin, zero second crossfade duration, and maximum buffer size, the gap between tracks is almost completely inaudible, even when listening closely with a good pair of headphones. The same CD ripped as ogg files has more audible gaps between tracks when played with the same playback settings.

---

### Post by cascade9 on 2009-12-04
I'm pretty sure that WMP removes silence, but since I've never used if for ripping, or anything else for that matter, I'm not sure. (WMP was one of the thing I used nLite to remove from WinXP). You could try EAC, with the 'remove silence' option ticked (EAC options-> Extraction-> 'delete leading and trailing silent blocks') to get a better codec than that horror known as .wma. 

You could also try using soem CDparanioa based ripper with LAME, I _think_ there is some option to fix the leading/trailign silent blocks with LAME. I know you can do it with other tools, foobar2000 has a "Edit MP3 Gapless Playback information" tool. No idea on what you could use to do this thats linux native.

---

### Post by hugmenot on 2009-12-04
Add this [PPA]("https://edge.launchpad.net/~lazka/+archive/dumpingplace"). It will give you perfect gapless in Quod Libet. (stable release will happen [soon]("http://groups.google.com/group/quod-libet-development/browse_thread/thread/d284b66423fa0a52").)

---

### Post by ottadini on 2010-07-21
ahh, finally :) 
I think Quod Libet needs better PR, this is what I've been hoping to find since moving to ubuntu on my desktop. 
ben.

---

