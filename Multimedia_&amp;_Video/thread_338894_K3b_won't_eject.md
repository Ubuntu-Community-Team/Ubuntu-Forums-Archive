---
title: "K3b won't eject"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by obsidion on 2007-01-15
OK, I know I have seen the solution somewhere but just cannot seem to find it.
Using k3b to copy a cd and it won't eject the cd to be copied after reading it in order to put in the cdr.

 A pointer at a solution would be much appreciated

---

### Post by gralbe on 2007-01-15
I think I recall two options (one I gave :) )

Someone just ran 'sudo k3b' and reported success.

I ran the k3b setup program (which requires your password and then, I presume, does a little chmod +s on some apps... didn't actually check).

Could you try my approach and report success or failure?

-g

---

### Post by obsidion on 2007-01-15
> **gralbe said:**
> I think I recall two options (one I gave :) )

Someone just ran 'sudo k3b' and reported success.

I ran the k3b setup program (which requires your password and then, I presume, does a little chmod +s on some apps... didn't actually check).

Could you try my approach and report success or failure?

-g

  The k3b setup just doesn't want to change anything. In the end I put a shortcut on my desktop.
with kdesu k3b. Not the ideal solution but it works, the trouble is that the disk access and the mounting etc default to root and there just doesn't seem anyway to get it to alter. I might have to enable the root password and see if I can fix it that way. I really don't want to do that as it has caused problems for me in the past namely admin tasks not knowing which password to use and just not running.

   It is the only hassle I have atm

---

### Post by gralbe on 2007-01-15
> **obsidion said:**
> The k3b setup just doesn't want to change anything. 

I just reran setup on mine and it doesn't want to change anything either so I'd guess that it thinks everything is fine (and I just confirmed that, on my system, k3b still ejects the disc as expected).

Have you run 'eject /dev/hdc' (or whatever your CD drive is) from the cli, just to verify that it works as your normal user?

---

### Post by obsidion on 2007-01-15
> **gralbe said:**
> I just reran setup on mine and it doesn't want to change anything either so I'd guess that it thinks everything is fine (and I just confirmed that, on my system, k3b still ejects the disc as expected).

Have you run 'eject /dev/hdc' (or whatever your CD drive is) from the cli, just to verify that it works as your normal user?

  That works fine. I think what is happening that when ik3b starts to copy the disk it grabs it as root then since it is fired up as normal user it can't eject the cd as it doesn't have the permissions.

---

### Post by gralbe on 2007-01-16
Well, FWIW here is some data from my install for comparisons sake:

(regular k3b options->programs display)

cdrdao:
/usr/bin/X11/cdrdao V1.2.1
overburn,multisession,disable-burnproof,suidroot,hacked-atapi,plain-atapi
-rws--x--x 1 root root 560584 2006-07-10 13:07 /usr/bin/X11/cdrdao

cdrecord:
/usr/bin/X11/cdrecord.mmap V2.1.1a03
gracetime, overburn, cdtext, clone, tao, cuefile, xamix, suidroot,plain-atapi,hacked-atapi, short-track-raw
-rws--x--x 1 root root 339788 2006-08-17 07:57 /usr/bin/X11/cdrecord.mmap

mkisofs:
/usr/bin/X11/mkisofs V 2.1.1a03-unofficial-iconv
udf, dvd-video,joliet-long, xa, sectype
-rwxr-xr-x 1 root root 472996 2006-08-17 07:57 /usr/bin/X11/mkisofs

readcd:
/usr/bin/X11/readcd V 2.1
clone, plain-atapi,hacked-atapi
-rwxr-xr-x 1 root root 156776 2006-08-17 07:57 /usr/bin/X11/readcd

It's weird that the same programs are also sitting in /usr/bin (not links) but k3b has chosen those in X11.

Anyway, maybe you can find a difference between mine and yours.

Also, besides my user, here are my groups:
adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin

---

### Post by obsidion on 2007-01-16
Can't see a difference, anyway found a work around so will probably stick with that, not the ideal solution of course but what the heck it works eh!
  Thanks for the input though, the hint about sudo sent me to the solution of using the kdesu k3b shortcut.

---

