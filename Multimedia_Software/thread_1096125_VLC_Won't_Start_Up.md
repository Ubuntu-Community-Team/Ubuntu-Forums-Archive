---
title: "VLC Won't Start Up"
date: 2009-03-14
forum: Multimedia Software
---

### Post by prenger745 on 2009-03-14
I installed VLC.  It was working fine.  I wanted different skins so I downloaded them.  When I tried to put them in the skins2 folder, I didn't have access.  The only way I know to get access is to run:

sudo chmod 777 -R /usr/share/vlc/skins2

Which I did.  All the skins went in fine.  I was able to select a new skin and it was working fine.  I closed it and rebooted.  I tried to start up VLC after that and nothing happens.  I completely uninstalled in from Synaptic and then re-installed it, but it still won't work.

Any ideas?

Thanks,
Dan

---

### Post by ajgreeny on 2009-03-14
I imagine vlc doesn't like the skins2 folder being universally accessible (777), and expects it to be whatever it was before.  You need not have changed the folder permissions, you should have moved the skins into the folder with ```
sudo cp
``` and left things as they were, or just used nautilus as root with gksudo nautilus.  I always have a launcher on my desktop to ```
gksudo nautilus
``` and name it RFM (root file manager) as it saves a lot of messing around.

Try again removing completely vlc and the skins you have downloaded, then remove that skins2 folder.  Now reinstall the application and skins again, but this time don't change the permissions, do it the way I said above.  Alternatively, using ```
gksudo nautilus
``` change the permissions back to what I think they should be which is owner is *root*, **create and delete** for root, **access files** only for all others, ie *group* and *others*.

---

### Post by prenger745 on 2009-03-14
I don't even know how to set it back to what it was...I delete the VLC folder and re-installed and still got the same thing.  Here is what happens in terminal:

[00000407] access_file access error: cannot open file /usr/share/vlc/skins2/Night.vlt (No such file or directory)
[00000397] main interface error: no suitable access module for `/usr/share/vlc/skins2/Night.vlt'
[00000397] skins2 interface error: failed to open /usr/share/vlc/skins2/Night.vlt for reading
[00000397] skins2 interface error: failed to parse /usr/share/vlc/skins2/Night.vlt
[00000415] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000415] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000397] skins2 interface error: failed to parse /tmp/vltw4fjIa/default/theme.xml
[00000397] skins2 interface error: error while parsing /tmp/vltw4fjIa/default/theme.xml
[00000425] xml xml error: XML parser error (line 1) : Document is empty

[00000397] skins2 interface error: failed to parse /usr/share/vlc/skins2/default.vlt
WARNING: QApplication was not created in the main() thread.
[00000430] access_directory access error: /usr/share/vlc/skins2/Night.vlt: No such file or directory
[00000430] access_file access error: cannot open file /usr/share/vlc/skins2/Night.vlt (No such file or directory)
[00000424] main interface error: no suitable access module for `/usr/share/vlc/skins2/Night.vlt'
[00000424] skins2 interface error: failed to open /usr/share/vlc/skins2/Night.vlt for reading
[00000424] skins2 interface error: failed to parse /usr/share/vlc/skins2/Night.vlt
[00000431] xml xml error: XML parser error (line 1) : failed to load external entity "skin.dtd"

[00000431] xml xml error: XML parser error (line 2) : Validation failed: no DTD found !
[00000424] skins2 interface error: failed to parse /tmp/vltjHuV7q/default/theme.xml
[00000424] skins2 interface error: error while parsing /tmp/vltjHuV7q/default/theme.xml
[00000434] xml xml error: XML parser error (line 1) : Document is empty

[00000424] skins2 interface error: failed to parse /usr/share/vlc/skins2/default.vlt
QObject::setParent: Cannot set parent, new parent is in a different thread
QPixmap: It is not safe to use pixmaps outside the GUI thread


It repeats the last line 100s of times...

---

### Post by mc4man on 2009-03-14
from terminal
```
vlc --reset-config
```

using a different skin in 0.9.x is extremely hit or miss

---

### Post by prenger745 on 2009-03-14
> **ajgreeny said:**
>   I always have a launcher on my desktop to ```
gksudo nautilus
``` and name it RFM (root file manager) as it saves a lot of messing around.



This sounds like what I need to have..but I don't understand how you get a launcher for that?

---

### Post by ajgreeny on 2009-03-15
> **prenger745 said:**
> This sounds like what I need to have..but I don't understand how you get a launcher for that?
Simple.  You right click on an empty part of the desktop and choose Create Launcher.  In the dialog which pops up, leave *Application* in the top box, type *RFM* in the second, type the command ```
gksudo nautilus /
``` in the command box, and *Root file manager* in the comment box.  You can click on the icon to change it if you want, but that's up to you.

Just be very careful using nautilus this way, as you can do a great deal of damage if you are not sure what you are doing, as you already appear to have done to VLC.

---

