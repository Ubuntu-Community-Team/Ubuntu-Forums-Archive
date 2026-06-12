---
title: "[Feisty] Amarok won't submit statistics to last.fm"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by rumburak on 2007-04-30
Since the upgrade, Amarok cannot submit playlist statistics to last.fm anymore. It always tries to submit, but I just get the error that some (here: all) tracks could not be submittet. Username and password are correct, all other net traffic works well. Amarok doesn't suffer any other problems.

Did anyone noticed the same?

---

### Post by Nythain on 2007-04-30
i randomly had that problem even back in edgy, but by random i mean it could just randomly not submit the info... i think my problem was cause mostly by net congestion to the site because after a few tracks it would be able to submit them again...

---

### Post by rumburak on 2007-04-30
Net congestion to last.fm is definitely not the cause. Other users on the same server like me can submit very well.

---

### Post by rumburak on 2007-05-01
I use ISDN and never spent a thought on my WLAN since I don't use it.
But - WLAN was enabled and found a net at some of my neighbours anyway.
After disabling eth1 and closing KNetworkManager it's fine again. I wonder why the rest of traffic  went through ppp0 and that requests tried to communicate via eth1..

---

### Post by super.rad on 2007-05-06
im having the same problem, eth1 is already disabled though. im using ubuntu aswell

---

### Post by Difushion on 2007-05-08
Same problem here. Any ideas?

---

### Post by Wartooth on 2007-05-18
I've just installed AmaroK on Dapper w/ GNOME, and this is the only problem I have with it.  It's running beautifully, otherwise.  :/

---

