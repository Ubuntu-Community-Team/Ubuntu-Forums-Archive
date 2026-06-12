---
title: "Help me rip dvds automatically."
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by Conspirator45 on 2008-01-27
I want my computer to automatically rip any DVD I put into the DVD drive to a Folder. I had a go at the guide I'm placing at the bottom of this post but it didn't seem to work. I put the dvd in and nothing happens. The DVD is mounted onto the desktop but other than that, nothing. Could somebody please give me a hand?

GUIDE:
I have ripped my entire DVD collection to my hard drive (over 300 discs), and wrote a script to help automate the process. At its core, it uses dvdbackup, but it eliminates all unnecessary interaction with you by:
- Automatically starts ripping as soon as the DVD is inserted
- Automatically names the subdirectory using the DVD label.
- Ejects the DVD when done, so you just have to pop in the next disc.

The only time you have to interact with it, is when the DVD label is blank, or it's a duplicate name with a DVD you already ripped.

0) Before starting, install dvdbackup
1) Download the script from here, and save it somewhere (like ~/ripdvd)
[cct-public.s3.amazonaws.com]
2) Make sure it is executable with 'chmod a+x ~/ripdvd'
3) Open it up in an editor, and change the 'backup_dir=' line to specify the directory where you want it to place all your DVD subdirectories.
4) In GNOME, go to System->Preferences->Removable Drives/Media->Multimedia, and set the "Play DVD when inserted" command to "/home//ripdvd %d" (I don't know how to do this in other types of desktop environments)

Then, insert a DVD. A Terminal window (primitive, isn't it?) will pop up with the script output. If it doesn't like the default name, it will beep, and ask you to enter a different one. After ripping, it will eject, and you can put in another disc, and the process will start over. Meanwhile, back in the terminal window, it will have asked you if you want to rename it from the default name. If not, just press ENTER.

---

