---
title: "Error: 'Gdm-binary[1208]:WARNING: Unable to load file ...'"
date: 2010-07-15
forum: Multimedia Software
---

### Post by russki_drewski on 2010-07-15
So, I've got a computer (HP dc7900) running Lucid Lynx that someone unplugged the monitor to in order to hook the monitor up to another computer. This is the only thing that apparently changed, but the display manager is not starting up at all after this. The output display does work. I see the post screen, any associated terminal commands before Ubuntu starts, I'll see the Ubuntu loading screen, but when it gets time to start the gdm so that I can login the screen goes blank and the monitor goes into power saving mode. ???

I booted into recovery mode (held down shift at startup) and opened up the root shell and tried to run gdm from the terminal (I just entered 'gdm', which has worked for me before). That didn't work, but it did give me the following error:

```

Gdm-binary[1208]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Gdm-binary[1208]: Unable to find users: no seat-id found
Gdm-binary[1208]: GdmDisplay: display lasted 0.008413 seconds
.  // same as above
.
.
.
Gdm-binary[1208]:GdmLocalDisplayFactory: Maximum number of x display failures reached: check X server log for errors

```

Something to that effect. I don't know where the X server log is. If someone could let me know I can post that as well.

So the display works, but gdm is broken. Does someone know how to fix this without reinstalling Ubuntu? 


Many thanks in advance!

russki_drewski

---

### Post by russki_drewski on 2010-07-16
Anyone ... please!:frown:

---

### Post by russki_drewski on 2010-07-21
I got a hold of one of the computer science linux admins at my university and he gave me some pointers:
[LIST]
[*]check error log files in /vars/log/ for xorg.0.log and gdm/
[*]display the log contents using '**less <filename>**'
[/LIST]
Doing this I found an error in one of the log files under the gdm folder:
[LIST]
[*]/etc/X11/x is not executable
[/LIST]
Following this I navigated to the above path and using the command '**ls -hal**' I listed the files in the X11 directory with all available info. It turned out that '/etc/X11/x' is a symbolic link which had somehow been overwritten to an invalid path. However, the system somehow had sense enough to make a backup of the link (**x.backup**) before it overwrote the link. I just replaced the dead link with the valid backup link and it worked like a charm! Hooray!
 
An FYI on other commands used to do this fix: (for those newbies newer than me out there)
_Go back one directory:_
[LIST]
[*]cd ..
[/LIST]
_Change directory:_
[LIST]
[*]cd <directory or folder>
[/LIST]
_Copy: (can be used to rename as well)_
[LIST]
[*]cp <old file name location> <new file name location>
[/LIST]
_Move: (can be used to rename as well)_
[LIST]
[*]mv <old filename location> <new filename location>
[/LIST]
 
The '**mv**' command is what I ended up using. For some reason '**cp**' copied and renamed the backup file, but the link didn't point anywhere after that.
 
Also, to boot into **recovery mode** in Ubuntu Linux you need to hold down **shift** at the post screen until you see the boot options on the screen.

edit:
I hope this will help someone out in the future on these forums. I've done a little extra here so that someone can fix this easier than I did.

---

