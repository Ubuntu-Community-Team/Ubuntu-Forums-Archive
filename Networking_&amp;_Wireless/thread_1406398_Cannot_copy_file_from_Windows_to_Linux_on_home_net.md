---
title: "Cannot copy file from Windows to Linux on home network"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by finsyourfriend on 2010-02-13
Greetings all! I must say, it's been a pleasure using Ubuntu, but I've come across a interesting situation:

When I attempt to copy a picture named 2pfennigobverse from my Windows based PC to my Linux box, I get the following error message:

"Error Copying File or Folder

Cannot copy 2pfennigobverse. Access is denied.

Make sure the disk is not full or write-protected 
and that the file is not currently in use."

Thing is, I can copy pictures from Linux to Windows just fine.

Thoughts?? :?:

---

### Post by finsyourfriend on 2010-02-14
Found a work-around; copied the picture to the shareddocs folder on the Windows PC and accessed it via Ubuntu. All is well.:D

---

### Post by sgosnell on 2010-02-14
That's one way, and probably the safest.  You can't write to a folder in your Linux box unless the permissions are set to let the world write there, and that isn't something you want to do lightly.  You can set one folder as writable by the world, however, for copying files there, and you can later move them when you're on the Linux machine.

---

