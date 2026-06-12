---
title: "TV Tuner Sound issue/question?"
date: 2008-04-25
forum: Multimedia Software
---

### Post by flyinraptr on 2008-04-25
Currently running Hardy 8.04 upgraded from Gutsy which was upgraded from Feisty. First off - let me just say the sound quality (5.1) has been impressive throughout all three iterations of Ubuntu - whether playing mp3's or viewing televison via the TvTime application.  I have but one annoying little glitch that I have not been able to figure out and I'm hoping someone might steer me in the right direction.

When I close the TvTime application .... the tv sound does not shutoff with it.  I have to either manually turn off the speakers power or open up the ALSA Mixer and lower the "capture" volume adjustment.  

Is this just the nature of the beast at this point - or a simple configuration fix?  Any ideas?

---

### Post by Pasdesignal on 2008-07-30
Have you solved this issue?

Cause I know, from researching another problem that their is a config setting which can be enabled to mute sound after quitting Tvtime.

I think i came across it here:

[http://linuxtv.org/v4lwiki/index.php/Main_Page](http://linuxtv.org/v4lwiki/index.php/Main_Page)

---

### Post by fishbulb1022 on 2008-12-27
I had problems with this too, turns out its a simple fix, only 3 steps (and they're pretty simple). You'll need an xml editor to fix this, I used screem. 

first, open a terminal and type "tvtime" (without quotes). Once it starts you can close it, you just need to find where the tvtime.xml file is. In the terminal window, it should say "reading configuration from" followed by the path. if it has two paths, it should be the first one. Mine started with /ect/.

next, in the terminal window, type "sudo screem" (again, without quotes, and replace screem with the name of the application you're using if its different) When it opens, go to file>open and use the path you found in the terminal to find the tvtime.xml file.

finally, scroll down to line 306, I believe. It should say MuteOnExit. Change the value from O to 1. File>save and you're done. 

Hope this helps. If you have problems with this, post back and I'll see if I can help.

---

