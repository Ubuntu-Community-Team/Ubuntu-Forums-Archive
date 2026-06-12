---
title: "Google chrome and Karmic odd Flash behaviour"
date: 2009-10-31
forum: Multimedia Software
---

### Post by kevindontenville on 2009-10-31
Just upgraded to Karmic from Jaunty on 5 different machines using a mixture of clean installs and upgrades and found that consistently things like BBC iPlayer don't behave properly in Google chrome whereas before they did. 

Initially it didn't play the  video but after following a guide for 64bit plug-in fudge I now have it able to play video but it still doesn't respond to any of the key controls eg pause. 

Firefox is fine and works well as always but for Chrome this is a definite regression in my small group of test machines. 

Anyone else seen similar?

---

### Post by SpearZ on 2009-10-31
Yep, can't work out what's going on. Fresh install of Karmic, but iPlayer is behaving strange.  I can listen to what's "playing now", I can't listen to any archived content.  It just sits there.
Also (maybe unrelated) I can listen to music on youtube, but I can't pause it.  The pause button doesn't work at all :'-(
Feels like a Flash problem...

---

### Post by SpearZ on 2009-10-31
> **SpearZ said:**
> Yep, can't work out what's going on. Fresh install of Karmic, but iPlayer is behaving strange.  I can listen to what's "playing now", I can't listen to any archived content.  It just sits there.
Also (maybe unrelated) I can listen to music on youtube, but I can't pause it.  The pause button doesn't work at all :'-(
Feels like a Flash problem...

Update!
Removing everything 'flash' related in 'Unbuntu Software Centre", and then doing
1. Terminal: sudo apt-get install flashplugin-nonfree
...sorted most of my problems with Youtube.  After that, trying to access anything on iplayer gave the "plugin install?" message.  I chose MPlayer, and now everything is working great.
Hope this helps someone...! :-D

---

### Post by kevindontenville on 2009-11-06
Thanks I will investigate that and see if it helps.

I wondered if it was something to do with appamor getting in the way but haven't found a suitable profile yet. Might have to write a permissive one (shock-horror!) and see if it works then.

I can feel the clean install slipping into a cludge ;-)

---

