---
title: "how can i get an image off a dvd that stops reading"
date: 2008-08-28
forum: Multimedia Software
---

### Post by alexschnallex on 2008-08-28
hello, i am hoping i can maybe find some advise here...?...i burnt pictures on this one dvd on a laptop.....now i am trying to access them, some will let me do this and some wont. i tried opening them with photoshop, paint and other programs. that made the programs not respond anymore. i tried to copy the whole disc, but neither nero or power2go or cyberlinkDVDsuite could do it all the way, they all stopped half way cause they failed to read the disc due to corrupt image files (?)
i just really want to recover these pics...ahhhh!....anybody got any ideas?

---

### Post by djRobbieF on 2008-08-28
You're citing nothing but Windows applications.

Because this is an Ubuntu forum, I'm assuming you mean you burnt the disc on some form of *buntu, and can't read it on Windows; am I correct?

If that's the case, access the disc on an Ubuntu system.  Any luck accessing it?  If yes, transfer the files through the network or to a USB flash drive (which uses the Windows-friendly FAT32 filesystem in most cases).

It's worth a shot.

---

### Post by cariboo on 2008-08-28
You could also make an image of the dvd using dd. To do this in a terminal type:

```
sudo dd if=/dev/dvd of=dvd.iso
```

You may have to change /dev/dvd to what it is aliased to on your system to find out what is is aliased to in a terminal type:

```
ls /dev/dvd
```

On my system it is /dev/scd0.

Jim

---

### Post by djRobbieF on 2008-08-28
> **cariboo907 said:**
> You could also make an image of the dvd using dd.

Doesn't sound like a *damaged* disc to me though, Jim.  Sounds like he's burnt it in a format that's not compatible with Windows, and then trying to access it in Windows.

That said however, it is possible that the disc was burnt at high-speed, in which case the disc could be faulty.  So in that case, dd *may* in fact help by trying to make an image of the disc, and then just re-burn at a lower speed...

Anyone else wanna draw a straw?  :)

---

### Post by djRobbieF on 2008-08-28
... although unlikely, it struck me that it could also be a faulty DVD drive in the Windows computer that you're using to read the disc.

---

### Post by az on 2008-08-28
> **cariboo907 said:**
> You could also make an image of the dvd using dd. To do this in a terminal type:

```
sudo dd if=/dev/dvd of=dvd.iso
```

You may have to change /dev/dvd to what it is aliased to on your system to find out what is is aliased to in a terminal type:

```
ls /dev/dvd
```

On my system it is /dev/scd0.

Jim

I prefer GNU ddrescue.

sudo apt-get install gddrescue

and run

sudo ddrescue /dev/dvd image log

It will create a log of what it is doing so that you can resume the image creation if you stop it in the middle.  It will also skip errors instead of doing what dd would do - quit.  If it cannot read a particular block, it will fill that part of the image with zeros.  That minimizes data loss.

[http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

---

### Post by alexschnallex on 2008-08-31
oh, thank you so much for all the replies....!
no, i burnt the dvd on a window system,,,,i to be honest, i didnt know what ubuntu was. i'm not that good with computers i guess :-))
i already tried to burn an image(on 2 different windows laptops), but eventually it stopped reading and then just quit the whole process...
and i tried reading the disc in 4 different drives, some let me read more and some less, but all of them struggled with this one image folder.

@az: will this [http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery) help me on a windows pc?

---

