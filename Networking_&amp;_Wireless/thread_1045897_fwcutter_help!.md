---
title: "fwcutter help!"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by Foster88 on 2009-01-20
Hello,

I was trying to Install the b43fwcutter package, and there was an error while it was downloading. It said Http was waiting for confermation. Am I supposed to type something their or just wait longer to see if it fixes itself?

---

### Post by Pyro_Killer on 2009-01-21
Maybe the mirror has gone bad?
This is of course highly unusual, but likely in these hacked times, I changed all my reposetories to the neighbor country, and now all is allways working, what country are your mirrorrs set?

sudo gedit /etc/apt/sources.list

The norwegian mirror suck, but the swedish one is optimal, dunno why, just the way it is.

---

### Post by Foster88 on 2009-01-21
Hi again,

Thanks for your reply. Now that I know it could be my mirror, how do I find which one I'm using, and how do I change it? sorry I'm what you call a noob. haha!

Thanks for your help, highly appreciate it

---

### Post by jonobr on 2009-01-21
Hello

if you cat the /etc/apt/sources.list it will show you your current mirrors

heres the mirrors list

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

To change you would modify the sources.list file, but always always make sure you know what your doing, and of course, make a backup before changing 
cp /etc/apt/sources.list  /etc/apt/sources.list.bkup
If you think you made a booboo , you can swap back

---

