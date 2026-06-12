---
title: "Reset VLC to default"
date: 2008-06-01
forum: Multimedia Software
---

### Post by Trevorius on 2008-06-01
A couple days ago I got the bright idea that it might be nice to get a shiny new skin for the VLC media player, which normally has a GUI striclty for radio. Long story short, huge mistake, and now I just want the plain old installation back, but just cant seem to get it. I've tried purging and reinstalling countless times (well, maybe ten or so), and I still can't get it to function properly. I did manage to get a couple of skins to come up, but most of the buttons wouldn't work (preventing me from adjusting setting graphically), and it eventually just ended up either freezing or crashing. 

I even tied compiling a new installation, but I never managed to get past confguration. It kept stopping to demand a new library package of some sort, and it seemed like no matter how many I hunted down and installed or how many errors I Googled, there was always someting else. I've wasted the better part of two days and I give up! I surrender. Someone please just tell me how to get it back to normal! (Or make it work properly with a skin, whatever's faster lol).

The last time I tried to launch it in Konsole, here's what it said:

```
VLC media player 0.8.6c Janus
Remote control interface initialized. Type `help' for help.
[00000291] main interface error: no suitable access module for `/home/trevorius/.vlc/skins2/default.vlt'
[00000291] skins2 interface error: failed to open /home/trevorius/.vlc/skins2/default.vlt for reading
[00000291] skins2 interface error: failed to parse /home/trevorius/.vlc/skins2/default.vlt
[00000291] main interface error: no suitable access module for `share/skins2/default.vlt'
[00000291] skins2 interface error: failed to open share/skins2/default.vlt for reading
[00000291] skins2 interface error: failed to parse share/skins2/default.vlt
[00000305] main interface error: no suitable access module for `/home/trevorius/.vlc/skins2/default.vlt'
[00000305] skins2 interface error: failed to open /home/trevorius/.vlc/skins2/default.vlt for reading
[00000305] skins2 interface error: failed to parse /home/trevorius/.vlc/skins2/default.vlt
[00000305] main interface error: no suitable access module for `share/skins2/default.vlt'
[00000305] skins2 interface error: failed to open share/skins2/default.vlt for reading
[00000305] skins2 interface error: failed to parse share/skins2/default.vlt
Segmentation fault (core dumped)

```

---

### Post by shad0w_walker on 2008-06-01
The settings for VLC (Which I believe would be what you are trying to get rid of.) are stored in a folder in your home directory called .vlc

To find it, open nautilus (File manager) and hit ctrl+h to show hidden directories. Removing the contents of that folder should cause VLC to generate the default configuration next time you start it.

---

### Post by Trevorius on 2008-06-01
Thanks oh so much! I would have tried that before, but I didn't know what that file was. I assumed any relevant configuration files would be burried somewhere in etc or something.

---

### Post by shad0w_walker on 2008-06-02
No problems, just remember that anything run as a non admin will be in your home directory (only place you can write to without admin)

Also, don't forget to mark this thread solved. There should be an option in the thread tools near the top of the page.

---

### Post by areskz on 2009-01-16
If you can't find .vlc in your home directory, you may find it in .config/ and .cache/

---

### Post by Robenter on 2013-01-23
I know this thread is a few years old but I was also looking to reset VLC to defaults.  I can confirm for me it was in the .config/vlc folder that I deleted the config files.

---

### Post by oldos2er on 2013-01-23
Old thread closed, please don't bump old threads.

---

