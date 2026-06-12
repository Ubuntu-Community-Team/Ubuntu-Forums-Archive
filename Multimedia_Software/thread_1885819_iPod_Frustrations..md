---
title: "iPod Frustrations."
date: 2011-11-23
forum: Multimedia Software
---

### Post by Roasted on 2011-11-23
I have an iPod Nano that I'm trying to work with here. It already has a music library on it and I'm doing my best to retain that. Likewise, I want to make it work on Ubuntu full bore. I don't care which application I use for it, though I've always liked Rhythmbox.

I noticed I can pull off the old library by simply opening it, selecting all, and dragging (within Rhythmbox) the highlightetd library to a bookmark on the side, in my case, Music. Then it copies accordingly so I can at least work from that library set.

But the problem I'm running into is pushing new files to it. I get a read only error. When I put the iPod into my Macbook Pro I can see it's HFS Journaled within disk utility. I tried to format it with OSX's disk utility to a non-journaled file system but it errors out. On top of that, it errors out on Ubuntu when I try to format in disk utility or even gparted.

So anyway, here is my goal. I want this iPod Nano to work on Ubuntu. That's it. :)

---

### Post by wolfen69 on 2011-11-23
Have you tried gtkpod? Always worked for me. Ymmv.

---

### Post by Roasted on 2011-11-23
> **wolfen69 said:**
> Have you tried gtkpod? Always worked for me. Ymmv.

What file system is your iPod?

EDIT - so I was reading this link a bit:

[http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

Does that mean that in order to initiate a NEW iPod on an Ubuntu system? Would I NEED Windows to initiate it or is that what the Rhythmbox iPod initialize thing is that comes up? If I recall, I used that feature, and got no where... but I may be wrong.. Hmm??

---

### Post by dusanyu on 2011-11-24
your iPod is going to have to be converted to FAT32 in order to use it 

this link is old but most of it apply when it comes to file systems 
[http://people.csail.mit.edu/adonovan/hacks/ipod.html](http://people.csail.mit.edu/adonovan/hacks/ipod.html)

or have a look at [http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

---

### Post by Roasted on 2011-11-24
So more or less, it has two partitions. One for the firmware OS, one for data. The data partition is HFS+ until Windows triggers it to format in FAT32 for Windows usage.

Okay, great.

Is there no trigger to make it automagically work in Linux? Speaking of which, if I format the 2nd partition to FAT32, why does that not work? In GParted it comes up as one solid unallocated partition. In Disk Utility, it comes up as two partitions, but when I try to format the HFS+ partition to FAT32, it errors out.

Likewise, Mac users are telling me on my Macbook Pro in their Disk Utility application I should have a format to MSDOS (FAT32) option, but I do not. It struck them as weird, but nonetheless, it's just not an available option.

So anyway, what do iPod users do when they're also Ubuntu users? I thought iPod/Linux was fixed years ago. Why is this such a hassle? Am I just going about it wrong?

---

### Post by skit85 on 2011-11-24
My ipod worked without any issues but i had originally formatted from a windows machine..

My Gf has an iphone which is synced to her imac so i might have a play around with that and see what i can work out for you ive never seen it being such a problem...

---

### Post by Roasted on 2011-11-24
Maybe I have to fire up my Windows partition and see what happens. So far all I've done to get it going is from OSX and Linux.

Can anybody who bought an iPod with having 100% Linux machines around comment? I wonder if most iPod/Linux users out there tend to make a pit stop at Windows before they get it fully working... I mean, it makes sense, I just thought some utilities in Linux were able to handle that job as well.

---

### Post by skit85 on 2011-11-24
If you have a windows partition, can you not just copy your library to linux then format your iPod through windows? that should give you what you want....

---

### Post by Roasted on 2011-11-25
Yes, but that's not the direction I'm wanting to go. The idea is to get this iPod working from start-to-finish front-to-back left-to-right in Linux without the use of iTunes, OSX, or Windows.

---

### Post by wolfen69 on 2011-11-25
You never said whether you had tried gtkpod or not.

---

### Post by Roasted on 2011-11-25
> **wolfen69 said:**
> You never said whether you had tried gtkpod or not.

Did you run the iPod from day one in gtkpod? Or did you use Windows or Mac to initialize it?

---

### Post by wolfen69 on 2011-11-25
> **Roasted said:**
> Did you run the iPod from day one in gtkpod? Or did you use Windows or Mac to initialize it?

I'm not sure I know what you mean by "initialize it", but I got my ipod from someone else and did a "reinstall" of iOS in itunes before using it. It worked straight away in gtkpod after doing that. But if apple is now using a different version of ios, it may not work. There's only one way to find out.

---

### Post by Roasted on 2011-11-25
I'm not entirely sure I know how to use this gtkpod. All options I select just do nothing. Load iPod, Load selected iPod, etc. Each option I use is just not doing anything, yet the iPod is plugged in. It doesn't look as straight forward as, say, Rhythmbox is where it has it listed on the left side. Am I missing something?

---

### Post by dankegel on 2011-12-19
gtkpod is broken for me right now; it always outputs
** (gtkpod:2544): CRITICAL **: repository_ipod_init_set_model: assertion `gtk_combo_box_get_active_iter(cb, &iter)' failed
so I can't use gtkpod.

I see this at
[http://www.gtkpod.org/bugs/index.php?do=details&task_id=70](http://www.gtkpod.org/bugs/index.php?do=details&task_id=70)
but not yet in
[https://launchpad.net/ubuntu/+bugs?field.searchtext=gtkpod](https://launchpad.net/ubuntu/+bugs?field.searchtext=gtkpod)

Amorok doesn't work, either.

I had to run iTunes in Windows to re-intialize and sync to my iPod :-(  See my notes at [http://kegel.com/linux/play-audiobook-on-car-stereo.html](http://kegel.com/linux/play-audiobook-on-car-stereo.html) for how to work around iTunes problems on Windows.
Sadly, iTunes doesn't sync to iPods if run in Wine.

It's kind of sad how broken this all is.

---

### Post by Roasted on 2011-12-20
[QUOTE=dankegel]

It's kind of sad how broken this all is.[/QUOTE]

We ARE talking about an Apple product here. You know how much they like their control. That said, I've had some good luck on both Rhythmbox and Banshee lately. Even Clementine I think was behaving for me once I initialized it on a Windows computer. Kind of stupid I had to do that, but whatever.

Mental note taken. Avoid iPods.

---

