---
title: "[SOLVED] 2009 won't install"
date: 2008-10-10
forum: Mandriva/Mageia
---

### Post by wolfen69 on 2008-10-10
i just tried the official release of both kde and gnome mandriva one. the live kde cd starts to boot, but stops part way through. next, the gnome cd tells me that it can't configure xserver and i must do this myself. ok, i put in the resolution and what not. i get to the desktop and click live install. i picked use existing partions and it tells me that i have to reboot for changes to take effect. huh? then i choose erase and use whole disk. tells me to reboot again. i then chose manual and again, reboot is needed. since i am in live mode, rebooting will have no effect.

what's up with this? every distro i've ever tried works good on this machine. *very* strange. and yes, the cd's were verified. btw, 2008.1 worked good for me.

---

### Post by AdamWill on 2008-10-10
Huh, that's an odd one - congratulations, you're the first person I've seen with that bug :). Um. What if you do custom partitioning, can you do it then? How about if you prepare the partitions in another distro before you boot One?

---

### Post by wolfen69 on 2008-10-10
i've tried custom partitioning and it was a no go. it's getting late, so tomorrow i'm going to try preparing the partitions ahead of time. i'll get back to you.

---

### Post by wolfen69 on 2008-10-11
well, i finally got gnome 2009 installed. had to pre-partition though. during install i had to set up xserver manually. ok, i finally get to my desktop and do updates. it asks me if i want to update my sources. yes i do. it gives me failed to fetch yada yada. cant update. next i add the plf repos. i thought it went well, but vlc fails to install. (missing too many packages)

on top of that, the version of vlc available is 0.9, which doesn't play nice with my tv tuner card. all in all, not a good first impression. i'm not saying it's bad, it just doesn't work *for me*. but i always have 2008.1 which pretty much worked near perfect. 

as far as the kde version, it starts to boot to live cd, then just stops every time. i just think that kde4 doesn't like my machine, as kubuntu 8.10 won't load either. strange happenings lately. definitely something i'm not used to.

lastly, if some of the top distros don't get there chit together, (you know who you are) i may just go with debian stable and call it a day. but that's for another discussion. peace.

---

### Post by AdamWill on 2008-10-12
It's likely just that the mirrors it's trying to use are overloaded. This always happens at release time, to most distros, it's kinda impossible to avoid. Give it a day or to to calm down and it'll be fine. As I recall you installed 2008 Spring a bit after release time, right? So you didn't see that problem.

Can't argue with the partitioning problem you had, though, that's an odd one :(. Actually I should've got you to take a readout of the troublesome layout with cfdisk before you changed it, but I forgot, so it'd be hard to diagnose the exact problem now.

Where does the One boot stop, exactly? There's a couple of known issues it could be.

---

### Post by Antman on 2008-10-12
> **wolfen69 said:**
> ok, i finally get to my desktop and do updates. it asks me if i want to update my sources. yes i do. it gives me failed to fetch yada yada. cant update. 
This happened to me too. I kept trying and after a while it went through. I guess the servers are busy because of the release.

---

### Post by n8ek on 2008-10-14
I've downloaded Mandriva around 6 times on 2 computer's either a torrent version or ftp on windows xp , vista and linux, burnt using nero and k3b (downloading torrent again)but the disks will not install/run, i get the Mandriva splash screen then the monitor goesblack and thats it?

Thanks

---

### Post by 67GTA on 2008-10-14
I tried the last KDE4 RC version and had to select "Text" mode to get the live CD to boot on my three machines. It would always hang before the desktop loaded if the "Text" option wasn't chosen. It installed fine in virtualbox, but I never tried to update it.

---

### Post by n8ek on 2008-10-14
might try the text mode install (never done it)Mandriva runs like a dream under virtualbox on my pc as well,

---

### Post by Vulpus on 2008-10-17
> **n8ek said:**
> i get the Mandriva splash screen then the monitor goesblack and thats it?

Sounds like it might be this:
[http://wiki.mandriva.com/en/2009.0_Errata#One_editions_fail_to_boot_to_a_graphical_desktop_.28xorg.conf_not_created.29](http://wiki.mandriva.com/en/2009.0_Errata#One_editions_fail_to_boot_to_a_graphical_desktop_.28xorg.conf_not_created.29)

---

### Post by wolfen69 on 2008-10-18
i solved my problem by just using 2008 spring (gnome). i have to say it runs like a dream. perhaps 2009.1 will work better for me. cheers.

---

