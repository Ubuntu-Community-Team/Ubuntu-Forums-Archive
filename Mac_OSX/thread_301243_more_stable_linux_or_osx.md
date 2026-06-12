---
title: "more stable: linux or osx?"
date: 2006-11-16
forum: Mac OSX
---

### Post by bionnaki on 2006-11-16
what os is more stable: linux or osx?

---

### Post by Polygon on 2006-11-16
either the same, or most likely linux is most stable (especially distros that have very strenuous testing procedures like Debian)

---

### Post by engla on 2006-11-16
Equally? OS X is really stable, and I have run this laptop on both OS X and on Dapper Drake for more than 30-35 days without reboot. 

As a long-time OS X user, I only know one bug that forces me to reboot the computer, it's an obscure Pasteboard (copy-paste thing) bug I found when programming. You can load lots of stuff with rich types into the OS X pasteboards (lots of kudos to apple, much cooler than gtk sadly), but when you do certain things right (wrong), the system just yikes out and you can't launch applications unless you reboot. Yes, I've tried killing services and logout-login.

I regard them as equally stable. But ubuntu/linux allows you to play with more stuff, and if you do, linux quickly destabilizes (at least for me when I tried compiling and replacing kernel, xorg, compiz etc). But it's just that you can't do much with the kernel or window server in os x that adds to its stability.

---

### Post by jnev on 2006-11-16
os x has not been very stable in my experience (though I only use it for final cut pro, so the fact that it's so intensive may have something to do with it). linux is VERY stable for me, in the three years I've used it it's only crashed (by crashed I mean full system freeze, like nothing short of hard reboot will work) twice. pretty good I think. apps aren't as stable with beryl but I think it's worth the tradeoff as I don't do anything that important.

---

### Post by grte on 2006-11-17
Debian.

---

### Post by aysiu on 2006-11-17
Moved to Mac OS X.

---

### Post by Sunnz on 2006-11-17
> **engla said:**
> I regard them as equally stable. But ubuntu/linux allows you to play with more stuff, and if you do, linux quickly destabilizes (at least for me when I tried compiling and replacing kernel, xorg, compiz etc). But it's just that you can't do much with the kernel or window server in os x that adds to its stability.

XNU (the OSX Kernel) is open source, right?

---

### Post by grte on 2006-11-17
> **Sunnz said:**
> XNU (the OSX Kernel) is open source, right?

Used to be, but they've since closed it.

---

### Post by Sunnz on 2006-11-17
Really? I have heard the opposite. :s

---

### Post by engla on 2006-11-17
It is closed on intel macs I believe, or at least signed or something like that. I've never tried recompiling the kernel, and there is no movement or group in the os x community that does it, so I have no idea what to do or what I could change. OS X is simply not about that.

---

### Post by earobinson on 2006-11-17
you cant just say something is more stable than something else you need to give me an idea of what your looking for in terms of stability.

for example a honda may be more stable than a hummer on the road but in a war a hummer is more stable than a honda

(I know nothing about cars)

---

### Post by doobit on 2006-11-17
I've been playing with an ibook with OSX Panther on it here, and the terminal works just like Linux. In fact I changed the admin's password and set sharing on some of his prevously locked folders - all with his permission, of course.
The whole OSX seems very Linux-like.

---

### Post by earobinson on 2006-11-17
OSX is built on the unix kernel im pretty sure

---

### Post by fuscia on 2006-11-17
> **earobinson said:**
> OSX is built on the unix kernel im pretty sure

[http://en.wikipedia.org/wiki/OSX](http://en.wikipedia.org/wiki/OSX)

---

### Post by Sunnz on 2006-11-18
OSX uses a Hybird Mach Micro-kernel, and some large part of it is actually FreeBSD...

I heard Leopard is gotta to get UNIX-certified next year too... so yea, if you are familiar with Linux, using Unix is a piece of cake.

---

### Post by hoagie on 2006-11-18
I really like OSX and I love Ubuntu. They both are stable, secure and run faster on my machine, than windows. I have to say that OSX looks a bit more professional (well it's a huge corporate product) but since Ubuntu 6.10, I think both systems are equivalent stable.

---

### Post by bhuot on 2006-11-20
I use both on different computers sharing the same cable Internet connection. OS X has not crashed on me in at least 2 years. One thing I like about the updates to OS X is that they come in a set of a whole bunch of them, so I can wait a week and see how the adventurous are doing and then apply the update when I have confidence it doesn't screw anything up. With Ubuntu issuing updates continually I am not able to verify that individual updates are working fine, so I just don't update at all anymore, after being burned with X-Windows going down in a Dapper update and the kernel screw up in an Edgy update - hosed all USB connections. Now I have Edgy RC without any updates and it works fine. I am actually using my Linux box for web browsing and graphic design (I know that sounds funny), since I use mostly open source design tools now the X-Windows based ones are easier to use on Linux. I would say Linux is much faster with half the RAM, but OS X does have better graphical capabilities than X-Windows (too bad you have to pay for a 3rd party application to make use of Quartz in vector drawing). I am using OS X for DVD-ROM burning as something is wrong with my DVD burner on Linux and my back up drive is HFS formatted which I don't use on Linux because it destroyed the file system before - I could share it but I don't want to use a FAT file system as it has such poor performance. I also do my web layouts and word processing on the Mac as that is where all my data is.

---

### Post by AlphaMack on 2006-11-24
I'd say about the same although there are times where GNOME will lock up OS 9-style for no apparent reason and no key combo will drop me into the console.

---

### Post by 3rdalbum on 2006-11-25
I find that Gnome is a bit unstable, but I rarely have so hard a crash that I can't get back to the command-line and restart X.

I haven't used OS X recently (the last time was a couple of years ago), but back then it used to crash all the time. And according to my father, who uses OS X a lot, it's SLOW. And if OS X crashes, there are no emergency keyboard combinations to write out remaining data and unmount your drives.

OS 9 is surprisingly stable on my iMac. No kidding, I once had a bomb message on OS 9 where I clicked the Restart button, the message disappeared and I could continue to use my computer without any problems. "I've crashed, now you've got to restart... hang on... no, it seems that I haven't crashed. Carry on."

---

### Post by wgscott on 2006-12-03
I've found that OS X is more stable compared to my PC linux installations. I think linux has a much harder job keeping all sorts of hardware compatible, whereas with OS X Apple has only its own hardware to worry about.

The main instabilities on OS X in my experience are due to the fragility of the HFS+ filesystem.  The Aqua GUI interface is a lot prettier than X11, but it is significantly slower than Xfce4 (not so sure vs. KDE). You can run X11 applications on OS X and they are pretty snappy, so it is the windowing system that is slower.

I seem to have to fsck with the underbelly of linux more than OS X.  I customize the crap out of both, but basic stuff like disk arbitration seems to me to be more fragile in linux (at least on my machine).  Ubuntu seemed to improve things a lot vs. the RH monster, but I still find my one Linux installation to be more needy of major intervention than my 10+ OS X machines combined.

NFS seems to work better on linux.  I had to turn the automounter off to get it to work right on OS X.

OS X seems to demand frequent restarts after software and security updates.  I don't think this is true of linux. I can't remember having to reboot due to any update (except version updates, and even then it wasn't obvious I had to).

I run a mailserver with OS X but I have a feeling it would be even more straightforward on linux.  Most stuff on OS X works out of the box, but I think they deliberately make setting up a mailserver hard so you will consider buying their OS X server edition.

---

