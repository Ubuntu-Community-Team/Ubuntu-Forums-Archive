---
title: "Exporting .ogg music files"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by ascherjim on 2008-02-09
Using Sound juicer CD extractor, I have been ripping many classical music CD's in .ogg format to a Desktop directory in Ubuntu.  However, every attempt I have made to copy (export) them from this directory to a flash card or external hard drive has failed.  I've even tried to do it through terminal command line Linux procedures, with the CD title directories copying all right, but without the .ogg files included.  What am I missing?  What simple thing am I doing wrong?  After all, one should be able to copy and export such files  Any (useful) advice will be appreciated.

---

### Post by yabbadabbadont on 2008-02-09
What command, exactly, did you try to use in the terminal to copy the files?  What error message, if any, was displayed?

---

### Post by ascherjim on 2008-02-09
> **yabbadabbadont said:**
> What command, exactly, did you try to use in the terminal to copy the files?  What error message, if any, was displayed?

Whether I try to copy the album (which is a directory) using"cp -r (album name) /media/disk or individual music items (which are .ogg files) from within the album (directory) using cp (.ogg file name) /media/disk, I invariably get a message which states "cannot create regular file (giving .ogg file name): invalid argument".  The file names, by the way, are the titles of the individual music items which contain words and spaces.  I should be able to copy directories and files in Ubuntu just using my mouse.

---

### Post by yabbadabbadont on 2008-02-09
Assuming that /media/disk is mounted, what is the output if you run (in a terminal):
```
ls -l /media/disk
```

Not being able to copy in the GUI is most likely a permissions issue.  Not being able to copy the files in the terminal is most likely due to the spaces or other special characters in the filenames.  That is why I asked for the exact command.  Just like using the windows command prompt, you must quote any filename or directory that contains spaces in the name.  :)

---

### Post by ascherjim on 2008-02-09
> **yabbadabbadont said:**
> Assuming that /media/disk is mounted, what is the output if you run (in a terminal):
```
ls -l /media/disk
```

Not being able to copy in the GUI is most likely a permissions issue.  Not being able to copy the files in the terminal is most likely due to the spaces or other special characters in the filenames.  That is why I asked for the exact command.  Just like using the windows command prompt, you must quote any filename or directory that contains spaces in the name.  :)

Wow.  I suspect that this route will become more trouble than it's worth.  By the way, the command ls -l /media disk works fine in showing me in each instance what's on the disk.  (I generally use "ls -la".)  For the most part, it's just the album (directory) name with no musical files contained within.

As I don't think I'll be able successfully to copy my .ogg files from the Ubuntu Desktop where they currently exist to my now ogg-compatible Nokia N800 music player, I think I'll just have to start over and rip them directly to a flash card, which works with the Nokia.  So, I've probably wasted two days of ripping CD's!  I hate to say it, as I do like Linux -- but this wouldn't be a problem in Windows!  Many thanks for your time and advice.

---

### Post by jken146 on 2008-02-09
I think yabbadabbadont was trying to figure out if permissions are restricting you from copying files to /media/disk.  Please post the exact output of the command (s)he gave you.

---

### Post by yabbadabbadont on 2008-02-09
I didn't ask you if "ls -l" would work.... I asked for the output so that I could troubleshoot any permissions issues.  :roll:

If you want help, please provide the information that is asked of you.  Otherwise, have fun.  :)

---

### Post by yabbadabbadont on 2008-02-09
> **jken146 said:**
> I think yabbadabbadont was trying to figure out if permissions are restricting you from copying files to /media/disk.  Please post the exact output of the command (s)he gave you.

What (s)he said.  ;)

(He, in my case)

---

### Post by ascherjim on 2008-02-09
> **yabbadabbadont said:**
> I didn't ask you if "ls -l" would work.... I asked for the output so that I could troubleshoot any permissions issues.  :roll:

If you want help, please provide the information that is asked of you.  Otherwise, have fun.  :)

I will check the permissions in the directories/files and make certain that I have appropriate permission to do what I intend.  Thanks for the good thought on where I might look for a solution.

EDIT:  OK.  I checked and changed them to give me full permission, but that didn't make any difference.  I suspect, as you surmised, that it's the spaces between the words in the titles -- and I don't intend to put the titles all in quotes to make it work.  The issue boils down to: How do I rip my CD's in the .ogg format on Ubuntu and copy and transfer them to my Nokia N800 media player?  Is there possibly a better, more flexible ripping software for creating .ogg files where this wouldn't happen?  Oh, well, my wife and I are going out for dinner (in Seattle) so I'll be off-line until tomorrow.  Again, many thanks to both of you.

---

### Post by jken146 on 2008-02-09
The software doesn't really matter; it just makes files in the ogg vorbis format where you tell it to.  You could try changing the naming convention in Sound Juicer (I think there is an option to replace the spaces with underscores) so that you can easily use the terminal to copy the files later.

Why don't you just do it graphically though?  Point your file manager to /media/disk and paste your music there.

---

### Post by ascherjim on 2008-02-09
> **jken146 said:**
> The software doesn't really matter; it just makes files in the ogg vorbis format where you tell it to.  You could try changing the naming convention in Sound Juicer (I think there is an option to replace the spaces with underscores) so that you can easily use the terminal to copy the files later.

Why don't you just do it graphically though?  Point your file manager to /media/disk and paste your music there.

Jken: I'm on my way out the door, but pointing my "file manager" (mouse?) at the relevant directory icon on my Desktop and pasting it on my /media/disk icon is what specifically doesn't work -- something about "wrong parameters" in the titles.  I will check into the Sound Juicer option for underscores rather than spaces.  Thanks again.

---

### Post by yabbadabbadont on 2008-02-09
I'm still betting that you don't have write permission on /media/disk.  Coping the files in the file manager should work even if they have spaces in the names.  You only need to quote them at the command prompt.  Assuming that /media/disk is mounted, you can change the ownership of it to your user by using:
```
sudo chown yourusernamehere /media/disk
```
If you still can't copy the files in the GUI after you have done that, then there is something else going on.

---

### Post by ascherjim on 2008-02-10
> **yabbadabbadont said:**
> I'm still betting that you don't have write permission on /media/disk.  Coping the files in the file manager should work even if they have spaces in the names.  You only need to quote them at the command prompt.  Assuming that /media/disk is mounted, you can change the ownership of it to your user by using:
```
sudo chown yourusernamehere /media/disk
```
If you still can't copy the files in the GUI after you have done that, then there is something else going on.

My trusty Ubuntu has suddenly gone haywire.  I can't get into root with my usual password, and a number of applications are inaccessible.  I'm going to have to reload Ubuntu sometime in the next few days!  Until then, I have downloaded some free ripping software in Windows (gasp!) that converts CD's to ogg files, and I will experiment with that for awhile.  At least there seem to be no problems so far in copying the ripped ogg files from my hard drive to my flashcard. Thanks again for your help.

---

