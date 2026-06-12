---
title: "Rhythmbox won't quit"
date: 2010-07-21
forum: Multimedia Software
---

### Post by MorrisseyJ on 2010-07-21
I am having a problem with rhythmbox. 

If i close rhythmbox using the close tab on the window it closes to a daemon on the application bar.

This is both fine and handy but i have a problem in that even when i left-click the daemon and hit 'quit', Rythmbox closes and then appears again a few seconds later. The same happens if i 'killall Rrhythmbox' in the terminal.

I can also see, in conky, that Rhythmbox is running as a process when it re-opens and i can effectively 'show Rythmbox from the daemon - so its not just a daemon problem.

Can someone either tell me how to permanently quit a running instance of Rhythmbox or tell me what setting i have enabled that keeps Rhtymbox opening?

Thanks.

---

### Post by dv3500ea on 2010-07-21
This shouldn't be happening, it doesn't happen for me and I can't find any configurations that would cause this to happen. It may be a bug so go to:
[https://bugs.launchpad.net/rhythmbox/+bugs]("https://bugs.launchpad.net/rhythmbox/+bugs") to report it.

---

### Post by MorrisseyJ on 2010-07-21
Hmmm, thanks for looking at this but i think that i have just worked this out.   I just noticed that Ryhthmbox opens automatically when i run conky. Its also while running conky that Rhythmbox won't close. When i kill conky Rhythmbox behaves normally.   The issue here is that i have a script running in conky which pulls the song name from rhythmbox. That script must be opening Rhythmbox to see if anything is playing.

---

### Post by yusof125 on 2011-02-27
hi, here I'M. Just call me, Soh.
To permanently quit the ryhthmbox player, just go to menu bar:
Music > Then choose Quit or press keyboard Ctrl and Q.

Now, It's really quit! so quickly. :P

---

