---
title: "Where is the Rhythmbox library .xml file?"
date: 2011-01-02
forum: Multimedia Software
---

### Post by therieb on 2011-01-02
Hello everyone!

I recently had to migrate my Rhythmbox library to another hard drive, and I wanted to erase the database and start over to avoid duplicates and missing files.  I search the forums and came up with the following threads:

[http://ubuntuforums.org/showthread.php?t=91214](http://ubuntuforums.org/showthread.php?t=91214)
[http://ubuntuforums.org/showthread.php?t=143939](http://ubuntuforums.org/showthread.php?t=143939)

These are pretty old and when I tried

mv ~/.gconf/apps/rhythmbox ~/.gconf/apps/rhythmbox.old

Rhythmbox still searched for the files in the old location.  The threads mention a file by the name of rhythmdb.xml, but I can't find that on my computer.  There does not appear to be any Rhythmbox files in .gnome2.  Does anyone know where this file lives and what it's called?  I'm using Ubuntu 10.10 netbook remix and Rhythmbox 0.13.1-0ubuntu6.  Any help appreciated.

---

### Post by Phillip Spencer on 2011-01-07
The location of Rhythmbox files changed a while back (foxing me when I wanted to do backups after upgrading!).   I am currently using Ubuntu 10.04, 10.10 and Linux Mint 10.  All of these have the rhythmbox files, including rhythmdb.xml, in the hidden directory username/.local/share/rhythmbox

Hope it is the same in the version you are using.
Cheers
Phillip

---

### Post by therieb on 2011-01-09
Sweet!  There it is.  Thanks a lot.

---

### Post by NeilHoskins on 2011-11-19
username/.local/share/rhythmbox?

I presume .local is some kind of hidden folder because, as a normal user, I can't see it in the normal file browser.  I presume I need to do something from the command line with root permissions?  Or is there a simpler, gui method of resetting rhythmbox's library?

---

### Post by Tank Jr on 2011-11-22
File names starting with a period (.) are hidden files. You can see them by opening the folder in the file browser and then pressing Ctrl+H.
For example, to see the .local folder, you open the file browser, and when you see the contents of your home, press Ctrl+H. Once done, you see the folder, and you can use the file browser to open it, look at what it contains and so on.
Hope this helps.
PS:
If the folder is in you home, typically root access will not be required to do anything to it.

---

