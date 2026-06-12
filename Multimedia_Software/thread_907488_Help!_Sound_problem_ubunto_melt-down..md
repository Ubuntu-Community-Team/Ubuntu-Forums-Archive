---
title: "Help! Sound problem ubunto melt-down."
date: 2008-09-01
forum: Multimedia Software
---

### Post by enderal on 2008-09-01
Help!

I was using the tutorial Sticky: Comprehensive Sound Problem Solutions Guide and followed the instructions.

I did...
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

Then...
sudo apt-get install linux-sound-base alsa-base alsa-utils

I did see that it said...
"VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following

Code:
sudo apt-get install gdm ubuntu-desktop"

But since I didn't understand what that meant, I rebooted and am now stuck with a dos screen and command line.

I was able to log in and I tried running the command above...
sudo apt-get install gdm ubuntu-desktop

but no help.

Anything I can do short of reinstalling? I hope not because I was just getting things the way I wanted and don't want to go through that all over again.

Thank you.

---

### Post by minky311 on 2008-09-01
I had that problem and all I did was once I logged in on the command line I typed in
```
startx
```
or 
```
start x
```

I can't remember which.

---

### Post by enderal on 2008-09-01
Thanks! That worked. It got me in there. I still have the same volume control problem but this is a new start at least.

---

### Post by enderal on 2008-09-01
I have a mess. I think I will reinstall.

---

