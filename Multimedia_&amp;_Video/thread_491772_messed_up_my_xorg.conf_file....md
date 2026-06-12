---
title: "messed up my xorg.conf file..."
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by Methodize on 2007-07-04
I updated to Ubuntu version** 7.04** and it when fine. but afterward the resolution wasn't as good as it was before. it was at **640X480**. so i decided to edit the file (**Xorg.conf**)and i guess i didn't do it right because now every time i boot i get the terminal. and i can't run any windows.
 
i did make a backup of the file though. i just don't know how, or even if i could get to it to change it.

should i just download burn and reinstall again?



also what would be the ideal hardware (processor,Video card, RAM, HD space) for a laptop using Ubuntu?

---

### Post by topsites on 2007-07-04
Yeah, don't fark with the xorg or you will be sorry LOL

The Xorg controls the Xserver and this Pooowaaansz your system, believe the Xorg for I spent weeks studying this very subject.

Teh good news is, it's not the end.
But you might want some coffee or hot cocoa or something relaxing to sip on, alcohol would be a nono.

Simply go into terminal or from the black box screen do a:
cp oldxorg.conf xorg.conf
Since all you did was edit, right?  
Yeah, just copy the backup over the messed up one.

What might also work is if you watch it while it boots, there's a point where 2 seconds count down (2, 1, 0) and it tells you to hit Esc, do that.
There it will give you some previous configs, try one of those, kinda like a restore point.

Reinstalling would probably be your next best bet, and oh I forgot to mention: do NOT touch the Xorg !!!
Xorg is G.O.D. on the system, bow to the xorg, respect the Xorg, pray that it works.
But, can't you reuse current burn, didn't you already download?

---

### Post by Methodize on 2007-07-04
yeah i uh lost the CD. ive been moving lots of stuff around and i lost track of everything. is there any way to get the resolution i had before without editing files?

Oh, and yeah! ill never even look at a xorg file icon again.

---

### Post by RomeReactor on 2007-07-04
Hi. **Methodize**, there's probably no need to reinstall; a user botching his/her xorg.conf is (unfortunately) a very common occurrence. You can start by trying to read the contents of the folder containing xorg.conf from the terminal (Applications->Accessories->Terminal):
```
ls /etc/X11
```
See if your xorg.conf backup is there, or at least a **xorg.conf~** (which would be sort of a backup also). If your backup is there (or the **xorg.conf~**), then you can try to restore it:
```
sudo cp /etc/X11/YOUR_BACKUP /etc/X11/xorg.conf
```
Obviously substituting YOUR_BACKUP with *your backup's actual name*. Or, if the ~xorg.conf is there:
```
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```

**cp** is the command to copy/paste, and you need to use **sudo** because those files are owned by **root** (in Ubuntu, an imaginary user that has administrator rights; not the account you created), and **sudo** allows you to execute commands (one at a time) with those privileges. In Unix and other Linux distros (I think), root is an actual administrator account (someone please comment further if I'm explaining things the wrong way).

If the previous commands don't help, you can also try to reconfigure your X server (the display):
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Follow the instructions as best you can, and it will most likely return you to your graphical desktop.

---

### Post by Methodize on 2007-07-09
I entered:```
ls /etc/X11
``` and i got a message saying that the file I wanted did not exist.
So i entered: ```
ls /etc
``` to see if i could find it, but still no cigar.

Finally i tried ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and it showed that my xsever driver was **vga**. After a while of switching between drivers I came across **vesa**. This one seemed as if it was going to work, but it didn't display anything at all, my screen went on standby. It did, however, play the sound that I have for the login screen.
So without seeing anything I logged in and that was pretty much it because I can't do much without seeing.

I wonder is there anyway to replace the X11 file with one, that i could get through the terminal, online?

---

