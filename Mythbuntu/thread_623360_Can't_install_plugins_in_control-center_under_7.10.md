---
title: "Can't install plugins in control-center under 7.10"
date: 2007-11-25
forum: Mythbuntu
---

### Post by danb35 on 2007-11-25
I recently upgraded my Feisty system to Gutsy, and installed Mythbuntu over that installation.  When I try to install plugins using the mythbuntu-control-center, I get an error box with the following:

Broken apt package cache

Check your repository lists for universe, multiverse, and main.  Perform a packagelist update as well.

When I click on the Details line, it adds this:

E:Unable to correct problems, you have held broken packages.

I've checked the software sources, and main, universe, and multiverse are checked off.  I've also verified in there that nothing is active under the community sources.  I've done apt-get update.  I've also (following some suggestions found while web searching) gone into synaptic under Edit to Fix Broken Packages.  None of this has had any effect.  I am able, in the control center, to add the restricted codecs.

What should I be checking here?  I had a similar error on another machine (also upgraded from Feisty), but it was resolved by deselecting the community software sources that had been for Feisty.  Thanks for any suggestions!

---

### Post by foxbuntu on 2007-11-26
How did you upgrade from Feisty to Gutsy? (Syanptic, apt?)

Have you checked your sources.list to make sure its all listed as Gusty?

Have you made sure the Multiverse, Universe, and Main Repos are all enabled?

Have you tried:

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

--or--

```
sudo apt-get install -f
```

--or--

```
sudo apt-get autoremove
```

---

### Post by danb35 on 2007-11-26
I used the system update tool to upgrade to Gutsy--I'm not sure the name of the binary, but it's the same one that notifies me of updates to installed software.

Yes, I've checked the sources.list, and there's nothing left there for feisty.  All three repos (main, universe, and multiverse) are enabled.

I hadn't tried the apt-get install -f or the apt-get autoremove (I had done the other apt-get commands).  When I ran autoremove, it removed a number of installed packages, saying they had been automatically installed and were no longer required.  However, the problem still persists.

---

