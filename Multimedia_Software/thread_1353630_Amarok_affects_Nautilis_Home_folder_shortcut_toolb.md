---
title: "Amarok affects Nautilis Home folder shortcut toolbar access"
date: 2009-12-13
forum: Multimedia Software
---

### Post by ChrisNZ on 2009-12-13
Hi
I'm was running Ubuntu Hardy Heron 8.10? then upgraded to Karmic Koala 9.10 with the same fault present (appears to be)

ON the Toolbar - Places - 
                     Home Folder (shortcut)

This will open Amarok after showing a mini screen loading something. I have uninstalled Amarok, rebooted and the problem is solved. Reinstalled and the problem is back. Notice this is on both systems. 

The length of time this has been happening is only a few weeks, if that is any clue. Plenty of folk have advised how to create a shortcut on the desktop (this works fine) however this is not fixing the problem only a work around.

Not a major problem (it appears) however any others found this and a fix?? Also have any other found that the same command (home folder) shortcut opens ANY other program other than Amarok and found a fix??

TIA
Chrisnz

---

### Post by mc4man on 2009-12-13
Does this happen only with the home folder or is it any dir.(folder) you try to open with a double left click?

---

### Post by ChrisNZ on 2009-12-13
> **mc4man said:**
> Does this happen only with the home folder or is it any dir.(folder) you try to open with a double left click?

Hi Mc4man

If all the windows are closed on the same workspace - the only toolbar open, where Applications - Places - System drop down menus are present. This is where the fault can be accessed. 

I have tested File Browser access via - Go -> Home Folder this works OK
And I have created a Bookmark for Places and this works OK.
Also the Icon Open Your Personal Folder works OK

Any other folders seem to work Ok weather it's a single or double click :D - no issues

So it appears only on the "Main" Toolbar

Cheers

---

### Post by mc4man on 2009-12-14
A bit of an odd situation, basically don't have a clue...

If it was all directories, while a solution might remain obsure, it would make more sense.

to backtrack - for a while in hardy and intrepid it was possible for the default to open dir.'s to be changed (inode/directory=

the solution then was to change back to nautilus (nautilus-folder-handler.desktop ( aka Open Folder ) thru the properties -> open with of any dir. (folder

Since then it isn't possible (or easily so), to change the default for dir.'s - in nautilus it's coded to be nautilus-folder-handler.desktop.
Actually now if you r. click on a dir. -> properties there isn't even a choice for 'open with' any more.

I don't know if this is an upgrade bug of sorts where you upgraded with the default for dir's set to amarok and somehow your home dir. remained so...

You could try this - go to places -> computer -> filesystem -> home and then r. click on the folder with your user name -> 'Open with other application' and from the list choose 'Open Folder'

Otherwise there are a couple of files that could be edited, see here
[http://ubuntuforums.org/showthread.php?t=1355961](http://ubuntuforums.org/showthread.php?t=1355961)

(worked for the Op

---

### Post by ChrisNZ on 2009-12-16
> **mc4man said:**
> A bit of an odd situation, basically don't have a clue...

If it was all directories, while a solution might remain obsure, it would make more sense.

to backtrack - for a while in hardy and intrepid it was possible for the default to open dir.'s to be changed (inode/directory=

the solution then was to change back to nautilus (nautilus-folder-handler.desktop ( aka Open Folder ) thru the properties -> open with of any dir. (folder

Since then it isn't possible (or easily so), to change the default for dir.'s - in nautilus it's coded to be nautilus-folder-handler.desktop.
Actually now if you r. click on a dir. -> properties there isn't even a choice for 'open with' any more.

I don't know if this is an upgrade bug of sorts where you upgraded with the default for dir's set to amarok and somehow your home dir. remained so...

You could try this - go to places -> computer -> filesystem -> home and then r. click on the folder with your user name -> 'Open with other application' and from the list choose 'Open Folder'

Otherwise there are a couple of files that could be edited, see here
[http://ubuntuforums.org/showthread.php?t=1355961](http://ubuntuforums.org/showthread.php?t=1355961)

(worked for the Op

Thanks

Tried the 'open with other app' - although it did immediately this had no affect permanently on the places -> Home folder shortcut.

I had a look at 1355961 and this was my txt on the inode line

inode/directory=kde4-amarok.desktop;nautilus-folder-handler.desktop;clamtk.desktop;

1st time with the change - it worked! :D
Now I hope it stays that way, i think it will after reboot, however testing now....Yip Swt! THANKS

Linux Rocks!

---

### Post by mc4man on 2009-12-16
It shouldn't change off of nautilus anymore, if I was to go in and add *kde4-amarok.desktop;* to the front of the line, nothing would happen, it would stay with nautilus

(just for info - on the rest of the lines you saw in mimeapps.list the first listed is your default, the remainder are choices seen on the r. click - open with on that mimetype

---

### Post by ChrisNZ on 2009-12-16
> **mc4man said:**
> It shouldn't change off of nautilus anymore, if I was to go in and add *kde4-amarok.desktop;* to the front of the line, nothing would happen, it would stay with nautilus

(just for info - on the rest of the lines you saw in mimeapps.list the first listed is your default, the remainder are choices seen on the r. click - open with on that mimetype

Thanks for the tip - Still learning eh! ;)

---

