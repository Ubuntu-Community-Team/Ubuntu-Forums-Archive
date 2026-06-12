---
title: "Rhythmbox + iPod: Deleting Music doesn't free space"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by gdi2k on 2006-12-01
It's great to see that Edgy's Rhythmbox finally supports writing to ipods as well as reading them! 

The problem I've noticed with it though is that if you remove songs from the ipod through rhythmbox, although they don't show up on the ipod any more, the space that the songs occupied is not freed, resulting in an ever-filling ipod.

Is this is known issue? I can correctly remove tracks using gtkpod.

---

### Post by tom56 on 2006-12-01
Maybe you removed them from the Rhythmbox library not the drive? There are two options in the right click menu.

---

### Post by OffHand on 2006-12-01
> **tom56 said:**
> Maybe you removed them from the Rhythmbox library not the drive? There are two options in the right click menu.

The deleted files are probably in a hidden .trash folder.

---

### Post by Dubbayoo on 2006-12-01
I don't have mine with me to test but I had a similiar issue once; I can't recall which app it was with though. I do recall that after you drag/drop/delete files you had to actually SYNC it as a separate step. Perhaps that is what you are leaving out?

---

### Post by lwtinman17 on 2006-12-01
When ipod is plugged in try emptying your trash.  Ran into same problem moving music from one computer to another.

---

### Post by gdi2k on 2006-12-02
Thanks for your quick responses! 

[QUOTE=tom56]Maybe you removed them from the Rhythmbox library not the drive? There are two options in the right click menu.[/QUOTE]

Yeh, that's what it feels like. There are 2 options when you right-click songs, "Remove" and "Move to Trash", but "Remove" is grayed out, so I can only use "Move to Trash". 

I've also tried emptying the Trash can, but there's no music in there. I've also browsed the entire iPod drive looking for .Trash directories (with "Show hidden files" enabled of course), but there's nothing there. 

[QUOTE=Dubbayoo]I don't have mine with me to test but I had a similiar issue once; I can't recall which app it was with though. I do recall that after you drag/drop/delete files you had to actually SYNC it as a separate step. Perhaps that is what you are leaving out?[/QUOTE]

There is no sync button or anything like that in Rhythmbox - there's only an eject button which is iPod specific, so I can't perform a seperate sync step. 

Maybe it's a known problem in Rhythmbox. I'll see if I can find a bug on their site.

Thanks!

GDI

---

### Post by gdi2k on 2006-12-02
Yeh, it seems this is a known issue which has been fixed (to some degree) in development versions, so it will only be a matter of time until they trickle down into Ubuntu. Maybe it'll be fixed in Feisty Fawn...

[http://bugzilla.gnome.org/show_bug.cgi?id=346434](http://bugzilla.gnome.org/show_bug.cgi?id=346434)

---

### Post by equal on 2007-04-11
Nope, still not working in Feisty. :(

---

### Post by el_rata on 2007-04-14
SH*T ... i'm having the same problem .... i'll dig into it ... when i have some answers i'll post them here .... until then good luck with it ....

---

### Post by Phantommxr on 2007-04-14
good info...thx

---

### Post by jshaffer on 2007-10-25
The "gnupod_check --fixit" utility suggested at [http://bugzilla.gnome.org/show_bug.cgi?id=346434#c24](http://bugzilla.gnome.org/show_bug.cgi?id=346434#c24) makes this issue a lot easier to deal with.

---

### Post by hardrock on 2007-10-26
It's really annoying that this bug exists for ages and still hasn't officially been fixed ...

---

### Post by techstop on 2007-11-10
> **hardrock said:**
> It's really annoying that this bug exists for ages and still hasn't officially been fixed ...

I'll say! Gah! Please fix it already. It's the *default* music player for ubuntu, you would expect it would work by default.... :(

---

### Post by Slim Backwater on 2008-04-08
I just ran into this.  I couldn't figure out why 400MB of song was filling a 1GB iPod.

I had to apt-get install gnupod-tools then gnupod_INIT -m /media/IPOD, then gnupod_check -m /media/IPOD then gnupod-check -m /media/IPOD --fixit and finally gnupod-check -m /media/IPOD  I thought about also doing an apt-get remote gnupod-tools to cleanup, but I'll probably need them the next time I delete a song.

So for others, if you want to delete a song from an IPOD, first right-click the song and choose move to trash, then exit RythmBox.

Then start a terminal and type these commands
1. df to identify where your iPod is mounted.  It will be under /media

2. sudo apt-get update

3. sudo apt-get install gnupod-tools

4. gnupod_INIT -m /media/{yourIPodname}

5. gnupod-check -m /media/{yourIPodname}

6. gnupod-check --fixit -m /media/{yourIPodname}

7. gnupod-check -m /media/{yourIPodname}

8. exit # to close the terminal

After the first time, you'll only need to "move to trash" and then do steps 5-8 after deleting a song.

These are alot of steps for a beginner to do, does anyone know if this might be fixed in 8.04?

Running Ubuntu 7.10.

Thanks.

---

### Post by Hiperi0n on 2008-06-18
Well, this wasn't solved in Hardy either, however after a gnupod_INIT the Ipod seems fine to work with rhythmbox. Moving songs to trash wipes them out of the Ipod entirely :guitar:

---

