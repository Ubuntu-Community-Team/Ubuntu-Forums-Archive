---
title: "maverick KDE unusable"
date: 2010-08-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-08-05
I installed kde alongside my maverick gnome testing install via the "kubuntu-desktop" metapackage.

After rebooting and logging into kde I found it horribly slow and unresponsive.
Desktop effects were enabled by default but I kept getting a popup saying certain effects couldn't be enabled and listed about 7 or 8 effects.
It didn't actually give any indication why though.
Although it was right about some of them (blur, magic lamp for example), other effects listed WERE enabled and working.

I went away for a short while and when I get back I checked the system monitor:
All 4 CPU's were alternately jumping from nothing to 100% which might explain unresponsiveness but there were no apps actually running, it was the desktop which had been stood not doing anything for 10 or 15 minutes.

Looking at the running processes there was nothing listed there that seemed account for the CPU spiking.

The computer is a HP G62 notebook with intel HD graphics.
It runs perfectly fine in the gnome variant even with excessive compiz effects and other kde distributions tried recently also run fine with desktop effects enabled so this is certainly a maverick thing.

Anyone else getting this?

---

### Post by buzzmandt on 2010-08-05
I run KDE full time now that's it's stable.  Lucid Kubuntu is Fantastic!! but maveric is not.  I'm not sure if it's KDE or intel graphics regression.  The smooth transition from login to desktop isn't smooth, it's jerky (in lucid it's smooth as silk).   I'm also getting the select few "effects could not be enabled".  It's not all the effects, just some.  Fall apart works, wobbly windows doesn't, just as an example.

As i said, not sure it's a graphics regression or if it's in KDE itself.  I was considering installing lucid on my test partition and then installing kde 4.5 on to it.  If i get time i'll do this.

Anyone else getting this?





I also have a regression of intel sound not working through headphones but will post a new thread for it.

---

### Post by x-shaney-x on 2010-08-06
I have installed kde lucid for comparison and there is no comparison, lucid version smooth and fast and ALL effects are working normally.

I have been having intel sound related issues in both lucid and maverick.
In lucid I get no sound until I install the also backports modules then it's ok.
In maverick I am having endless sound problems and have since I tried the firs alpha.
Just have to leave things to settle and see how it goes nearer release.

---

### Post by x-shaney-x on 2010-08-06
Some other things I have noticed after booting into KDE today.

Aside from the other issues mentioned, I get gnome apps opening on startup also - rhythmbox, empathy, docky and something else (I forgot).
I don't know why these are running and I don't have ANY of those autostarting on gnome.

I also get several boxes popup on startup with this messages: ```
No command arguments supplied!
Usage: kdesudo [-u <runas>] <command>
KdeSudo will now exit...
```
I'm not sure why kdesudo should be running on startup at all but when I look at the system monitor there are 4 running instances.

In fact there are a LOT of multiple KDE processess running,  don't know if this is normal for KDE or not:

akonadi_nepumuk - 6 instances
nepumuk - 12 instances
kdesu - 4 instances
telepathy-haze - 4 instances
kio-http - 6 instances
getty - 6 instances

There are more but you get the idea.  It has crossed my mind that many of these multiple instances could possibly be because it is a multi-core computer? But I don't know much about that and 6 and 12 instances seem excessive.

While ksyguard was open, only xorg, kwin and ksysguard itself should any CPU activity with xorg jumping highest to 10% at one point, still nothing account for 4 cores using 100%

---

### Post by x-shaney-x on 2010-08-06
Hello, me again.

Desktop effects > Advanced > Use Vsync

Enabling this option has changed things dramatically.
All effects now working and CPU no longer jumping to 100%.

Looked at startup and shutdown options and noticed it adds all gnome startup entries, even if they have been manually disabled and I also turned off nepumuk search.

The desktop is still choppier than I am used to with gnome or other kde distros and cpu and ram usage both generally higher than I am used to also.

---

### Post by buzzmandt on 2010-08-06
no good for me, vsync didnt work.

I also have many instances of multiple items running but i'm getting no cpu spikes

---

