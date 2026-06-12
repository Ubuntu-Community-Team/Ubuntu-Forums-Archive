---
title: "Lost GB's of data, because of wrong assumption about Mac OS X behavior"
date: 2008-02-19
forum: Mac OSX
---

### Post by Sammi on 2008-02-19
I just caused my father in law to loose gigabytes of backup files because I made a wrong assumption about Mac OS X behavior.

He has a Macbook and had been moving a large folder and all its content to a external HD, but half way in the transfer got interrupted because of a non-standard letter in a file or folder that the FAT filetable on the external drive couldn't handle. He proceeded  to remove the files from the laptop that had been successfully transfered, and called for my help.

He was not sure what the name of the file or folder that was causing troubles was, and I figured that the only way to find out, was to recreate the problem. So I, in my infinite wisdom, started the transfer again by dragging the folder from the desktop to the external HD, and choose "replace" when it asked, just as I've become accustomed to do after years and years of Windows and Ubuntu conditioning. 

I don't have much experience with Mac OS X, but just assumed that it would do the same as Windows and Ubuntu do. They only add missing files and overwrite files that are already there, and leave other files alone, but it seems that Mac OS X does things a whole lot differently. It does not keep the files in the folder it overwrites. Nope. I starts out clean, and then copies what supposed to be copied.

The thing is, my father in law had already deleted what he had skillfully managed to backup to his external drive, meaning that it all was lost. Just lost. Because I made a wrong assumption about Mac OS X behavior.

](*,)

---

### Post by ryanhaigh on 2008-02-19
One of the better things about FAT filesystems, although I am assured by the ExtFS devs that its purely accidental, is that files can be recovered once deleted rather easily. Of course the fact that you may have written over the deleted data may make things more difficult but you should be able to recover at least some of the deleted data. Perhaps you could mention to your father in law that it's always a good idea not to delete your original files until your backup is complete I experienced a similar problem when backing up another persons files to my samba server, a few long filenames prevented the copy from completing.

---

### Post by Demio on 2008-02-21
That's your own fault. Replace means replace, not merge.

---

### Post by Sammi on 2008-02-21
> **Demio said:**
> That's your own fault. Replace means replace, not merge.In Win and Ubuntu replace means "replace the files that exist in both places and leave everything else in the destination folder be". And that's the safest behavior IMHO. Especially when Mac noobs, like me, are tired and impatient and end up assuming dangerous things.

---

### Post by seanc7 on 2008-02-21
> **Demio said:**
> That's your own fault. Replace means replace, not merge.

Except in Windows and Ubuntu, where replace means copy new and ask if it's okay to overwrite the existing files with copies from the source. It doesn't clear out the folder and start again.

If you've never used MacOS then it's an understandable mistake. If you can look for any MacOS undelete utilities. Like back in the days of DOS, undelete was a lifesaver.

Actually I just thought of something, have you checked in the recycle bin to see if the files are there?

---

### Post by tehet on 2008-02-21
Sammi,
perhaps you can try az's recue-mix:
[http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

---

### Post by Sammi on 2008-02-21
It's a PPC Mac. Does anyone know of a ppc based live cd that has testdisk/photorec on it?

---

