---
title: "Jaunty : where did my UMS walkman go ?"
date: 2009-04-26
forum: Multimedia Software
---

### Post by chewif on 2009-04-26
Hi,

I originally bought the sony NWZ-A816 mp3 player cause it had ums support and could be used on my ubuntu machine.
However since I upgraded to jaunty the thing is behaving as a MTP device.

I felt much more confortable using the UMS mode.

Is there any way I can tell the automounting process to go back to the way things were under the previous versions ?

Thx

---

### Post by pasti on 2009-05-08
Hello Chewif

I had this problem with my walkman an NWZ-A818 In hardy 8.04, it worked perfectly in Intrepid 8.10, and now the bug's back in jaunty,anyway there's a really simple fix.

plug in your walkman, it should be detected,

The nautilus file browser will open a window with a button at the top left offering to open Rhythym box, don't click the button, instead right click the blank window directly underneath, and choose the "create new folder" option in the context menu that has just opened, you don't have to name this folder, just leave it as "untitled folder".

DON't & I can't stress this enough, delete this folder from this window as you will delete all the files on your walkman

open this folder as you would any other folder, and you will see all the files on your walkman,including the "untitled folder" go into the "music" file and all your music should be accessible as normal.

The next time you mount the walkman you will have to go through this again, i.e create a new folder, but this time when you open it up you will see "untitled folder 2", I just delete the first one to keep things tidy.

I realize this isn't a particularly clever fix, some people edit the gphoto settings, but it works for me, hope it works for you too

good luck! & remember the ipod isn't the only game in town

---

### Post by apolonio on 2009-05-08
thanks! It is working for me too in Jaunty, but somehow this bug is strange, this sony should be pretty much compatible, with ubuntu hardy there was a work around changing and recompiling the code of hal, with fetsy gibon I had no problems at all. Perhaps time to change to an Ipod????.

---

