---
title: "mplayer problem"
date: 2011-05-10
forum: Multimedia Software
---

### Post by Dhanjal on 2011-05-10
I am facing some problems with mplayer today after updating through mplayer-daily ppa. Whenever i open any video using SMPlayer or UMPlayer, the user interface freezes. I have to use force quit to close them. If i open the same video through command line using mplayer, it works. I wonder what's the problem?

---

### Post by dasan on 2011-05-10
can just give a try after removing settings for smplayer.
remove any .smplayer folder or file and try again

---

### Post by Dhanjal on 2011-05-10
I have removed smplayer and umplayer many times, and then wiped out the package, cache and config using ubuntu tweak. Didn't delete the folders though.

---

### Post by dasan on 2011-05-10
these things may not remove your user settings..
i don know whether tat s the problem or not you can see the folders once you enable show hidden folders and files

---

### Post by SeijiSensei on 2011-05-10
SMPlayer's configuration data are stored in ~/.config/smplayer.

Have you checked the logs to see if they report the problem?  Try Options > View Logs.

---

### Post by Dhanjal on 2011-05-10
I have tried it too. There's no hidden folder in the ~/.config because synaptic removes them when we do mark for complete removal. I have double checked it. I have seen the logs too, there are no errors, it's strange. It seems like a problem with smplayer and umplayer user interface because kplayer, kmplayer and gnome-mplayer are working flawlessly. The bottom progress panel in smplayer is like it is dead, can't click anything.

I also tried an old version of mplayer, and smplayer works just fine with that. It seems like the new version is not supported yet by smplayer.

---

### Post by mc4man on 2011-05-10
> There's no hidden folder in the ~/.config because synaptic removes them when we do mark for complete removal.
Have never seen that removing a package will remove files from ~/
Anyway, the latest mplayer ppa build seems fine with smplayer - if you want to try a slightly newer build then just dl and install the package from here (0.9.3
[https://launchpad.net/ubuntu/oneiric/+package/smplayer](https://launchpad.net/ubuntu/oneiric/+package/smplayer)

Smplayer can be affected by some config setting in ~/.mplayer/config

---

### Post by Dhanjal on 2011-05-10
Removed the files manually from ~/.config/smplayer and ~/.mplayer after removing it in Synaptic. Everything is working fine now, Thanks guys

---

