---
title: "Password prompts during install"
date: 2007-10-29
forum: Mythbuntu
---

### Post by subliminalbrad on 2007-10-29
I've been trying to install Mythbuntu on my media center PC, but I keep getting a password prompt from gksu. Once before the desktop appears, and again when I run the installer. 

It seems to accept a blank password, but when I try to run the installer, nothing happens after the password prompt. I tried running it from the terminal, but sudo doesn't accept a blank password and I can't find any password documented anywhere.

I ran the CD checker from the boot screen, and checked the md5sum of the ISO, both check out. I've also burned a second disc just in case the first one had problems but the second disc behaves the same way. Please help!

---

### Post by superm1 on 2007-10-29
> **subliminalbrad said:**
> I've been trying to install Mythbuntu on my media center PC, but I keep getting a password prompt from gksu. Once before the desktop appears, and again when I run the installer. 

It seems to accept a blank password, but when I try to run the installer, nothing happens after the password prompt. I tried running it from the terminal, but sudo doesn't accept a blank password and I can't find any password documented anywhere.

I ran the CD checker from the boot screen, and checked the md5sum of the ISO, both check out. I've also burned a second disc just in case the first one had problems but the second disc behaves the same way. Please help!
Well this is really odd.  Can you try to launch ubiquity from a terminal and see if you are getting a backtrace?

---

### Post by subliminalbrad on 2007-10-30
I'm getting I/O errors with a vanilla Ubuntu install, this is starting to look like bad hardware. I'll replace the optical drive and try again.

---

