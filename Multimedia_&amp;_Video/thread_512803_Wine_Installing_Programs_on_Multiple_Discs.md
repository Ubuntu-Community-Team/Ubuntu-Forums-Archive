---
title: "Wine: Installing Programs on Multiple Discs"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by hnaamyilkemku on 2007-07-29
Hello all,

I've successfully downloaded and configured wine and installed Steam. Now I'm trying to install CSS off of multiple CDs, but when the installer prompts for the next CD Ubuntu does not let me eject the first one because a program--presumably wine--is still using it. Does anyone know how to address this problem? I'm aware of several workarounds for this particular installation--e.g. downloading my brother's CSS directory, downloading from the Internet, etc.--but I'd like to know for future reference how to do this. Thanks!

---

### Post by srhlefty on 2007-07-30
I've taken this text from the Descent 3 AppDB page ([http://appdb.winehq.org/appview.php?iVersionId=884](http://appdb.winehq.org/appview.php?iVersionId=884))

> 
Use standard multi-CD installation procedure:

   1. Map your CD-ROM to a drive (say d:) using winecfg
   2. Insert CD and mount it
   3. From _outside_ of CD-ROM mount point (cd ~) run wine 'd:\setup.exe'
   4. When prompted for CD2, in the _separate_ terminal run wine eject d:
   5. Repeat steps 2 - 4 for each CD 


I've not done this personally, so I can't guarantee that it works, but it's worth a shot.

---

### Post by rkrisher on 2008-06-13
I just discovered by playing around and tested a way to do it before I come across this post.  Spreading it around to a lot of posts because I've been searching for months.

in terminal or under start/run, type "wineconsole cmd"

This brings you to a windows like dos terminal.

change into your CDROM disk typing "d:" or whatever your drive letter is

type in your setup program name, i.e.: "setup.exe" or "install.exe"

the install will start. Change to your C drive with "C:"

When prompted for disk x, type in "eject"

insert next disk and continue.

Repeat until application is complete.

Remember to let your CD auto-mount by selecting "open in window" or manually mount it before clicking OK at the "Insert CD X" prompt.

Hope it helps.

BTW, you need to use dos commands when exploring around in the command prompt.  Like "dir" instead of the "ls" we got used to.

---

