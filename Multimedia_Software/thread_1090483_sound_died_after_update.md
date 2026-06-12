---
title: "sound died after update"
date: 2009-03-08
forum: Multimedia Software
---

### Post by sheishkabob on 2009-03-08
My step dad uses an semi-ancient computer (dell optiplex GX110). When I could not find a windows OS old enough to still run on the market, i gave him Xubuntu. I've been fixing the machine ever since.

The new problem is that his sound quit working after he did an update. He isn't sure which update he did. I'm asuiming it was an upgrade from gutsy(which i installed originally) to either hardy or intrepid. (I can't find the command to tell me which, but if this will help, tell me the command and i'll give you the response). 

I've run a few commands to diagnose and it would appear that the system no longer recognizes the sound card as a sound card.
When I ran "lspci", a ensoniq es1271 showed up as a sound controller.
When I ran "cat /proc/asound/cards (or modules)", It said their were no sound cards. running "aplay-l", said there were no cards as well.

None of the GUI card selectors (pulse and sound manager) can find a card.

My question is: How do I make the sound card be recognized as a sound card? I know it works, it worked before.

---

