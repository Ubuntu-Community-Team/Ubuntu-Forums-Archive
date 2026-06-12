---
title: "How to initialize a blank CD/DVD &quot;Like a USB Flash Drive&quot;"
date: 2012-11-18
forum: Multimedia Software
---

### Post by stlu on 2012-11-18
Greetings everyone,

I because curious about this feature since a friend showed me a way to write to a CD-R that I never heard of.  It makes it feel like you can create files, delete files, etc, and keep adding files time and time again, of course until it is full.

He showed me how he creates it under Windows, and upon inserting the blank disk, you have the 'normal' option of burning like a CD/DVD (write-once) or the option to use the disk "Like a USB Flash Drive"

The method under Windows Vista/7 looks like this:
[http://www.youtube.com/watch?v=h9phpJ7py5M](http://www.youtube.com/watch?v=h9phpJ7py5M)

I researched and I understand that this filesystem is UDF+VAT, and the VAT is what allows for the flexibility of adding more files and marking files as deleted.

From these older threads, I can see that this has been a poorly-supported filesystem for anything beyond basic UDF (write-once, read-only) capabilities.

[http://ubuntuforums.org/showthread.php?t=1197627](http://ubuntuforums.org/showthread.php?t=1197627)
[http://ubuntuforums.org/showthread.php?t=848601](http://ubuntuforums.org/showthread.php?t=848601)

The big question is:

[LIST]
[*]Are there any changes to Ubuntu recently that would allow me to create the same UDF VAT filesystem on a blank CD/DVD?  Or a utility that I can install specifically for this task?
[/LIST]


_Using UDF+VAT filesystems after Initialization_

I have tested out a blank DVD-R which was initialized under Windows "like a USB Flash Drive".  I added files in two separate sessions.  I then tried out the DVD in a DVD-RW drive under Ubuntu.  The good news is that I can read the files from session #1 and session#2 as if they had been burned in one sitting.  The bad news is, so far it seems that I cannot mount it rw, even though it was inserted into a DVD-R drive.

I also opened the DVD under K3B, and it showed the previous two sessions, and appeared to allow me the option of writing a 3rd session.  However, I didn't carry this to completion because I was presented with a blank filelist to add into (I was expecting to see the current filesystem tree).  So it looks like K3B will add files in an isolated way. That isn't what I wanted. If I have a "Folder_01" containing File A and File B, I was able to add File C to the exact same folder under the Windows file manager.  This feature is what makes it so flexible compared to standard burning, which is to mix new files into various existing folders.

so, next big question

[LIST]
[*]Is there a way to make desired changes to the Windows-formatted UDF+VAT filesystems, so I could write, for example, a 3rd session to my test DVD under Ubuntu?  Or is there a third-party program that can do this?
[/LIST]

Also, I don't know which version number of UDF that Windows is creating with this method... is there a way to see that?

Thanks!

---

