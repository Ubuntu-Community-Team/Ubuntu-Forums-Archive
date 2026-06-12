---
title: "5/6/2008 updates damaged system"
date: 2008-05-06
forum: Mythbuntu
---

### Post by uncle hammy on 2008-05-06
I ran a sudo apt-get update this morning and 4 updates were installed.  2 of them were to do with "jockey", and the other 2 I don't recall.  Anyways, they are brand new updates, because I had run update last night as well, and there was nothing.

Since the updates, I am having a very strange issue.  I can't reboot my machine.  When I don't it cycles off, but when it comes back up, it loads to the mythbuntu splash screen, the progress bar goes about 1/10th of the way, then that's it, it just sits there.

If I hard power it off, and power it back on, it comes up properly.    However, this is now the only way I can "reboot".

Does anyone have any ideas how I can reverse this problem?

Thanks,
Scott

---

### Post by superm1 on 2008-05-06
Scott,

Please boot into recovery mode to look at /var/log/dpkg.log and see what the updates were.

---

### Post by uncle hammy on 2008-05-06
Here's the entire log from this morning's update.  The packages were jockey-gtk, jockey-common, sudo, kdelibs-data...

```

2008-05-06 08:09:36 startup archives unpack
2008-05-06 08:09:41 upgrade sudo 1.6.9p10-1ubuntu3 1.6.9p10-1ubuntu3.1
2008-05-06 08:09:41 status half-configured sudo 1.6.9p10-1ubuntu3
2008-05-06 08:09:41 status unpacked sudo 1.6.9p10-1ubuntu3
2008-05-06 08:09:41 status half-installed sudo 1.6.9p10-1ubuntu3
2008-05-06 08:09:41 status half-installed sudo 1.6.9p10-1ubuntu3
2008-05-06 08:09:41 status unpacked sudo 1.6.9p10-1ubuntu3.1
2008-05-06 08:09:42 status unpacked sudo 1.6.9p10-1ubuntu3.1
2008-05-06 08:09:42 upgrade jockey-gtk 0.3.3-0ubuntu7 0.3.3-0ubuntu8
2008-05-06 08:09:42 status half-configured jockey-gtk 0.3.3-0ubuntu7
2008-05-06 08:09:42 status unpacked jockey-gtk 0.3.3-0ubuntu7
2008-05-06 08:09:42 status half-installed jockey-gtk 0.3.3-0ubuntu7
2008-05-06 08:09:42 status half-installed jockey-gtk 0.3.3-0ubuntu7
2008-05-06 08:09:42 status unpacked jockey-gtk 0.3.3-0ubuntu8
2008-05-06 08:09:42 status unpacked jockey-gtk 0.3.3-0ubuntu8
2008-05-06 08:09:42 upgrade jockey-common 0.3.3-0ubuntu7 0.3.3-0ubuntu8
2008-05-06 08:09:42 status half-configured jockey-common 0.3.3-0ubuntu7
2008-05-06 08:09:42 status unpacked jockey-common 0.3.3-0ubuntu7
2008-05-06 08:09:42 status half-installed jockey-common 0.3.3-0ubuntu7
2008-05-06 08:09:42 status half-installed jockey-common 0.3.3-0ubuntu7
2008-05-06 08:09:42 status unpacked jockey-common 0.3.3-0ubuntu8
2008-05-06 08:09:42 status unpacked jockey-common 0.3.3-0ubuntu8
2008-05-06 08:09:42 upgrade kdelibs-data 4:3.5.9-0ubuntu7 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:42 status half-configured kdelibs-data 4:3.5.9-0ubuntu7
2008-05-06 08:09:42 status unpacked kdelibs-data 4:3.5.9-0ubuntu7
2008-05-06 08:09:42 status half-installed kdelibs-data 4:3.5.9-0ubuntu7
2008-05-06 08:09:45 status half-installed kdelibs-data 4:3.5.9-0ubuntu7
2008-05-06 08:09:45 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:46 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:46 startup packages configure
2008-05-06 08:09:46 configure sudo 1.6.9p10-1ubuntu3.1 1.6.9p10-1ubuntu3.1
2008-05-06 08:09:46 status unpacked sudo 1.6.9p10-1ubuntu3.1
2008-05-06 08:09:46 status unpacked sudo 1.6.9p10-1ubuntu3.1
2008-05-06 08:09:46 status half-configured sudo 1.6.9p10-1ubuntu3.1
2008-05-06 08:09:46 status installed sudo 1.6.9p10-1ubuntu3.1
2008-05-06 08:09:46 configure jockey-common 0.3.3-0ubuntu8 0.3.3-0ubuntu8
2008-05-06 08:09:46 status unpacked jockey-common 0.3.3-0ubuntu8
2008-05-06 08:09:46 status half-configured jockey-common 0.3.3-0ubuntu8
2008-05-06 08:09:47 status installed jockey-common 0.3.3-0ubuntu8
2008-05-06 08:09:47 configure jockey-gtk 0.3.3-0ubuntu8 0.3.3-0ubuntu8
2008-05-06 08:09:47 status unpacked jockey-gtk 0.3.3-0ubuntu8
2008-05-06 08:09:47 status unpacked jockey-gtk 0.3.3-0ubuntu8
2008-05-06 08:09:47 status half-configured jockey-gtk 0.3.3-0ubuntu8
2008-05-06 08:09:47 status installed jockey-gtk 0.3.3-0ubuntu8
2008-05-06 08:09:47 configure kdelibs-data 4:3.5.9-0ubuntu7.1 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status unpacked kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status half-configured kdelibs-data 4:3.5.9-0ubuntu7.1
2008-05-06 08:09:47 status installed kdelibs-data 4:3.5.9-0ubuntu7.1

```

