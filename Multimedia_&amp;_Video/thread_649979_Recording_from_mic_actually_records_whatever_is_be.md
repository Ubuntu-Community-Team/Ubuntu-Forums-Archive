---
title: "Recording from mic actually records whatever is being output to speakers."
date: 2007-12-25
forum: Multimedia &amp; Video
---

### Post by DinkyDogg on 2007-12-25
When I try to record in Gnome Sound Recorder, it doesn't seem to matter which channel I try to record from - it records what's being output to the speakers (or headphones, in my case) rather than what's being input from the microphone. Even more bizarre is that I know my mic is working because when I turn AMic all the way up in the Playback section of Alsamixer, the mic outputs directly to the speakers. When I tap on the mic, I hear it on the speakers, for example.


How can I get my mic to record, rather than output directly to the speakers? Can I make it stop recording from the output and record from the mic input instead?

I'm using a Creative Audigy 2 Platinum, according to alsamixer. If there's any more information I could provide that would help, please let me know.

---

### Post by Ralphie on 2008-01-16
I have this same issue. 
Audacity is only picking up whatever sound ubuntu makes eg:music, or other system sounds.

I cant seem to make Audacity want to use my actual microphone for mic input. 

this is basically a big BUMP :)

---

### Post by Whiffle on 2008-01-16
It probably has to do with what channel is set to Capture.  I don't know what the gnome mixer is, but if you open up a terminal and run

alsamixer

Then hit Tab, and arrow over to what channel you want to capture from, then hit the spacebar and it will set that to do capture.  You can do the same thing in gnome mixer it think, but you'll have to figure out what to click.

---

### Post by Ralphie on 2008-01-16
i just figured it out!

ok, go to the terminal, and enter: 
alsamixer

now a screen should come up with some levels. 
press TAB so that it puts you in the "capture" menu, use your arrow keys to go to the volume bar that says "PCM" press the down arrow until it is all the way down.

now go to the "MIC" section and raise the volume all the way up.
it might be off the screen, if you keep pressing the right arrow you'll eventually find it.
[IMG]http://www.teamtreetops.com/gallery2/main.php?g2_view=core.DownloadItem&g2_itemId=115&g2_serialNumber=1[/IMG]

*edit* 
we replied at the same time, whiffle, thanks for the want to help :D

---

