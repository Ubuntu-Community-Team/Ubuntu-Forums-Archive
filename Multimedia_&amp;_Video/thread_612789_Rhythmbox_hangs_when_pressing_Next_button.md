---
title: "Rhythmbox hangs when pressing Next button"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by zonum on 2007-11-14
All,

I am running Gutsy and happened to notice today that when listening to mp3's under Rhythmbox that it would hang when it ended with a song and never went to the next song.  I had to kill the rhythmbox process by hand, then tried again.  

This tiime, I would start playing an mp3 (which plays just fine), then I would press the Next button and sure enough, the rhythmbox window would go gray, and just hang there - I have to kill the process "manualy".

Then, I ran rhythmbox with debug on (rhythmbox -d) and it shows that I when I press the Next button it stays at the message: "...PAUSING pipeline...".

Let me say that this behavior did not occur with Edgy.

Any ideas?

Thanks!

---

### Post by zonum on 2007-11-14
Some additional findings.  First, the issue does not seem to be with Rhythmbox as I installed Banshee and the issue happens with Banshee too - that is, after playing one mp3 song, and/or pressing the >> button, Banshee hangs and has to be Force-Quit.

Here is the interesting thing.  If I open Firefox and go to YouTube and play any one of the videos, and then I open Rhythmbox, I can then press the Next button and/or Rhythmbox plays the mp3 songs one after another as normal without going gray/hanging.  I can close the YouTube tab, and as long as I keep the current Firefox session going, I can start/stop Rhythmbox all I want, and it continues to behave correctly.  If I close Firefox, Rhythmbox stops working (Next button hangs it and/or only one mp3 song plays then hangs), and have to go through the whole procedure of starting Firefox, going to YouTube and playing at least one video.

I have repeated the above several times without issues, thus, its repeatable (this is Gutsy).

If any of you have some thoughts with the above findings, please pass them along.

Thanks,

zonum

---

### Post by zonum on 2007-11-29
All,

Following up on this topic, which I really think may be an issue with Gutsy more than anything else, I have gone back to Feisty (I had created an image of my Feisty install),  since last night, and have yet to see any issues with Rhythmbox as I reported earlier, nor with Firefox turning gray when there were videos (Flash?) on the page, etc.  Of course, I didn't expect any issues, as I had been running Feisty without any of the issues I have experienced so far with the Gutsy update.

I will continue testing stuff with Fiesty before I attempt to update again to Gutsy (via Synaptic).

zonum

---

