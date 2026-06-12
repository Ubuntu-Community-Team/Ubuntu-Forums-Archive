---
title: "How to get preview icons for .m2t video files?"
date: 2009-01-17
forum: Multimedia Software
---

### Post by pixelpaul on 2009-01-17
Ubuntu 8.10 file browser will show preview icons for .mpg and .mpeg files.  My Canon HV30 video camera makes .m2t files, (which play nicely in VLC btw). The file browser does not create preview icons for these files. However, these .m2t files are really mpeg files and if I rename them to mpeg, the preview icon will be created.  

Other than renaming all these files, is there another way to get file browser to create the preview icons?

If not, is there a way to batch rename all the files?

---

### Post by SqRt7744 on 2009-01-18
You can do both. First, to batch rename all you files, you really only need the 'find' command. Try 'man find' or this link for more info [http://www-128.ibm.com/developerworks/aix/library/au-unix-find.html](http://www-128.ibm.com/developerworks/aix/library/au-unix-find.html)

as an example to rename all files in your home folder and sub folders, start a terminal and enter:

find ./ -name "*.m2t" -exec mv {} {}.mpeg \;


To get nautilus to automatically generate previews, you might (I'm just guessing here) have to add a line to /etc/gnome/defaults.list in the video section, maybe just underneath 
video/mpeg=totem.desktop
which reads:
video/m2t=totem.desktop  (or maybe vlc.desktop?)

then again, that may just do nothing. Probably won't break your computer though :)

---

### Post by pixelpaul on 2009-01-18
SqRt7744:

I tried to modify the defaults.list file, adding the video/m2t=totem.desktop line.  However, it said I did not have permission to save it.  I went to system/authorizations and tried to change things there so I might unlock permission but was unsuccessful. 

I'm new at ubuntu so I'm not sure how to do simple things sometimes...

---

### Post by SqRt7744 on 2009-01-19
I think it's probably better to just rename all your files by clicking on applications->accessories->terminal and entering the 'find' command i mentioned above.

As a side note, to copy and paste a line there is trick in unix systems: just highlight the text in the browser and paste it with a center click into the terminal (try pressing the wheel down, or both buttons togther). No ctrl-c & ctrl-v needed.

If you really really want to edit the defaults.list file, you have to enter the command preceded by 'sudo' (=super user do). e.g. sudo gedit /etc/gnome/defaults.list
.... but editing defaults.list might not be the proper way to achieve what you are trying to do. The defaults file associates file-types with programs, so, for example, you can set vlc as the player to open wmv files...but in linux, file-types are generally determined by the magic bytes in the files themselves, as opposed to the file extension (as in windows). It seems this isn't always the case though so who knows.

I'd recommend using vim instead of gedit, but you have to learn how to use the editor vim first, and a system file isn't the best place to practice.

---

### Post by pixelpaul on 2009-01-19
SqRt7744:

I took a chance and tried the sudo gedit /etc/gnome/defaults.list command and added video/m2t=totem.desktop

That was the answer!!  I'm now getting preview icons. Oddly, though, there is 1 folder of files that it doesn't create icons for. Strange, since all the clips were shot with a Canon HV30 and captured using HDVSplit on a vista machine.  

As a new user, I am SO IMPRESSED with ubuntu...

Thanks for your help, much appreciated.

Paul

---

### Post by SqRt7744 on 2009-01-20
wow that was an almost totally random guess :)

... re. the folder that isnt showing previews, try creating a new folder and moving the files into it to see if previews are created...

---

### Post by pixelpaul on 2009-01-22
SqRt7744:

Sorry for the delay, had to get a new monitor for the ubuntu computer.

Anyway I tried what you suggested, making the new folders and moving the footage files over.  That did the trick!

These preview icons make life a lot easier when dealing with lots of footage.  This is something vista could not do.  Chalk up another convert to ubuntu!

Paul

---

