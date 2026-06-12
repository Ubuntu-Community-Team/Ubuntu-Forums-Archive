---
title: "Emu 1212m No sound before or after ALSA Upgrade"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by margotcopeland on 2007-06-21
Hi.

I'm fairly new to Ubuntu, and have wanted to go open source for my project studio for a long time.

I Installed my Emu 1212m...no sound. So I spent the next two days reading and trying to get to the root of the problem.

After reading a number of forum articles, it seems that UStudio has an older version of the ALSA drivers, and the current -14rc's make the 1212m work :-)

I downloaded the drivers, lib, and util files..../configured (Igot stuck - UStudio doesn't include complete sourcecode headers and such. Found them...installed them...and I was on my way...Till another thing called "curses" but me in the bum. Installed them.

Finally able to go! Stopped Alsa,  conf...make...make install on all 3 in the right order.

I bootted up...and no sound. Tried to get to the mixer to "unmute"...no mixer was available because no sound card was available???? It's there and working in Vista...but not with Ubuntu :-(


I REALLY would love this all to work (Midisport 4x4 is another hell to come), but all this command line stuff,...all I want to do is play my music...and I seem do far aay from doing that.

Would anyone have any suggestions, instructions, and helpful hints that would make this journey feel a little less siberian trek  and a bit more Fiji???

Thank You & Namaste,

Ms Margot Copeland

---

### Post by MEW on 2007-06-21
This may seem like a stupid question... but, did you load the modules that you compiled into the kernel? Ubuntu won't automagically load them on bootup unless you tell it where they are. I think that the command to load the modules for that card would be ```

modprobe snd-emu10k1-fpga 
```

---

### Post by margotcopeland on 2007-06-22
> **MEW said:**
> This may seem like a stupid question... but, did you load the modules that you compiled into the kernel? Ubuntu won't automagically load them on bootup unless you tell it where they are. I think that the command to load the modules for that card would be ```

modprobe snd-emu10k1-fpga 
```


Here's what I got when I ran the command:

margot@ubuntustudio:~$ modprobe snd-emu10k1-fpga
FATAL: Module snd_emu10k1_fpga not found.
margot@ubuntustudio:~$ 

I'm really new at this. Does this mean when I added the source code parts it needed                                          to be able to compile it might not have put them in the right place?  After getting the  things to compile and insta[l, it would just be a matter  of unmute and play,,.nope  :-(

At this point I'm tempted to do another clean install...but if my basics are way off it would just be asking for the same results. Could anybody (especially someone using Ubuntu Studio?) help me...I's so much appreciate it!

Thank you so very nuch!

Ms Margot Copeland

---

### Post by Mr. Lobster on 2007-08-20
using a clean install I had the same issue.

---

### Post by hetbeest on 2008-02-13
Margot, did you get it working? If not, look at [http://ubuntuforums.org/showthread.php?t=367324](http://ubuntuforums.org/showthread.php?t=367324)

---

