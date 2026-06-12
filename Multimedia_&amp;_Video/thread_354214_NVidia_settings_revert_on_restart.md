---
title: "NVidia settings revert on restart"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-02-05
I have installed the NVidia drivers via the envy script, and all seems good, I can use the GUI to enable TV out, but if I ever have to restart the system, it reverts back to the old setting, and I have to manually enable the TV output again, even though I tell the GUI to save the settings to xorg.conf.  This is really irritating, since this is a remote MythTV frontend, and i don't want to have to have a monitor attached.  Any suggestions would be much appreciated.

---

### Post by pickarooney on 2007-02-05
Are you sure you have the permissions to overwrite xorg.conf? Have you checked before rebooting that the content of /etc/X11/xorg.conf are correct and that they're overwritten after a reboot? Try making the file unoverwritable at a pinch.

---

### Post by old_geekster on 2007-02-05
Try this guide to see if it helps:

[http://www.ubuntuforums.org/showthread.php?t=336412&highlight=Hub](http://www.ubuntuforums.org/showthread.php?t=336412&highlight=Hub)

It worked for me several times.

---

### Post by josesanders on 2007-04-18
Well, I'm an idiot.  The problem was in fact that the NVidia configuration utility did not have permission to overwrite xorg.conf.  I wish it would have told me that, though, when it claimed to write the file.  I just had to output the xorg.conf to a new file in the home directory and manually copy it to the right location.  Thanks for the suggestion pickarooney.

---

