---
title: "bullets in folder names"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by nixIT on 2009-02-24
Hello all,

I recently installed Ubuntu Ibex on my work laptop, previously had Fedora 9 on it.

Everything so far has been running smoothly, more so than with Fedora 9.  However, when I access our network share, which is a NetApp device set up with CIFS, some of the folders/directories were created with bullets in front of them.  Why you may ask, uh, the honest answer is our users are idiots and they wanted those folders to appear at the top of the folder list in windows.  don't ask me, they are lazy.  

Anyway, I have the folders mounted the same way I did in Fedora, but those folders with bullets in the front of the name are showing up as question marks (ie. ??Folder1, ??Folder2, etc).  When I try to view the folder contents in Ubuntu I get the following:

> 
**The folder contents could not be displayed**
"??Folder1" could not be found. Perhaps it has recently been deleted


This worked fine in Fedora, and I can navigate to the folders in Windows with no problem.  

Is there a way I can navigate to these folders and get to the files?

/nixIT

---

### Post by puppywhacker on 2009-02-24
the question marks are unprintable characters. not literal characters. if you use them in commands the are wildcards for a single character. like an asterisk (*) is a wildcard for multiple characters. Apparently your cifs characterset between Fedora and Ubuntu is different. Your bullit is most likely a 2 byte character.

You can fix it for good by mounting the drive with an option like iocharset=utf8 (or another set depending on your country)

you can copy the data out of the folders on the command line
cp -R *Folder1* /tmp/FOL1

(I say we all use UTF-8 and live in piece and harmony)

---

### Post by nixIT on 2009-02-25
Thanx for the info, though the iocharset=utf8 did not help, I am still getting the error message.

I would love to copy the files out of the directories and remove all leading spaces and goofy-***(tm) characters from filenames, but again, this was setup this way because our users are lazy to look through a folder listing for the one they want.

any other ideas that will allow me to read/write to these folders?

---

### Post by nixIT on 2009-02-27
bump.

Any ideas how I can get access to read/write to these folders?  This worked fine in Fedora 8/9/10.  This is the only issue I've found with Ubuntu so far.

/nixIT

---

