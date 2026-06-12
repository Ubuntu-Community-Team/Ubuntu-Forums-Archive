---
title: "Copied dvd = no medium found"
date: 2006-10-10
forum: Multimedia &amp; Video
---

### Post by gargoyle on 2006-10-10
I am attempting to play a copied dvd.
I have VLC installed and it will play commerial dvd's ok.
However if I try and play a copied version, nothing happens.
I have check my file browser and it will not recognize the dvd.

I tried mounting the dvd with the following.
**sudo mount /media/cdrom0/ -o unhide**
Gives error messege **No medium found**

Any idea as to what the problem is here??

---

### Post by Kateikyoushi on 2006-10-10
Are you sure the disc is burned properly ?

---

### Post by gargoyle on 2006-10-10
The disk plays ok on winxp using PowerDVD.
So I have to assume it is burn ok.

Question was I using the proper mount instruction for the dvd?

---

### Post by kuja on 2006-10-10
Some DVD drives have trouble reading DVDs that were burnt. In some cases this means the media is of lower quality. another possibility is that you burned the disk at too high a speed. I recommend if you want the disk to be able to be played back to use high quality DVD+/-R disks, to use DAO write mode, and to burn the disk at a really slow speed.

---

### Post by gargoyle on 2006-10-10
No the quality of the dvd is not in question because the computer was a dual boot, the dvd played with winxp PowerDVD in the same unit.

Therefore it can not be a question of quality of the dvd, it has to be something in Ubuntu that is stop the dvd from playing and being recognized.

Any other ideas?

---

### Post by Kateikyoushi on 2006-10-11
If you use gnome try to disk mounter.
Right click on a panel >> add to panel >> disk mounter.
This would automount your dvd drive.

---

### Post by gargoyle on 2006-10-11
To Kateikyoushi 
Sorry but it looks like Disk mounter is for mounting Floppy disk and not DVD's.

It seems no matter what I try burnt dvd's are just not recognized.

---

### Post by Kateikyoushi on 2006-10-11
On both of my machines it mounts partitions and internal, even external firewire optical drives automatically.

---

### Post by gargoyle on 2006-10-11
To Kateikyoushi;
If I moved the mouse over the icon it said
 **Floppy drive (Not mounted) **
So assumed that is what it was later on I checked it with a cdrom and it showed another icon which showed the cdrom was mounted.
Sorry about that.

Ok so far I have
Music commerial cd will mount and play
Cd-rw with data recognized and listed in the file browser(Natilus)
Movie Commerial dvd will mount and play
dvd-rw with data recognized and listed in the file browser(Natilus)
**Burnt dvd movie still not recognized.**

This is a bummer because I wanted to get away from WinXp and switch over to Ubuntu but if one of the thing I like doing best is not available, this will put a real damper on the tranision.

I sure hope I can find a solution to this problem otherwise I do not know if I would want to continue using Ubuntu.
I really do not want a dual boot system just so I can watch dvd's.

Thanks for the reples from everyone.

---

### Post by nevle on 2006-10-12
I have the same problem, burnt dvds just are not recognised at all, however at least one commercial dvd will also not play. These dvds all play on dvd players or windows computers.Any suggestions?

---

### Post by gargoyle on 2006-10-12
Hi nevle,
I seems like I am not along with this problem.
It also seem like no one has an answer to this problem.

One the problems here is the number of people using Ubuntu is still pretty small in comparison to other operating systems so there is not a lot of people to pull information from.

I am posting this problem in other forum in hopes of getting and answer somewhere. I hope there is one I would hate to have to go back to WinXp but if I can not find answer the it is back to WinXp and go bye to Ubuntu.

Will go luck hope an answer shows up, if it does I will post it here.

---

### Post by nevle on 2006-10-12
dvds burnt using Magix with lite-on burner with imitation dvd-r xp sp1.When i put it in dvd player it spins and the light goes on but doesn't see the disc.

---

### Post by gargoyle on 2006-10-12
It seem like the problem has to do with the fact the dvds are burnt using the UDF coding.

There are few threads going on about this problem.
If you search for UDF you will find other people with the same problem and no real answer.

I wish I could give you more guidance but like you I have no idea as what do do next.

I even tried install a package called udftool. But I can not see any difference, and I can not seem to find any instructions as to how it works.

---

### Post by gargoyle on 2006-10-13
It seems I have found my answer possibly to my problem.
It turns out to be the disks them self.

I know people have said to use quality disk in the past. So this is part of the problem here.

I basically use 2 different types of disks so far.
**Playo**
----------------------------------------------------------------------------
Unique Disc Identifier : [DVD+R:AML-002-000]
----------------------------------------------------------------------------
Disc & Book Type :       [DVD+R] - [DVD+R]
Manufacturer Name :      [Anwell Precision Technology]
Manufacturer ID :        [AML]
Media Type ID :          [002]
Product Revision :       [Not Specified]
Blank Disc Capacity :    [2,295,104 Sectors = 4.70 GB (4.38 GiB)]
Recording Speeds :       [1x-2.4x , 4x , 6x-8x]
----------------------------------------------------------------------------
[ DVD Identifier V4.2.0 - [http://DVD.Identifier.CDfreaks.com](http://DVD.Identifier.CDfreaks.com) ]
----------------------------------------------------------------------------

**Nexxtech**

----------------------------------------------------------------------------
Unique Disc Identifier : [DVD-R:UME01]
----------------------------------------------------------------------------
Disc & Book Type :       [DVD-R] - [DVD-R]
Manufacturer Name :      [Ume Disc Manufacturing Ltd.]
Manufacturer ID :        [UME01]
Blank Disc Capacity :    [2,298,496 Sectors = 4.71 GB (4.38 GiB)]
----------------------------------------------------------------------------
[ DVD Identifier V4.2.0 - [http://DVD.Identifier.CDfreaks.com](http://DVD.Identifier.CDfreaks.com) ]
----------------------------------------------------------------------------

**It turns out that every disk made by Playo does not work in Ubuntu but works in WinXp. **  These disk are advertised (Staples) as 8x burn rate but only will burn at 4x. Yes they are you cheap media, at $5.00 for 50. One other point here is that 2 different machines were use to test out the disks, this in itself could be a factor in the problem.

**Now the disks labeled Nexxtech play in both Ubuntu and WinXP.** Again this was on 2 different machines. These disk were also cheap media at $8.00 for 50.

One point for both media is both are 8x but I alway burnt at 4x never at the advertised rate of 8x.

So maybe some of the problems in fact are do to the media, maybe you might want to check the quality of the media.

I found that [Video Help website]("http://www.videohelp.com") has a data base of various disk you can search through if you want to know how good a particular disk is.

So is this the final answer to the question about the dvds, I really can not say for sure but this is what I discovered about my problem.

I would like to thank all of you that replied to my post for you help.

---

