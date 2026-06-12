---
title: "unarchiving .rar archives"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by alfreddo on 2007-11-28
I have the unfree version of Unrar installed (Ubuntu v.6.06, KDE desktop). Using Archive Manager,  It successfuly unarchived and combined some .rar parts, but when I sought to extract the resulting file I was asked for a password. 

I then unarchived and combined the identical .rar parts using WinRar on my Windows XP machine and the resulting file extracted and ran without any problem.

I have since experimented with other .rar archives. WinRar on the Windows PC unarchives, combines and extracts them all without prompting for a password. Unrar on the Linux PC asks for a (non-existent) password every time.

So I find I am still reliant on Windows.  Any solution?

---

### Post by kdarkentity on 2007-11-28
Hmm... i do believe in the past i have done this as well only it worked in reverse. I downloaded a .rar file that was divided into 5 parts and when i tried extracting it with windows it prompted me for a password, so i booted into linux and used the archive manager to extract the files and no password was necessary. 

Does your archive manager for linux always require a password to extract your files? Or is it simply this one archive you downloaded?

---

### Post by alfreddo on 2007-11-28
I've tried a couple of other .rar archives that extract OK using Windows, but in each case Linux has asked for a password.

The Archive Manager help file states that passwords are currently only supported for two types of file - .zip and .arj. Definitely not .rar

---

### Post by kdarkentity on 2007-11-28
hmm... well you could probably always just use winrar in wine or crossover

---

### Post by alfreddo on 2007-11-28
Yes, that might be the only short-term solution, loth though I am to be dependent on Windows in any way.

I have downloaded the basic Linux version of WinRar - called RarLinux - but so far have failed to install it. Following these instructions in the Readme file just produces error messages in the terminal:

mkdir -p $/usr/local/bin
mkdir -p $/usr/local/lib
cp rarfiles.1st /etc
cp default.sfx $/usr/local/lib

I'm flying blind with this stuff most of the time.:confused:

---