Does this help?

---

### Post by uncle hammy on 2008-05-07
I am starting to wonder if I don't have a bad hard drive, that has coincidentally gotten very bad and this update pushed it over the edge.  Let me outline what's happened...

1.  Original installaion (about 5 days ago), I kept getting an I/O error at 22%, and after making the 4th CD image, I finally got it to install.  I chalked it up to bad cds.

2.  Although it has run stable since I got it installed, I had a couple occasions where during a reboot, the screen came up with a lot of debug info, all culminating with a "kernel panic something".

3.  Since this update, I consistently get a lock up during reboots (at about 1/10th progress on the myth splash screen), and usually the only way I have to actually get the system going is to completely power down, and power back up.

4.  To me, this is the kicker.  I can't even boot up with the cd into "Install Mythbuntu" or "Live Environment" anymore.  I get to the splash screen, the progress bar goes back and forth, I finally get some disk activity and then I get to about 1/10th progress, and I freeze...every time.  I tried several times last night, and never did get into the live environment.

The only thing making me question my hard drive conclusion is this post [http://ubuntuforums.org/showthread.php?t=772485](http://ubuntuforums.org/showthread.php?t=772485) and this post [http://ubuntuforums.org/showthread.php?t=783119](http://ubuntuforums.org/showthread.php?t=783119).  Especially the last post, because this machine is an Athalon 64x2, NVidia 7600 GS (using NVidia drivers), AND it a cool and quiet setup.

---

### Post by uncle hammy on 2008-05-07
I may retracting my previous post.  The motherboard in this machine is the Asus M2A-VM, which apparently has some memory and issues with linux kernel hanging at startup, all of which are apparently fixed with a BIOS update.  I am going to try it.

---

### Post by uncle hammy on 2008-05-07
In the interests of putting a nail in this one.  I went out today, got an RMA to return the piece of crap ASUS board, and then hit the local ma & pa shop and picked up a Gigabyte GA-MA69VM-S2.  Now, the Gigabyte is no top of th elin eboard either, but after exchanging the boards, I reinstalled Mythbuntu, and have not had even a slight issue.

I think it's safe to say, that the board was my problem.

---

