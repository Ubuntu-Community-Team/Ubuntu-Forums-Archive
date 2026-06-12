---
title: "Iptables trouble"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by IceDoE on 2010-03-03
For a while now I've been working on this problem, and have read several tutorials or similar questions on how to fix this and nothing sticks:

When I reboot my computer, my iptables sets itself to a policy of dropping everything, adds a bunch of rules, and a bunch of extra chains, to the effect that (due to everything being set to drop) I can't do anything. 
I know how to fix this from the terminal to the extent of just clearing most of it and changing the policies back.
However, what I don't know is how to make it stay that way.
I have a file with the iptables rules I want, so every time I start up I just run iptables-restore, but I don't want to have to do this every time, particularly since others use this computer who do not have admin privileges. 

I've tried changing /etc/network/interfaces with the added code pre-up iptables-restore < (etc)
But that never does anything, or if it does it just makes stuff work even less. I've tried changing init.d before based on similar info elsewhere, still no luck. 

I don't know how to get it to stick, and I don't know why it is defaulting to the rules it is, other than that I used a firewall app a while ago and afterwards this was the result, for which I uninstalled that app after no success using it to reverse the damage.

Any help/suggestions?

---

### Post by iponeverything on 2010-03-03
The last application you installed left behind some junk.

If it was firestarter:

```
sudo apt-get remove --purge firestarter
```

---

### Post by IceDoE on 2010-03-03
hmmm, well it was Guarddog, though I do have firestarter as well (have for a long time before this was a problem, and everything is set to allow most things in firestarter anyway). I tried the command with Guarddog, said it wasn't there, then I restarted the system to check and it's having the same problem.

edit: just tried to do it with firestarter too, just in case it had screwed something up as well (and since I wasn't using it right now anyway). No luck.

---

