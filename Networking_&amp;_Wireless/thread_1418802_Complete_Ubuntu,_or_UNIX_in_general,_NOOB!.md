---
title: "Complete Ubuntu, or UNIX in general, NOOB!"
date: 2010-03-01
forum: Networking &amp; Wireless
---

### Post by Marvio on 2010-03-01
I can see you guys rolling your eyes from here!! :)

Fortunately I'm not a noob to networking, actually I've always been a windows guy, and have my MCSE; I know, I know... But hey! I'm trying!! :)

Got a "simple" question...

I want to use windows apps in Ubuntu, hopefuly, if this works, I'll start advising my customers to go UBUNTU!!

I work mainly with dentists, and dental apps are amongst the worst coded pieces of crap out there. Most absolutely need a UNC style mapped drive letter to work; So, in windows I'd have P:\\server\share.  

I've been looking for a couple of hours now and I can't seem to find a way to make Ubuntu behave the same way, or at least behave the same way when I launch the app, I'm using wine.

Anyway I can actually mount a share to a drive letter in Ubuntu? I realize it's Unix, it works completely different, but I really want to make this work!!

---

### Post by essox on 2010-03-01
Hi and welcome to the unix world!

Have you tried running winecfg to configure your drives? 
You will need to have access to the UNC path from Ubuntu (e.g. have it mounted somewhere) in order to access it from wine. Afterwards you'd just need to configure the mount point as a drive in winecfg.

---

### Post by Marvio on 2010-03-01
> **essox said:**
> Hi and welcome to the unix world!
 
Have you tried running winecfg to configure your drives? 
You will need to have access to the UNC path from Ubuntu (e.g. have it mounted somewhere) in order to access it from wine. Afterwards you'd just need to configure the mount point as a drive in winecfg.
 
Ha! No kidding! I was looking up and down to make it work in Ubuntu itself and completely forgot to check out Wine :)
 
Also, while we're in the topic...
 
How do I make the windows share mounts to be persistent? So every time I boot Ubuntu it's already mounted and authorized by the server?
 
PS> I'm loving UBUNTU!!

---

### Post by Iowan on 2010-03-01
A couple of links:
 [http://ubuntuforums.org/showthread.php?t=1186877]("http://ubuntuforums.org/showthread.php?t=1186877")
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

