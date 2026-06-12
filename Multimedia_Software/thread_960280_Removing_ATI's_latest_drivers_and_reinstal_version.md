---
title: "Removing ATI's latest drivers and reinstal version supplied by Ubuntu"
date: 2008-10-27
forum: Multimedia Software
---

### Post by employeeno5 on 2008-10-27
I imagine this info has to be floating around here somewhere already but I'm having trouble finding it through search.

I recently tried installing ATI's latest proprietary drivers from their website in hopes of solving a flickering screen issue when playing games in WINE. Clearly nothing too important but I thought I'd give it go.

Anyways, it was not successful and now applying 3D acceleration only gives me a blank white screen if anything at all.

What I'm having a bit of trouble figuring out how to do is remove whatever ATI's website installer did my system so that I can reinstall the fglrx version that Ubuntu's proprietary hardware tool provides. That one worked great with the exception of the screen flick issue in WINE.

Thanks for any help or advice in advanced. 

PS
I'm Using 8.04.1 currently, but was probably planning on upgrading to 8.10 later this week, in case anyone thinks the upgrade would resolve this for me.

---

### Post by Bablefish on 2008-10-27
Unless you get better advice, mine is reinstall your OS

---

### Post by employeeno5 on 2008-10-27
> Unless you get better advice, mine is reinstall your OS 

I was considering that anyways. I'm using 32bit right now, and was thinking that when I put Ibex on, perhaps I'd do a clean install and start giving 64bit a go.

If there is another way to do this though, I might prefer to not have to reinstall, or at the very least, I always appreciate learning something new about Linux and being that much more empowered for in the future.

Thanks again.

---

### Post by Brain-free on 2008-10-27
God no, you don't need to reinstall Ubuntu.... The way to uninstall the ATI drivers is actually very simple. Give this to your teminal:
```
sudo apt-get remove --purge xorg-driver-fglrx
```
One thing though. How did you install the ATI drivers? Did you follow the instructions in the unofficial wiki for ubuntu?

---

### Post by employeeno5 on 2008-10-27
> One thing though. How did you install the ATI drivers? Did you follow the instructions in the unofficial wiki for ubuntu? 


Here's a run down of what's I've managed to do to my system:

Yes, I tried it via the wiki first and had a failure as described previously, receiving a blank white screen once enabling 3d graphics.

I tried the command you listed above and then rebooted but found that re-enabling fglrx through Ubuntu's hardware driver interface resulted in the same thing.

I then used the .run provided by ATI on their website to see if would improve the situation, perhaps overwriting my problem with something better.

This resulted in X failing to start at all.

I restored my xorg.conf to a back-up and then attempted again to remove the driver by purging xorg-driver-fglrx again without luck. 

Finally I installed Envy, asked it remove ATI drivers, which got me back to the white screen scenario I received when I had first used the wiki. 

Not having much to lose, I asked Envy to install its drivers. It has installed a driver that seems to work pretty darn well. However, it has some issues with the screen saver and now the Steam games I was trying to play in WINE don't open at all, and the whole point of this in the first place was to try to get them to display better. 

If I remove the Envy drivers and attempt to use the original one Ubuntu will automatically put on, I'm back to the same issue from original wiki attempt which is a blank white screen.

So at the moment, my options are an Envy installed driver with some issues, or the "typical one" which seems irrevocably replaced with whatever the Wiki had me do, providing only a white screen.  

I hope that wasn't too hard to follow, and I imagine I've pretty well screwed things up. I'm ok with that, I knew that was fairly likely as I started this and continued along each step of the way. I was just experimenting I guess :)

I was hoping there was an easy way to back out of this or to restore the original settings without reinstalling the whole system; but like I said before if I do have to, I was thinking about doing that anyways to make 64bit switch.

---

### Post by mike310z on 2008-10-27
This may not be relevant, but flickering with ATI drivers in full screen games is a well know problem that persists in 8.10.
It can be often be eliminated by turning off visual effects in System->Preferences->appearance->visual effects.

---

### Post by mike310z on 2008-10-27
This may not be relevant, but flickering with ATI drivers in full screen games is a well know problem that persists in 8.10.
It can be often be eliminated by turning off visual effects in System->Preferences->appearance->visual effects.

---

### Post by employeeno5 on 2008-10-27
Thanks Mike,

That's a nice heads up for the next time I try to get some games working.

I'm actually going to start putting the 8.10 RC on a few minutes. I think I fugged things up a bit too much considering I'm was just going to upgrade this week anyways.

---

### Post by Yellow Pasque on 2008-10-27
For future reference, the correct way to uninstall the ATI drivers downloaded from their website is -
```
cd /usr/share/ati
sudo sh fglrx-uninstall.sh
```

---

