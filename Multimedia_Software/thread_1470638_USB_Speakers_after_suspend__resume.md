---
title: "USB Speakers after suspend / resume"
date: 2010-05-03
forum: Multimedia Software
---

### Post by FokkerCharlie on 2010-05-03
Hi

I have just installed Lucid 64 on my lappy, and it works well.  I have one issue, however, with my pair of Logitech V5 external USB speakers.

When I suspend and resume, the speakers are switched off.  The little blue light on them is not illuminated, and there's not sound.  If I open gnome-volume-control, I see the internal laptop sound system, but the Logitech kit has disappeared.  killall pulseaudio resets everything and the speakers reappear and work again, but this is a bit of a pain...

Any ideas on how to get the speakers to work right away after resume?

Cheers
Charlie

---

### Post by inameiname on 2010-05-03
You're doing better than I am. I have no sound at all on resume. 'Killall pulseaudio' doesn't work for me. Basically I have to restart. :P

Anyway, I have an idea that I've noticed works for some, however I am unsure of how to make it work. Not really a fix, but what you could do is create a bash script and set it to run only on resume which includes the words, "killall pulseaudio". That way it'll do that for you automatically, and voila. I've read others doing similar for other reasons, so I figured it might be worth a shot if no true fix works.

---

### Post by FokkerCharlie on 2010-05-03
Yeah, I think that would be possible.  I'd much rather have a proper fix, though, as we didn't have this problem in Karmic!

I'll have a rummage around, see if we can figure out a script...

Charlie

---

### Post by inameiname on 2010-05-03
I suspect you really don't need anything but: 

#!/bin/bash

killall pulseaudio


I actually found a couple of posts that might help if a script for a temporary fix is desired:

([http://ubuntuforums.org/showthread.php?t=472830](http://ubuntuforums.org/showthread.php?t=472830))

([http://myricci.com/index.php?option=com_content&task=view&id=41&Itemid=9](http://myricci.com/index.php?option=com_content&task=view&id=41&Itemid=9))

Though, the dude who asked in the first one couldn't get it to work, but it's a start.

---

### Post by FokkerCharlie on 2010-05-08
Cheers, inameiname

I have tried to travel that road before, without success.  However, the problem seems to have sorted itself out... sometimes, I just don't get computers.

Cheerio
Charlie

---

### Post by inameiname on 2010-05-08
Hehe, it happens. I think the biggest problem is that computers never seem to get you. :P

---

### Post by chronos00 on 2010-07-18
Have you found a definitive solution for this problem?

I also found out that:
```
sudo alsa force-reload
```
can also help bring USB speakers back

---

### Post by chronos00 on 2010-07-18
I found this information, perhaps It is useful to someone as well. Haven't tried it myself yet.

[Link: "Getting ALSA to work after suspend / hibernate"]("https://help.ubuntu.com/community/SoundTroubleshooting#Getting%20ALSA%20to%20work%20after%20suspend%20/%20hibernate")

---

### Post by inameiname on 2010-07-19
My problem actually fixed itself. Apparently, from what others on here have told me, the latest Ubuntu Linux kernel fixed my issue, which unlike yours, was an issue with having no sound on resume through my internal speakers. 

Perhaps with the latest updates your problem fixed itself as well.

---

