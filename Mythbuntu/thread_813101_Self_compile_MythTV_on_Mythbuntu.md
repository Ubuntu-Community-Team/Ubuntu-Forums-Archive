---
title: "Self compile MythTV on Mythbuntu?"
date: 2008-05-30
forum: Mythbuntu
---

### Post by MrMunkily on 2008-05-30
Thinking of switching from Ubuntu with a manual Myth install to Mythbuntu... It looks great! I just have a few concerns.

Does Mythbuntu play nicely with a self-compiled MythTV in /usr/local? I need to run SVN for some bug fixes and themeing work. Will the GUI control center work well with a self-compiled binary?

Also, can I install software & libraries from Hardy's repos?

How does the X86_64 version handle Win32 codecs? Will it use a 32-bit Mplayer?

---

### Post by superm1 on 2008-05-30
> **MrMunkily said:**
> Thinking of switching from Ubuntu with a manual Myth install to Mythbuntu... It looks great! I just have a few concerns.

Great!

> 
Does Mythbuntu play nicely with a self-compiled MythTV in /usr/local? I need to run SVN for some bug fixes and themeing work. Will the GUI control center work well with a self-compiled binary?

What types of fixes are you looking for?  We can always pull extra stuff into the weekly builds and you can use those.  It's much nicer to go that route rather than having to hand compile stuff.

If you really need a self compiled, you will lose some of the nicities that we prepatch in certain paths, start and stop services when running mythtv-setup, and proper group checking.  All in all, most preferable to either build your own "packages" using our source packages or use weekly for your case

> 
Also, can I install software & libraries from Hardy's repos?


Of course

> 
How does the X86_64 version handle Win32 codecs? Will it use a 32-bit Mplayer?
You can install them if you'd like, but realize that most of  the win32 codecs have open source variants available now adays (even wmv)

---

### Post by MrMunkily on 2008-05-30
> **superm1 said:**
> What types of fixes are you looking for? 

Actually, now that I think about it, there probably isn't anything I need. I need to keep up with .22 development... but NOT on my TV machine :) that would be... foolish.

Are you guys making weekly builds from svn head? From what I've read, it's under major reconstruction (MythUI) and doesn't really work yet.

---

### Post by superm1 on 2008-05-31
As far as i know there are weekly builds of head too, but yeah still not usable.

---

### Post by MrMunkily on 2008-05-31
Actually - while I don't need new MythTV versions, I DO need svn versions of ffmpeg - I tried out the livecd and unfortunately hardy's ffmpeg is too old to play my odd hardware-encoded h.264 files. I think this pretty much requires me to recompile myth as well if I wanted to use it... But I guess I could build from your deb-source and do it "properly"?

---

### Post by laga on 2008-05-31
Currently, there are no weekly builds of head. I haven't updated the packaging scripts to QT4 yet.

---

