---
title: "[SOLVED] Youtube/Flash Videos not working (all of a sudden)"
date: 2008-12-23
forum: Multimedia Software
---

### Post by ShiningKarambaStar on 2008-12-23
I went to play a couple vids on Youtube, and found out the player isn't working. It was working fine before. Other sites aren't working anymore, either. I'm on Ubuntu 8.06. I'm not sure just when it quit working, but here's the only changes I can think of that I did in the last few days:
I know there was an update for Firefox yesterday. Today I installed a couple GDM themes, some wallpaper, and the Murrine GTK engine. Please, any ideas? The videos will begin to load, and play for about 3 seconds before quitting. The player nor the browser actually freezes, the videos just quit playing. I can actually move the seek slider anywhere in the video and play 3 seconds worth, before it quits. Hitting the play/pause button does nothing.

---

### Post by wolfen69 on 2008-12-23
you could try reinstalling firefox and flash. completely remove both from synaptic.then
```
sudo apt-get clean
```then
```
sudo apt-get autoremove
```
you might also want to go to your home folder, do Ctrl-h to reveal your hidden folders. firefox's configuration files are in the .mozilla folder. delete this also. then go back to synaptic and reinstall firefox and flash.

---

### Post by Ridor on 2008-12-23
I had the same problem - I found a lock file in my .mozilla/firefox/xxxx.default folder. I removed it and flash plays again.

---

### Post by ShiningKarambaStar on 2008-12-25
Thanks, uninstalling flash and firefox and re-installing did the trick. There was a "Lock" file in the Firefox directory, but deleting it did not help. It just came right back.

---

