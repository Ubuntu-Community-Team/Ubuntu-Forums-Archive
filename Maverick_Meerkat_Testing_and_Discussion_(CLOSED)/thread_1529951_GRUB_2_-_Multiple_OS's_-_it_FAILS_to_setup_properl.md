---
title: "GRUB 2 - Multiple OS's - it FAILS to setup properly"
date: 2010-07-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2010-07-12
[Can You Please Help to Sort this problem out - this link shows when GRUB2 is not  working]("http://sites.google.com/site/problems7730zg/home/grub-2-problem-of-other-operating-systems-wanting-to-overwrite-the-good-one/problems")

This happened after the latest Upgrade Today.

If  GRUB2 update worked my link above would not show any errors in it  especially knowing that I have 13 operating systems running perfectly  .....  before it.

Then after the upgrade it all changes the problem is one GRUB2 needs to be the CONTROL one .........

GRUB2 Mint to GRUB2 Maverick ....... and it all goes to rubbish ..........

[B]The things that are not working on my Setup now are the Graphics and the Theme and the Links.

[/B]

---

### Post by ranch hand on 2010-07-12
I do not, first, see how any of these other problems can be connected to grub itself.

I, for instance, would love to blame all my problems on plymouth.  The problem for both of these assumptions is that grub is a boot loader, plymouth a boot manager.  They really do not have a thing to do with anything after your boot.

I could be wrong about that of coarse.

When grub is updated and installs on the MBR you should get a box asking where to install it.  This does not, I admit, always happen.  If it does and you do not want that OS to be the root for your MBR grub, you need to just select no option.  You will get a warning that you may not be able to boot.

If you have grub from some other OS already installed on the MBR this is not a problem.

What we need is the results (the  whole thing) from the boot info script.  You will get a Results Text file on your desktop.

You can get it here;

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I have no idea how it works on non Debian based OS' but I know it works great on the Debian based ones.  Any will do, probably better from the problem one is you can boot to it but it really doesn't matter.

We will have to copy the bugger to gedit and study it anyway.  I know how long it will be.

---

### Post by 23dornot23d on 2010-07-12
Cheers Ranch Hand ,,,, as you say its massive ....

[Download Boot File]("http://sites.google.com/site/23dsources/allsorts/RESULTS.txt?attredirects=0&d=1")

Once I understood how GRUB2 took control of the MAIN drive ..... 

I tried to not let any other OS touch it ...... problem is Lucid Was done a long time back and has been upgraded
right through from 9.04 .... maybe even earlier ....

It still can take control of sda1 ..... my main hard drive GRUB2 bootloader.
USB 1 should be sdb
USB 2 should be sdc
__________________________________________________________

The older OS's are no problem as they do not use GRUB2 update.

___________________________________________________________

I have just noticed something on there .... its counting 4 drives .... I had a SDD
card in the front of this when I did the Upgrade .....

That may explain why its not seeing (sdc drive) as it thinks its (sdd drive)

---

### Post by ranch hand on 2010-07-12
There seem to be some problems with that but I think it is all there.

Just so we have an aid in navigating this bugger how about the results of;
```

sudo fdisk -l

```
That way we can have a separate screen to have that info on.

---

### Post by 23dornot23d on 2010-07-13
Sorry Ranch Hand here is the clean NEW Data * (Less confusing)


[B]This is the new Clean Boot Info File ..... 
[/B]
[New File]("http://sites.google.com/site/23dsources/allsorts/RESULTSnew.txt?attredirects=0&d=1")

```

keith@keith-laptop:~$ sudo fdisk -l
[sudo] password for keith: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50a5b170

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2   *        1306       15070   110562991    7  HPFS/NTFS
/dev/sda3           15854       16245     3145796    7  HPFS/NTFS
/dev/sda4           15071       30401   123146257+   5  Extended
/dev/sda5           15071       15471     3221001   83  Linux
/dev/sda6           16246       20690    35704431   83  Linux
/dev/sda7           20691       27291    53018412+  83  Linux
/dev/sda8           29365       29820     3662788+  82  Linux swap / Solaris
/dev/sda9           29821       30401     4666851   82  Linux swap / Solaris
/dev/sda10          27291       29272    15909888   83  Linux
/dev/sda11          29272       29364      743424   82  Linux swap / Solaris
/dev/sda12          15472       15523      417658+  82  Linux swap / Solaris
/dev/sda13          15524       15853     2650693+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a32b4b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       27084   217552198+   c  W95 FAT32 (LBA)
/dev/sdb2           27085       29545    19767982+  83  Linux
/dev/sdb3           29546       36882    58934390+   f  W95 Ext'd (LBA)
/dev/sdb4           36883       38913    16313976   83  Linux
/dev/sdb5           34963       36882    15422400   83  Linux
/dev/sdb6           29546       32050    20121349+  83  Linux
/dev/sdb7           34899       34962      514048+  82  Linux swap / Solaris
/dev/sdb8   *       32051       34774    21880498+  83  Linux
/dev/sdb9           34775       34898      995998+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x010a1416

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        8877    71304471    7  HPFS/NTFS
/dev/sdc2            8878       19469    85080240   83  Linux
/dev/sdc3           19470       22039    20643525   83  Linux
/dev/sdc4           22040       60801   311355734+   5  Extended
/dev/sdc5           22040       23833    14410273+  83  Linux
/dev/sdc6   *       38648       53154   116524850   83  Linux
/dev/sdc7           60640       60801     1301233+  82  Linux swap / Solaris
/dev/sdc8           23834       27685    30940914+  83  Linux
/dev/sdc9           53154       60639    60124160   83  Linux
/dev/sdc10          27686       38647    88051712   83  Linux

Partition table entries are not in disk order
keith@keith-laptop:~$ 


```
Just to check it was not the camera sd card causing the problems - I did a grub-update

and the problems on USB drive 2 - still exist ,,,, it will not find the OS's

---

### Post by oldfred on 2010-07-13
If you removed a drive that does cause problems. At the grub menu try editing the X drive number in the set root =(hdX,Y)

I installed from a USB to a USB and removed my install USB. The USB would not boot. The drive had changed from sdg to sdf and I now believe that the search stops looking after the first empty drive, so even though the UUID was correct search did not find it since I did not have sdd or sde. I was able to get it to boot only by editing the set root drive number to the correct number (which I was not sure so I tried several).

---

### Post by 23dornot23d on 2010-07-13
I did used to have to do that at one time to get the drive to boot up ..... and learned from it .... but to make things simple
I have just removed the sd cards and why they were in is another story - (uploading-screenshots-of-GRUB2-failing)
but they are out now and the update-grub made no difference.

_________________________________________________________________
 
This is as tidy a system as I can make it for this exercise - the main problem is why GRUB2 does not let me leave it as is 
Once it is set up properly ........... 

The problem lies in the fact that if you have more than one GRUB2 ....... One needs to be in Control ......
The others should not be able to overwrite the MENU ......which is what this one has done .....

I have been working fine for months and will still be if I install the MINT one ..... bit we will sort this first ...... before I put it
back to normal .....
_________________________________________________________________

I have it now with only the 3 drives which is the way I always do run it ........ 

and I have just done a update grub ..... with the 3 drives only ..... 

sda
sdb
sdc



I will try as you say though ...... and go through all the drives again ...... it may take me some time ..... have a coffee .....

sda2 ....................... Vista *not bothered if it works ,,,, takes too long to check out ,,,,

sda5 ...... Works ....... Mandriva
sda6 .......Works ...... Ubuntu 9.10
sda7 ....... Works ...... Ubuntu 8.10
sda10 ..... Works ...... Zorin 3

sdb2 ...... Works ..... Ubuntu 9.04 ....
sdb4 ...... Works ...... Maverick 10.10  ......This is the one the update-grub was done from
sdb5 ...... Fails .... know about this Mandriva never works unless on the first drive !!!
sdb6 ...... Works ... Knoppix 5.1

[B]I know from the past when this happened all my problems were on the last drive ..... 
I can pretty much guarantee the first two drives are ok .... but will check them.
[/B]

I managed to boot into sdc6 ....... that  seems odd ..... Mint 9 
                                 sdc5 ........ FAIL
sdc8 ........ FAIL
                                 sdc9 ........ FAIL
sdc10 ....... FAIL

OK so its all on the last drive ,,,,,,,,,,,,, so anybody any ideas why ?

And Why does it not pick up the Graphics ........... is Plymouth the problem ..... ?

I might be able to recover my boot options from sdc6 then ............ 
( So does anybody want to find a solution to this or do I put my system back to normal using MINT )

I can give the boot info from there see if there are any obvious differences ,

But if Plymouth was to blame ,,,,, does a different Plymouth run from MINT > ?

[B]GRUB2 is it to Blame ..... something is not working right on the last drive sdc
Plymouth is it to Blame for no Graphics ...... 

or (is it the way I have my Drives layed out ...... if so how does MINT sort it all out to work properly ?)


[/B]

---

### Post by ranch hand on 2010-07-13
I just got back from other chores and am headed to bed.

Just a couple of observations.

The main one is that you seem to think that having more than one grub is a problem.  In 9.10 testing I had 19 installs of Ubuntu on this drive, all with grub 2, another with grub leagacy.  The other installs changed but always included Mandriva with grub legacy.  This caused no problems at all.

I have 3 drives on this box.  One drive does not boot with the others.  It is my main drive and I do not want testing OS' anywhere near my stable main OS.  So I only have two that boot together and then only under certain conditions.

One internal has a number of OS' that I am interested in and let other people fool with.  One of them I use to boot with.  That has 2 custom menus so that I only have to mess with one if things change on the test drive (external usb enclosure).  One menu for the internal and one for the external.  They combine to make one screen menu with all 18 OS'.  If I do not want all that I can disable the one for the external drive.

I do not have any OS set up on the external to boot it and the internal.  That was set up in 10.04 testing though and worked very well.

So, I have never booted 3 drives, just 2.

I would like to know what this means;
> 
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

"msdos4"?  WTF?  I can some what deal with C drives and A drives but msdos drives I have a problem with.  I started on msdos and we did not have partitions as there was no HDD.  Just a couple of floppies.  What drive is that defining?  I surely hope it is not sda4.

I assume that sda is the drive that bios want to boot from and so you need grub installed on its MBR.

I would pick one and install it so you can boot with ease.  You said mints grub2 worked, I would use it for now.  We can bounce back to Mangy Moose after some study time.
I will have to do some studying on your setup tomorrow.

---

### Post by 23dornot23d on 2010-07-13
Cheers Ranch Hand 

I have no idea where the msdos is coming from .....  in the listing ......

I did post a second list with only the 3 main drives only on it ......

I have one Windows Vista on here that I do not use and that is NTFS

______________________________________________________________

I actually stick to using sda as my main boot drive ....
I also keep the two USB drives in the same order as on the second boot listing I posted

It took me some time to figure out how to get all these systems running together, 
I hate seeing errors on the screen - so I ensure that if I get one I sort it out.

Why this GRUB is giving 4 errors before the MENU pops up is strange as the other GRUB does not.

______________________________________________________________

I will do as you say and get this back to a fully working 13 OS system ......
its will take me at least 30 mins to do this has I have to do a clean installation
of MINT ....  I have just woke so will have some breakfast then do it ...

Ok thanks for looking at the boot listing ..... 

I have no idea why it keeps putting msdos ,,, that was one thing that struck me
as I cannot remember seeing it there last time.

We will see what I get with the next install of MINT 9 ....

[B]OK MINT is on and the MENU is ok again - video drivers picked up and I have a background pic for the MENU

[IMG]http://5270667693938030042-a-1802744773732722657-s-sites.googlegroups.com/site/23dsources/home/xorgconf/boot.jpg?attachauth=ANoY7coiBrL-q8LLYTsb3QoEV7gxwstKgZcrf03Q2GaFMm_VYwktv0MSmAVNc9kLbDHihW99U1jadaHuHSoTOnsjiIW6of-iNIlUejg3rnP3z1Gy6zm11-u6sw504yAjgZj1bQqnP5rIpUi6gxbzm6ZhLAdlgUECiFXsLzqNm1Wo8iMPBTmFqgsda8a-FSGMSpgOaqfOQy3s-RCR5_IRCEmeYCO4dOB0dw%3D%3D&attredirects=0[/IMG]

_________________________________________________

Now to see how many work ..... will go through these as I use them and post here ......

sda6 - Ubuntu 9.10 ..... Linux keith-laptop 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686 GNU/Linux
sda7 - Ubuntu 8.10 ..... Linux keith-laptop 2.6.27-17-generic #1 SMP Fri Mar 12 03:09:00 UTC 2010 i686 GNU/Linux
sda10 - Zorin 3 ..... 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux[/B]
[B]
sdb4 - Ubuntu 9.04 ..... 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux


I will start on sdc as this is the problem drive for 10.10
(I put MINT on it in place of Fedora 13 .......) 

sdc5 - this is the new version Mint 9 just installed  - tick
sdc8 - Mint Linux keith-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux - tick
sdc9 - Ultimate Edition 2.8 *test version - tick
sdc10 - Ultimate Edition 2.8 - tick

One thing I will try ....... I will see if Gnome 3 now works again ........

NOPE GNOME3 is another problem ..... MUTTER is not running at all .......

_________________________________________________________

So have done a aptitude safe upgrade - this minute - and MUTTER now works
*........GNOME3 - still does not though ....... *

[/B]

---

### Post by VMC on 2010-07-13
I was afraid to ask this question regarding the new grub2 reference to msdos nonsense. Apparently it got change in grub2 update somewhere along the line. [Ex. set root='(/dev/sda,msdos8)']. I just went along with it. I googled looking for something to explain this strange occurrence. I couldn't find any explanation.

As a side not, I also noticed you having 3 swap partitions, which is unneeded.

---

### Post by 23dornot23d on 2010-07-13
The swap spaces yep - needs sorting ...... cheers.

I wondered if anyone would mention them .... how I ended up with them is another story
basically comes from when I was learning to lay the LINUX drive partitions out ..... 

I always assigned 3 parts to Linux (/)(swap)(/home) ..... from my Mandrake 7 days - it sort of stuck with me ...... 
so every OS I would install had (/)(swap)(/home) as that was the only way I knew ,,, at that time .... 
(so thats where the swaps come from ..... I think I have deleted or merged a couple together already).

That was my first USB drive I bought and that has had many OS's on it .....bit of an excuse really ..... for a untidy drive ..... but that's the way it is ........
( I always keep the first partition as it is from the manufacturer - (NTFS or whats on to begin with) - this was from when I used Windows - 
(that could go now too I suppose) 
I was always scared of messing with the first part of USB drives as I have one - a 20 Gig Thompson Lyra refuses to communicate anymore across the USB )
 

I have changed though ........ we learn and I am still learning (and willing to learn) .....

My 2nd USB is layed out a little better ,,,,, I think ........ 1 swap ...... 1 home ...... and a few OS's

It causes me no problems having the swap spaces like that on the first USB - 
so I never got around to changing them 
( Now you have mentioned it - I will sort it out )

___________________________________________________

**OK I am now running in the version of Maverick 10.10 on sdb4 - (**this was upgraded from Lynx).
[B]
guess the next thing is the boot layout that was produced in MINT ......
(I will not alter the swap spaces just yet ..... I am keeping it easy as I can to work out why the other GRUB FAILS)


Ok the link to the latest file ......  [URL="http://sites.google.com/site/23dsources/allsorts/RESULTS.txt?attredirects=0&d=1"]BOOT LISTING

[/URL][/B][COLOR=Red]Maverick[/COLOR] Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.
[COLOR=SeaGreen]MINT[/COLOR] Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.[B]

So whats different .......

what is this for ?  [/B](,msdos4)

---

### Post by VMC on 2010-07-13
I'd be curious to know if someone that **doesn't **have a Windows partition, does the msdos reference in grub2 go away or never gets implemented?

---

### Post by cariboo on 2010-07-13
I don't have a Widows partition, the msdos references are still there.

---

### Post by 23dornot23d on 2010-07-13
_______________________________

The main problem is ......

THE MAVERICK GRUB2 - will not work with MULTIPLE OS's on 2 USB drives 
(These 2 USB's are plugged into this laptop all the time - and the boot order should never change)

_______________________________

But it was interesting to see the Photographic SD card took priority over My 500 Gig in the Boot sequence when left in. It actually became **sdc**

I really DO NOT WANT THAT TO HAPPEN ..... THE BIGGER DRIVES SHOULD TAKE PRIORITY - IMHO
secondary items - USB sticks and Photo SD cards

**The one exception is Booting **
( so UNLESS WE ASK THE BIOS TO BOOT FROM THESE they should be at the end of any list )

---

### Post by cariboo on 2010-07-13
Please quit making your posts so hard to read, colored text and trailing comma's and periods are not wanted or needed, they just make the post hard to read.

---

### Post by oldfred on 2010-07-13
I just converted one drive sdb to gpt and while it booted ok I could not chainload windows on sda or load any of the Ubuntu installs I have on sdc.
I filed a bug but it was already fixed with this having to be added for the grub in a gpt partition system to see msdos or MBR systems which just about all systems use now.
insmod part_msdos

Edit - VMC has link to bug 

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743)

---

### Post by VMC on 2010-07-13
> **oldfred said:**
> I just converted one drive sdb to gpt and while it booted ok I could not chainload windows on sda or load any of the Ubuntu installs I have on sdc.
I filed a bug but it was already fixed with this having to be added for the grub in a gpt partition system to see msdos or MBR systems which just about all systems use now.
insmod part_msdos

I'd like to read that bug fix. Can you supply a link? thanks.

Edit: Perhaps [this]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/604743") is it.

---

### Post by kansasnoob on 2010-07-13
> The problem lies in the fact that if you have more than one GRUB2 ....... One needs to be in Control ......
The others should not be able to overwrite the MENU ......which is what this one has done .....

I have been working fine for months and will still be if I install the MINT one ..... bit we will sort this first ...... before I put it
back to normal .....

You're not the first to notice that :)

Look at the conversation between myself and Seeker here:

[http://ubuntuforums.org/showthread.php?t=1516153](http://ubuntuforums.org/showthread.php?t=1516153)

At that time I was using my Karmic to boot with a custom menu and I was shocked that upgrading Maverick's grub2 "silently" reinstalled its grub2 to the mbr.

But it appears that's intentional. If dpkg was last told to install grub to a certain device it will now automatically do so on upgrade. I don't think that's very sane behavior but that seems to be where we're headed.

---

### Post by oldfred on 2010-07-13
I remember a while back where some one complained that the dpkg setting still uses drives (sda) for the setting on where to reinstall. If it is a USB or any drive that changes drive number it will reinstall to the wrong place. They wanted it changed to UUID but something about that being a huge change.

---

### Post by kansasnoob on 2010-07-14
> **oldfred said:**
> I remember a while back where some one complained that the dpkg setting still uses drives (sda) for the setting on where to reinstall. If it is a USB or any drive that changes drive number it will reinstall to the wrong place. They wanted it changed to UUID but something about that being a huge change.

I'm fairly certain that's true.

OTOH how was it handled with legacy grub?

The answer is, "it seldom was". Legacy grub was just well established after a decade or so, thus there were almost never package upgrades to grub.

There will undoubtedly be 'missteps' tweaking grub2 but I think we're going in the right direction.

---

### Post by ranch hand on 2010-07-14
I am sorry to say that  I have been busier than a one armed paper hanger until now.  Have not really had much of a look at things,

Why reinstall Mint?  Surely all you need to do is run "grub-install /dev/sda" to reexstablish it as the boot root.

If you can't boot it can be done from a Live CD of an OS using grub2.

The little I did look at gave me these issues;

What is on sda13?

You have 2 installs of 9.10, apparently upgrades that have both grub-legacy and grub2 components.
This is not good, it will cause problems.  Either finish the upgrade or revert to grub-legacy.

/dev/sda3 overlaps with /dev/sda4
That from the boot info script.  I am real good at doing this type of thing.  It is not a good thing.

The deal with looking to sda4 for grub is a mystery but I wonder if the crowded partitions play  apart in this.

You have extra swap partitions on there.  You could knock them off and move every thing to the right a little including the start of sda4.

Reading this thread makes me wonder if you have tried purging the offending grub-pc and grub-common, going in and removing any old files left behind and reinstalling the buggers?  Part of why I ask that is this sda4 business.  An extended partition is not the sort of place to look for things like that.

I have got to go get some sleep.  Busy, hot day again tomorrow.

---

### Post by 23dornot23d on 2010-07-14
Cheers Ranch Hand

The overlapping systems sda3 sda4 .....  
[COLOR=Red]( 1. This is Sorted now - and overlapping does not exist anymore )[/COLOR]

sda3 is Vista

sda4 is the Extended Partition

sda5 is Mandriva

I read about the [resize error in gparted ]("http://gparted-forum.surf4.info/viewtopic.php?id=13777")and wonder if that caused this.

**I have never manually alter my drive structure to cause a overlap.**
( So either this happened in gparted or one of the installs ... or Windows Vista did it .... after a restore )

I will look and see if this is the main problem.

I have started to sort this ..... the overlap is no longer there .... 
I ran Testdisk 6.11 (it analyses and finds the start and end points of partitions as well as other things)

But although it appeared to fix it I am running into another problem now
when running gparted (system goes beyond end of disk .... so am looking at this [thread for the solution]("http://ubuntuforums.org/showthread.php?t=1038943") )


First sector 0
Last sector     488392065
Total sectors  488392066
Warning Can't have a partition outside the disk !


**I will get to the bottom of this and sort it though .....** then move on to the next thing ....
[B]
swap space on sda [/B]will be sorted once I can get gparted running again 
[COLOR=Red]( 2. The 4 swap spaces sorted now .... I have reduced it to 2 swap spaces )[/COLOR]

**swap space on sdb** is sorted too (there is only going to be **one swap on each drive**) 
[COLOR=Red]( 3. The 2 swap spaces sorted here too .......there is one only here now)[/COLOR]
[B]
swap space on sdc[/B] is ok one only
_________________________________________________

**sda13 was a part of the Vista install **and I believe one of the installs took this as
swap space and set it as a linux partition ...... it did ..... and it was naughty to do this.

[COLOR=Red]( 4. this was a swap and is now merged with the two others that were there sda10 sda11 sda12 )[/COLOR]

(The Linux install would have asked me at the time of the install if I wanted to do this )
(but I never realised it was part of Windows and even if I did it would not have bothered me at the time). 

I may be wrong but (I usually try to avoid altering the end partition if I believed that the Windows sets up needed it). 

This obviously did happen though and what could I do to revert it after the incident ....
it sits there with the original information on it as far as I know it did not stop anything functioning.


But the reason for GRUB2 not pointing to partitions on sdc could this be part of the problem ?.


__________________________________________________________________

[COLOR=Red]( 5 .....[/COLOR] in progress ... )

The 9.10 ..... versions I will now go back and continue the upgrades and remove any other left over Grub versions ..... 
I possibly kept them at the time incase GRUB 2 ever failed in a big way - 

But it will be fine and it just needs some TLC to get it working spot on .

__________________________________________________________________

I will remove the extra swap partitions - as we know these should not be a problem.

But they do not look good ...... so will tidy up now 
( I was waiting till you checked the file and said it was ok to alter these - and will now alter them )

__________________________________________________________________

Ok I did not know the extended partition was not a good place for GRUB2.

Thanks ..... 

I will see what I can do to sort out these issues out and tidy 
[B]sda *([pretty certain that a resize of ext4 did this]("http://gparted-forum.surf4.info/viewtopic.php?id=13777"))
 [/B] 
I will minimise the extra swap space this is mainly on
[B]sdb *(this will not change the boot problems though)
[/B] 
After doing the above I will post a new BOOT REPORT.

**sdc** is good though ..... that's maybe why MINT has no problems at all ..... we will see what happens after doing the above.

______________________________________________________________
Just a quick re-cap.

(**sdb4** is where the new GRUB2 is set up from .... 
Why **sdc** which is the cleanest drive causes the problems for the new GRUB2 ....

 It sets only one of the ext4 partitions in it to boot up that being **sdc6** ([the rest fail.]("http://sites.google.com/site/problems7730zg/home/grub-2-problem-of-other-operating-systems-wanting-to-overwrite-the-good-one/problems"))

the ( **sda** and **sdb** ) drives - The new GRUB2 menu actually works and points correctly to **sda** and [B]sdb partitions 
[/B]when the new GRUB2 is created using grub-update on **sdb4** the problem)

_______________________________________________________________

Why reinstall Mint?  Surely all you need to do is run "grub-install /dev/sda" to reexstablish it as the boot root.

[B]Its the only method I knew and trusted to get my system back to full functionality.
[/B]( If Grub2 had let me run Linux Mint from sdc .... a grub-update would have done .... )
Maybe what I should do is install Mint on the sdb ..... that way it becomes simple ....
Good thinking

---

### Post by ranch hand on 2010-07-14
You can mess with grub from a live CD;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

I keep a chroot script somewhere on every OS to chroot into that OS.  That way I can copy/paste it to the Desktop of the Live Session if I need too (handy on these testing OS').

sda13 is listed as Linux with a code 83 which I think means it should be bootable.  That is why I wonder what is on it, in the list all it says is ext4, no boot files, no OS identification.

---

### Post by 23dornot23d on 2010-07-14
Ok cheers

[Chroot .]("http://en.wikipedia.org/wiki/Chroot").... How does the script work exactly ?

sda13 .... is a mystery to me as yet then .... 
I will get to it soon though.

I am doing a deep search on sda ..... just a recon at moment.

Hopefully once gparted works I can ensure I have a tidy drive and remove sda13 if needed.

---

### Post by ranch hand on 2010-07-14
I am on nothing but (except for 8.04) ext4.  No problems with gparted ever caused by gparted.  I do have a tendency to pack my partitions a little too tight.

I think this is a bigger problem when dealing with ntfs partitions but that is not a problem for me as I just delete anything that even smells of MS.

If you were to get rid of sda11 or 12 you could slide every thing up there, shrink sda4 a hair, and probably have that problem gone.  Probably leave a small unused spot on your drive.

You have Mint8 on sdb8.  Simple enough to install its grub anywhere you want including sdb or all drives.

---

### Post by 23dornot23d on 2010-07-14
If you were to get rid of sda11 or 12 you could slide every thing up  there, shrink sda4 a hair, and probably have that problem gone.   Probably leave a small unused spot on your drive.
**Yep once I manage to get gparted going this is what I wil do**

Gparted would not run because of the overlap on sda ..... so sorted it ..... and now

Gparted now gives this ..........
Warning Can't have a partition outside the disk !

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, [COLOR=Red]30401[/COLOR] cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x50a5b170

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         128     1028128+   b  W95 FAT32
/dev/sda2            1306       15070   110562984+   7  HPFS/NTFS
/dev/sda3           15071       15471     3221000   83  Linux
/dev/sda4           15472       [COLOR=Red]30402[/COLOR]   119933257+   f  W95 Ext'd (LBA)
/dev/sda5           15472       15523      417648   82  Linux swap / Solaris
/dev/sda6           15524       15853     2650692   83  Linux
/dev/sda7           15854       16245     3145792+   7  HPFS/NTFS
/dev/sda8           16246       20690    35704428   83  Linux
/dev/sda9           20691       27291    53018412   83  Linux
/dev/sda10          27291       29272    15909888   83  Linux
/dev/sda11          29272       29364      743416   82  Linux swap / Solaris
/dev/sda12          29365       29820     3662780   82  Linux swap / Solaris
/dev/sda13          29821       30401     4666840   82  Linux swap / Solaris



```This seems to look ok now ..... sda3 and sda4 no longer overlap but ( [COLOR=Red]30402[/COLOR] ) 

It was ok on the first listing I posted page 1 [post #5]("http://ubuntuforums.org/showpost.php?p=9582637&postcount=5") * 
( So Testdisk has just done this but it cured the overlap - W95 ext'd - why a change here )

**OK am just going to see what still runs**
* computer seems to be ok ..... so the next step .....

Get the rest of the information to solve where the end of drive sda is and to correct it.

**( I will not confuse things ..... will get back to this once its sorted as this is now a different issue )**
___________________________________________________________________

You have Mint8 on sdb8.  Simple enough to install its grub anywhere you want including sdb or all drives.     
**Ok will look into doing this once I clean my 'sda' up a little**

I can boot by swapping the BIOS and used to do this to use a Mandriva GRUB1 

That then chainloaded to whatever I wanted ..... which was great.

But one of my installs made Grub2 the main one.

_______________________________________________

Once we get the drive sorted out then Grub2 should function ok and run all the OS's on **sdc**

 .... that's saying ..... that when I tidy this up and re-run it that it will be ok ...... 
[B]I will then do a grub-update on sdb4
[/B] 
*  Everything should be alright ?

(I for one know the Graphics will not be .... but as you said that may be Plymouth .... a separate problem)

---

### Post by VMC on 2010-07-14
> **23dornot23d said:**
> Ok cheers

[Chroot .]("http://en.wikipedia.org/wiki/Chroot").... How does the script work exactly ?

sda13 .... is a mystery to me as yet then .... 
I will get to it soon though.

I am doing a deep search on sda ..... just a recon at moment.

Hopefully once gparted works I can ensure I have a tidy drive and remove sda13 if needed.

Regarding chroot and how to use it. I use the following two scripts :
```
#!/bin/bash
## copy 7 commands below then paste:
sudo mount /dev/sdaX /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt/ /bin/bash
=============
Remove CHROOT
=============
#!/bin/bash
## Ctrl+d to exit chroot,
## copy 6 commands below then paste.
sudo umount /mnt/etc/resolv.conf
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
```

Relpace the "X" above with the partition your chroot'ing to.

---

### Post by 23dornot23d on 2010-07-14
Cheers VMC ...... once I sort the end of my drive out ..... 

I will see if I can use the code you have posted ty ;)

______________________________________________

I am getting confused with sorting the end of my sda drive out ......

[Here is where I am]("http://sites.google.com/site/problems7730zg/sda-layout-after-testdisk---30402") ..... 

none of the figures seem to make sense to me YET

They will though ..... there is always a solution ..... and not everything is obvious at first sight.

OK SORTED .... [The Gparted view of sda Now]("http://8491362605497748020-a-1802744773732722657-s-sites.googlegroups.com/site/problems7730zg/sda-layout-after-testdisk---30402/gparted1.jpg?attachauth=ANoY7couU48nn9htqZvadMepyD3XoeF8G5JJs13hRnLAs0xaxk-DNaea7qHa8ao4WENgX_dse5MPIKsbi4EyLhYTRHtbWwbtxF6ITLvwdG8KQ_D4qve_KheMHDaoQJFsKUHL1rJF289htcwY2edZ_40-AYH_jz1YCM3txcmscyLW5QjN3sEuNGUMLvGGqmz0OjS1XyzMHe6yMb46XqCJNgt-I5-ggDPkE-LAWCBbEctrOZj4CCbQSSgyxZczw1tOZrY6zW-pqDKS&attredirects=0") ..... before I remove the swaps and tidy it up

OK TIDY .... [There are still 2 Swaps but this is better]("http://8491362605497748020-a-1802744773732722657-s-sites.googlegroups.com/site/problems7730zg/sda-layout-after-testdisk---30402/gparted2.jpg?attachauth=ANoY7crqXFY3olsDtOPqaATNngCAtgJa9t8F0T2f69QHHAA2WnmXGcTItQATFgJmyQZNbnmN6WLH069uAvd-cPezHdoJEOrrwwB3ri08AT33pgKc3FY8tqfFdC7w8kiGFx3kZgoWSdMn-W18Z1xR0xViXN1cLEsQ2jXBru7F_ghV8ot-SAAFIR7IpL5MKUbhhOebU3PmlV9Nd71bhz9-UzngJYROJEebW_i3Rs3DZD4Iar52749Dc7JfTQKiE9HVh64iDIynwHPZ&attredirects=0") ..... free space around the Main one too
no more overlapping of partitions .....

---

### Post by VMC on 2010-07-14
I just used it because I change Maverick from one partition to another. The easiest way to to boot with a livecd, then I open gedit and change sdaX to lets say sda7 and then copy and past into an opened terminal. 

then you can:

```
sudo grub-install /dev/sda
sudo update-grub
```

once done make sure you Ctrl+d then copy and paste the last parts of the script.

---

### Post by jerrylamos on 2010-07-14
Grub2 is screwed up as of Alpha2.  I've got an IDE drive that Ubuntu thinks is sda, and a SATA that is sdb.  Grub2 thinks sda is hd1 and sdb is hd0.

Hold the phone!  That's backwards!

Grub2 then booting looks for a specific UID on one drive that install put on the other.  Never occurs to Grub2 to look on the other drive for the UID.

fstab is also screwed up, claiming that the partition was installed on the other drive.  At least it runs.  Grub2 dies.

So I re-installed Alpha1 & did massive updates....

Yes I wrote a launchpad bug #602514.

Jerry

---

### Post by 23dornot23d on 2010-07-14
> 

Grub2 then booting looks for a specific UID on one drive that install  put on the other.  Never occurs to Grub2 to look on the other drive for  the UID.

This could very well be what happens here too ..... as I think the UID s are correct for mine too.

But it seems to be looking on the wrong disk for them ....... this is just a hunch when watching the drive lights flashing.

We will soon find out,  I have fixed the problems on the drive now .... just cleaning up the updates and upgrades for Ubuntu 9.10 ...... 
and removing any of the OLD legacy Grubs as I no longer use them.

_________________________________________________________

Once this is done I will do a fresh > [BOOT report]("http://sites.google.com/site/23dsources/allsorts/RESULTS.txt?attredirects=0&d=1")[]("http://sites.google.com/site/23dsources/allsorts/RESULTS.txt?attredirects=0&d=1") using the BOOT script.

Then the only thing left to do is a update-grub from sdb4 I think ......

__________________________________________________________

---

### Post by ranch hand on 2010-07-15
You could use a custom file too.  With symbolic menu entries you boot to the defined partition.

The entries I use are generally specific to Debian based OS'.   I love the buggers as you never need an update, they just boot to the newest kernel (Debian based) on that partition.

As an example of what they do, if you were to replace one of your 9.10 installs with the newest Zorin release the old menu entry, unedited, would boot you right up.

You define the drive, you define the partition.  This is why, for instance, I am unaware of any problems with grub in A2 (assuming  that jerrylamos is correct, no reason to doubt him).  on all my installs 30_os-prober is disabled.  10_linux is usually enabled but very seldom used on my test OS' and disabled on stable releases.  Who uses 20_memtest86 more than once a year?  You can enable it when you want it.

You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09)

On the OS that boots 2 drives I have 06 and 07_custom.  One for sda and one for sdb.  That way I can know exactly where I need to go if I want to change the menu for some reason.

The entries are not in partition order, they are in the order I want them.

I think custom menus are about the coolest thing because you can control what the name is, what order the stuff is in (like grub-legacy) and the entries are not dependent upon the kernel (unlike any grub version.

Plug this in your 40_custom file of what ever OS you boot from and plug in the drive and partition number for an OS on your  box do not change anything else, it will show up at the bottom of your menu;
```

echo "Adding Ignernt Inchworm on sda7" >&2 
cat << EOF
menuentry "Ignernt Inchworm on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
EOF

```
I have an OS (Lounge Lizard) on sda7.  I edited that for your box.  Try it.  Then just change the numbers.

Remember to run update-grub.  Remember that 40_custom is at the bottom of the menu (thus mine are renamed to a lower number).

I think you may like it.

---

### Post by 23dornot23d on 2010-07-15
Well it all seems to be ok now

The original GRUB2 remains after the update-grub

I tried this twice now and no problems

Thank you very much Ranch Hand, oldfred and VMC 
also everyone else that added to this thread ....... cheers.

I will take this as a learning experience ...... and maybe less likely to jump onto
one thing like GRUB2 ...... 

( Its not taken over yet - which is great - but it did this once before - then swapped on
an upgrade - but for now everything is running just as I like it - and no errors )

I guess the overlapping partition was the main problem then.

I am glad that this is sorted and have learned a lot about how the disk should be
set up and organised.

Thanks again ..... I will mark this as solved

---

### Post by ranch hand on 2010-07-15
Glad it is working.  Things can be a bugger.

When you get upgrades for grub-pc and grub-common it will usually install on the MBR as a normal part of setting up the new Grub.  If this is the grub you boot with and it did not do this you would not be able to boot as the files would not be the ones being looked for by the old version on the MBR.

You should, however, get a dialog box asking where to install grub.  If it is not the one you are using to boot with leave all options blank blank and hit OK.

This should bring up a warning that your system may not boot.  This you can ignore as you do not boot with that grub.  Tell it to proceed. 

If you do not get the chance to choose where it goes file a bug against grub;
```

ubuntu-bug grub

```
I think.  Could be grub-pc.

---

### Post by 23dornot23d on 2010-07-15
> When you get upgrades for grub-pc and grub-common it will usually  install on the MBR as a normal part of setting up the new Grub.  If this  is the grub you boot with and it did not do this you would not be able  to boot as the files would not be the ones being looked for by the old  version on the MBR.

Ok I guess that is what is changing THE GRUB MENU when I do the safe-upgrades so the **upgrades for grub-pc and grub-common**, will watch out for these next time ....  and see what happens.

If it does change back to the black and white boot menu and the 640 x 480 .....
After doing the Upgrades to grub-pc and grub-common ....... 
I will start another thread . I have a funny feeling that this may still still happen.

I think that .....
[B]I need to burn a clean install of the latest Maverick CD and Start afresh now.
and see if that picks everything up as it should also putting a nice bootloader up for me without messing about.

MINT does this - was one of my reasons for starting this thread - to solve it.

I believe if the boot screen looks good and goes in without any errors it will give NEW USERS more confidence - the first few screens you see need to look good and the menu system working correctly .......

First Impressions go a long way.

Thanks Again .... Ranch Hand 
[/B]

---

### Post by ranch hand on 2010-07-15
The background for your menu is black and text white by default in Ubuntu.

Ubuntu assumes that you use auto login for one thing (makes no sense to me) and they leave out the contents of the /usr/share/images/desktop-base file from Debian (good idea they are for Debian).

If you look at your /etc/grub.d/05_debian-theme file you will see that it is calling for a .png file from that desktop-base file.

Those images are generally 640x480 (72.00 pix/inche) in resolution.  If you have gimp it is pretty easy to get an image the right size.  You can also in the debian theme file change the font color.

If you check your Mint installs debian-theme file you will see where it is getting its image from.  There may be more in there that you could choose (Debian has several - all boring).

You can also install "grub-splashimages" from the Ubuntu repo.  It installs a new file /usr/share/images/grub, changes the folder that /etc/grub.d/05_debian-theme looks at for the image to that file and supplies several images (maybe Mint uses them?).  I do not like them all that well and never install them.

I have gimp and all my photos and the entire internet full of images.

I usually use the same image as my wallpaper.  It is different for each install so when an update does change the MBR  on me I know right off what OS I am booting from.

---

### Post by 23dornot23d on 2010-07-15
I did try working out how this was working once before ....

I just wanted to see where the pictures came from and how to change them

So I did this [GRUB Backgrounds etc Web Page]("http://sites.google.com/site/linuxbootubuntu/") ..... 

I refer back to it when I want to change things - 

Similar too [My Background images for each System]("http://sites.google.com/site/23dornot23d/") are different ,,,, 
this needs updating too though.

All good GRUB2 stuff will come from developing this now ..... 
I am sure it has a lot of scope - brave move to get rid of GRUB1
(but people still have options I think)

I want to be able to use GIF animations at start up too in GRUB2 obviously with a 
way of switching them off or just to one frame of them if some computers cannot handle it. 
(maybe just the border could be animated quicker loading - but it could be made to look good)
similar to the Start up of Ultimate Edition as it goes into the Login Screen.

---

### Post by ranch hand on 2010-07-15
There is a link in my sig for a thread of mine that has a bunch of links at the bottom of the first post.  The second one you probably know the first is the only documentation worth a fiddlers dam (I have never figured out what is wrong with the mother of a fiddler) when grub came in with 9.10A2.  Pretty great stuff.

There is also, near the bottom of the list, a link to a how to for reverting to grub-legacy.  There are a couple of pit falls you really want to avoid and that will take you through it.

Getting rid of grub legacy was a great move.  It puts Ubuntu and the Ubuntu devs into the present reality.  Part of that reality is that grub-legacy is not supported by the grub devs.

Grub-legacy was  a great bootloader, hated when introduced, that was very flexible.  The problem is that file system and drive technology is changing by the week (it seems like anyway) and grub-legacy was just not up to that.

Grub now has the ability to adapt quicker and easier because of the seemingly fragmented script structure.  That structure means that instead of being a huge repository of patches it can just have parts of it edited to meet the changes very fast.

Some things are not quite as easy to do, but most are easier.  It is, for instance, a little tougher to change which grub you are booting from using a live CD.  On the other hand you do not have to use a Live CD which you did with grub-legacy.

Changing the menu background is a piece of cake in Grub and a pain in the butt in grub-legacy.

Editing menu entries seems harder to folks because they will not use custom menus.  The custom menus are in there because most folks have a fairly static setup and this is easier.  It is easier for people with a lot of OS' that change a lot (you have 6 menu entries for one OS for instance).

All that other crap - 10_linux, 20_memtest86 and 0s-prober are ONLY needed on the first boot.  After that it is clutter.

If you are interested in more graphics in your bootloader you should check out Burg.  I know there is a thread somewhere on the forums about just that where the developer hangs out quite a bit.  Totally useless to me.  It is a really great piece of work.

There may be a thread on this testing forum.  A lot of folks here use it.  Has Icons and everything.

I be animated icons would work there, if that is what you meant.

---

### Post by jerrylamos on 2010-07-15
Ranch hand, thanks for the hints.  This is a dual hard drive setup with according to ubuntu an IDE as sda and a SATA as sdb.  Grub2 has them flipped as (hd1,0) and (hd0,0) respectively.  So I tried this based on your posting:

06_custom
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above
menuentry "Maverick Meerkat on sda8" {
    set root=(hd1,8)
        linux /vmlinuz root=/dev/sda8 ro quiet
        initrd /initrd.img
}
menuentry "lubuntu A2 on sda9" {
    set root=(hd1,9)
    linux /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=524388 rw quiet
    initrd /casper/initrd.lz
}
menuentry "slitaz (on /dev/sda7)" {
    set root=(hd1,7)
    linux /boot/vmlinuz-2.6.30.6-slitaz root=/dev/hdb7 home=/dev/hdb7 rw quiet
    initrd /boot/rootfs.gz 
}

On the same hard drive, lubuntu thinks (hd1,9) is sda9 while slitaz thinks (hd1,7) is sdb7....weird.  It works.

Also interesting the grub.cfg calls out on the linux line:

linux   /boot/vmlinuz-2.6.35-8-generic-pae root=UUID=0672c821-3a3b-4b70-aab9-8e967a9a0c60 ro   quiet

while your simpler line boots O.K.:
linux /vmlinuz root=/dev/sda8 ro quiet

Do note the lubuntu and slitaz are CD images mounted on 1 gb partitions for testing purposes.  Run fine but are not persistent as defined here.

Thanks, Jerry

---

### Post by ranch hand on 2010-07-16
You can add "splash" on the end of that instruction string.  I just copied on of my entries to the post.

Most of this drive has variations of 10.10 on it and that means plymouth.  If I have "splash" in the string I can see the splash.  All day.  Can't boot with the bugger enabled.

If you want to boot to recovery, by the way, you can edit that line to look like this by hitting e when the menu comes up;

linux /vmlinuz root=/dev/sda8 ro single

or make another entry with that line and label it recovery.  I did that on the wifes laptop.

Sorry about the "splash" thing I just do not think about it when I am on this drive.

---

### Post by cecilpierce on 2010-07-16
> **ranch hand said:**
> You can add "splash" on the end of that instruction string.  I just copied on of my entries to the post.

Most of this drive has variations of 10.10 on it and that means plymouth.  If I have "splash" in the string I can see the splash.  All day.  Can't boot with the bugger enabled.

If you want to boot to recovery, by the way, you can edit that line to look like this by hitting e when the menu comes up;

linux /vmlinuz root=/dev/sda8 ro single

or make another entry with that line and label it recovery.  I did that on the wifes laptop.

Sorry about the "splash" thing I just do not think about it when I am on this drive.

After every update mine locks up at the plymouth screen, really a pain, but I reboot three or four more times and it finaly goes past the plymouth crap.
Have you tried that? I wonder whats going on or if any one else gets this?
Cec

---

### Post by ranch hand on 2010-07-16
@cecilpierce
I expect the Plymouth problem to be solved.  They will get it to work or drop it.

It will never work as long as they keep messing about with the graphics.  This is not the problem.  The problem is plymouth.d supplied by libplymouth2.  The whole damned thing needs jack up and a new one backed under it.

I do not have time to boot multiple times to try this out.  Why?  Because I am tired of messing with it, Alt+Sysreq+b gets old really fast, booting takes over a minute when it works anyway.

Your experience with booting sever al times points not at a graphics problem but to a problem with plymouth .d having trouble with itself getting to the next step in the boot management process.  They keep patching it and it is going to collapse under the weight of those patches.   "Crappy from the Start" would be a good moto for Plymouth and any OS using it.

My main drive, I am sorry to say, is being shifted to Debian (Squeeze).

Ubuntu will stay on my test drive, where I spend most of my time, but my main drive is supposed to be reliable.  10.04 is barely bootable, 10.10 a little better.  This is not good enough for an OS you actually want to set up for long time use and security.

---

### Post by jerrylamos on 2010-07-16
> **ranch hand said:**
> You can add "splash" on the end of that instruction string.  I just copied on of my entries to the post.

Most of this drive has variations of 10.10 on it and that means plymouth.  If I have "splash" in the string I can see the splash.  All day.  Can't boot with the bugger enabled.

All "Splash" does is execute extra code during boot.  I don't need to waste that time so I don't use "Splash".  Testing I reboot a lot so I don't want to wait for something that doesn't add function - and occasionally fails with development code.

Jerry

---

### Post by ranch hand on 2010-07-16
Heck, I don't remember what I posted.

Here is what the first 3 of mine are.  The first is an upgrade 9.10>10.04>10.10.  It was upgraded for the 10.04 toolchain, thus the name (short for Lounge Lizard).
```

echo "Adding Lounge on sda7" >&2 
cat << EOF
menuentry "Lounge on sda7" {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet
        initrd /initrd.img
}
EOF

echo "Adding Mangey Moose on sda14" >&2 
cat << EOF
menuentry "Mangey Moose on sda14" {
    set root=(hd0,14)
        linux /vmlinuz root=/dev/sda14 ro quiet
        initrd /initrd.img
}
EOF

echo "Adding Gnome on sda16" >&2 
cat << EOF
menuentry "Adding Gnome on sda16" {
    set root=(hd0,16)
        linux /vmlinuz root=/dev/sda16 ro quiet
        initrd /initrd.img
}
EOF

```

---

### Post by 23dornot23d on 2010-07-16
I understand why it will not boot drive sdc now after a upgrade

the grub-common was changed ....... and reverted me back to a non functioning sdc ......

The reason is its switching the 2 drives and seems to be getting the id's mixed up .........

sdc works in blue in the link below ....... but not in red ....... I wonder why !!!!!!!!!!!!

[PROBLEM IN PROGRESS]("http://sites.google.com/site/problems7730zg/mint-9-sdc5")

---

### Post by ranch hand on 2010-07-16
sdc is an external is it not?   I have found that grub is more reliable, assuming the external is always in use, to have a grub from there on the MBR of sda.

The custom menu also works better the more drives you have because you are asking for specified drives and partitions ranter than uuids.  It seems to me that the uuid should be better but it does not seem that way.

The scripts to generate the boot/grub/grub.cfg file on sdb8 will be in /etc/grub.d and /etc/default/grub.  The MBR is just looking for the /boot/grub/grub.cfg file on sdb8.

That is not what is important though because any mistakes in the grub.cfg file are caused by some thing in the other 2 files.

One thing that I have found is that when you set up your drives it is important to have all of them active at the time.  This insures no conflicts in uuids for one thing.  It also, for reasons completely beyond me, seems to make it possibe for all the drives to "see" each other.

That is why I have taken to partitioning from the Live CD, at least for initial setup, instead of from an OS on some uneffected drive.  It just seems to work better in the end.

---

### Post by ranch hand on 2010-07-16
> **23dornot23d said:**
> I understand why it will not boot drive sdc now after a upgrade

the grub-common was changed ....... and reverted me back to a non functioning sdc ......

The reason is its switching the 2 drives and seems to be getting the id's mixed up .........

sdc works in blue in the link below ....... but not in red ....... I wonder why !!!!!!!!!!!!

[PROBLEM IN PROGRESS]("http://sites.google.com/site/problems7730zg/mint-9-sdc5")
As to your last point, this is why I am wondering why you have not booted to 10.10 and gone to terminal or synaptic and "apt-get purge" or synaptic "complete removal" grub-pc and grub-common, gone to nautilus and deleted any left over files (/boot/grub, contents of /etc/grub.d and /etc/default/grub) and then reinstalled grub-pc and grub-common.

I would apt-get install them so that you get good output if there is any mistake.

It just seems that it is not working correctly.  If reinstallation does not fix it file a bug and use a different grub to boot from.

This is a testing OS.  It is not supposed to work yet.  If bugs are not filed they will not be fixed.

---

### Post by 23dornot23d on 2010-07-16
> 

As to your last  point, this is why I am wondering why you have not booted to 10.10 and  gone to terminal or synaptic and "apt-get purge" or synaptic "complete  removal" grub-pc and grub-common, gone to nautilus and deleted any left  over files (/boot/grub, contents of /etc/grub.d and /etc/default/grub)  and then reinstalled grub-pc and grub-common.

I would apt-get install them so that you get good output if there is any  mistake.

It just seems that it is not working correctly.  If reinstallation does  not fix it file a bug and use a different grub to boot from.

This is a testing OS.  It is not supposed to work yet.  If bugs are not  filed they will not be fixed.           

I am going to find out more before I post a Bug report ,,,,, they need the right information
as you say I need to sort some more things out too ..... this is now in progress again.


**SWAPPING OF THE HD IDs SEEMs TO BE WHAT HAPPENS (0,0) (1,0)**
oldfred seemed to say try this with (x,y)  and Jerry has a similar problem.
Just wondering if anyone else has this or similar and have already sorted it with a custom menu.

If the safe-upgrade had not overwritten the good MENU we would have been ok,

I am getting there, but with so many operating systems 
( the automatic addition of all the old kernels to the MENU listing it makes it a chore ) .

Maybe there should be a default setting for this just to add the last 2 ...... 

I need a quick way to sort the old kernels last 2 will do me  - I think Tweak does this ,,,,,

Have to check again - everything has a place - its just remembering where it is .......

---

### Post by drs305 on 2010-07-16
> **23dornot23d said:**
> 
Maybe there should be a default setting for this just to add the last 2 ...... 

I need a quick way to sort the old kernels last 2 will do me  - I think Tweak does this ,,,,,


I wrote a G2 tweaks post and one of the options is limiting the number of displayed kernels to just one. You could modify it to show several if desired by adding a counter. It's pretty geeky stuff but it does work.
The link is the G2 Tweaks in my signature line.

The good news is that there is a Grub2 script modification which has been presented to the Grub developers by Colin Wilson to add the "howmany" feature to the /etc/default/grub script. The devs haven't approved the change yet, and it may not get into versions earlier than Maverick. We'll just have to wait ... and hope.

---

### Post by 23dornot23d on 2010-07-16
Cheers thats exactly what I need ..... 

I think that its a good idea being able to revert back to other kernels ..... but its tidy if we only display 
what we need to see in the menu at any one time ..... ok will check your signature links out.

I just have a few more things to do - 

I do like it when it stays as I set it up - but reducing the numbers would help me a lot

Thank you drs305.

---

### Post by drs305 on 2010-07-16
23dornot23d,

The example I have in the Title Tweaks thread limits the main kernels to only one. Give me a bit and I'll update it (improve it) so you can set the number you want displayed. (I'll use 2 in the example.)

[URL="http://ubuntuforums.org/showthread.php?t=1287602"] Grub 2 Title Tweaks Thread
[/URL]

---

### Post by drs305 on 2010-07-16
Section 2 of Title Tweaks has been modified so the user can specify how many Linux kernels on the / partition to display. 

This is an user modification and any official update to the /etc/grub.d/10_linux file will overwrite this change.

---

### Post by 23dornot23d on 2010-07-16
Cheers have just added it .... and will try it out Thank you

Thanks for that code its now implemented  ....... works great ..... on the OS you are in
plus I have the latest version of Ubuntu-Tweak for removing the old kernels ...

I will soon have my menu looking good - sdc seems to be the problem drive as sdb always picks up ok. 


Does anybody know if the boot loader on a USB has to be within a 124 Gig limit ....( this seems to be applying to sdc )

I just noticed a warning when installing SUSE 11.3 , saying it may not boot if the boot loader is not within the first 124 Gig 

I did this because I wanted to see if any of the other developers had altered the GRUB2 menu .... 
But SUSE 11.3 is using a older version GRUB1.5
  during install there was a warning 124 Gig I think .... this just flashed on and off again 
I have searched - but nothing tells me of a limit yet - maybe this was a older limit or if it still applies could also be
a part of the problem.

---

### Post by jerrylamos on 2010-07-17
> **23dornot23d said:**
> Cheers thats exactly what I need ..... 

I think that its a good idea being able to revert back to other kernels ..... but its tidy if we only display 
what we need to see in the menu at any one time 

To make sense out of this testing system with 13 bootable partitions and for the ubuntu's multiple kernels on each I have an 06_custom as described by Ranch Hand which shows on the screen first all 13 in logical order followed by the usual grub.cfg long winded random order multiple line UUID nonsense.

That way when an update hangs the latest kernel there's a previous kernel available somewhere down in the mess for investigating the bug.

Jerry

---

### Post by 23dornot23d on 2010-07-17
You have it 100% correct there Jerry .... thats really what I need the same as you have ......

A list at the front with the OS's all of them in disk order sda1 to sdc10

and then following that all the automatic stuff , jumbled up , I would prefer this in disk order too though.

---

### Post by ranch hand on 2010-07-17
You just build a 06_custom file, enable it, run update-grub.  Leave the other files enabled and there you have it.

---

### Post by 23dornot23d on 2010-07-17
Cheers Ranch Hand

Have just done my first entry and it works fine thank you for the help .... used your[ first link.]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Configuration%20File%20Commands.html#Custom_Boot_Entries")
and added the text below .....

Works great and appears where I want it at the beginning ...... excellent ...... :D  

I will add them to this now and put them in order.

```

#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
menuentry "BOOT up sdc5  Linux Mint 9   (/dev/sdc5) (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 9969bae7-8927-41ab-a19a-0c6c45293f8d
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=9969bae7-8927-41ab-a19a-0c6c45293f8d ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
EOF

```( At least now I can put this somewhere safe and use it again if things mess up for any reason.)

---

### Post by ranch hand on 2010-07-17
The only trouble with that entry is that you will have to manually edit the kernel version to keep it up to date.  That is why I like the symbolic entries.

With the symbolic entries, however, os-prober goes nuts and puts every OS on every partition in your generated menu from reading the custom files and getting it wrong.  That is why I disable the bugger.

If you want the os-prober generated menu entries your entries are the ones to use.

I would use that on one OS and my way on another.  That way you can use the shorter menu for every day use and then shift the MBR version over to yours if you run into trouble with an )S and need the older versions of kernel.

What I do if I need that is to disable the custom file and enable OS prober and run update grub and wade through all that crap to the OS in question or shift the MBR version to the problem OS and enable 10_linux which just reads that OS and gives the menu for it with no problem.

This new grub is different, needs some work still, but is just too flexible if you learn how to do it.  I think it is just a lot of FUN.

I also keep the links to all of drs305s grub2 threads handy.  Herman is really great too.

---

### Post by 23dornot23d on 2010-07-17
Ok the second two entries are the shorter versions ......sda7 works ,,,,, just checking sda10 now (yes fine)

Seems a good way .... and easy too ..... 
( Like the good old days - back in charge of my System again )

Not too keen on all the automatic names ,,,, it gets confusing.
(Similar to when the disk drives were re-listed in Nautilus)
 sda1 sda2 sda3 ..... Are good for me I know what they are.

(Listing them with this means nothing to me ..... how do I know its sdc5
**500 GB Hard Disk: 32 GB Filesystem )**
( Doing a properties or(CLI) df does not give me info to link the 2 together )
I end up going into the boot folder to find out what it is !!!

```

#! /bin/sh -e
echo "Adding custom boot entry(s)" >&2
 cat << EOF
menuentry " sdc5 >>> Linux Mint 9 (/dev/sdc5) (on /dev/sdc5)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 9969bae7-8927-41ab-a19a-0c6c45293f8d
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=9969bae7-8927-41ab-a19a-0c6c45293f8d ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry " sda7 >>> Ubuntu 8.10 " {
    set root=(hd0,7)
        linux /vmlinuz root=/dev/sda7 ro quiet splash
        initrd /initrd.img
}
menuentry " sda10 >>> Ubuntu - Ultimate Edition on the MAIN DRIVE " {
    set root=(hd0,10)
        linux /vmlinuz root=/dev/sda10 ro quiet splash
        initrd /initrd.img
}
menuentry " sdc10 >>> Ubuntu Ultimate Edition 2.8 (on /dev/sdc10)" {
    insmod ext2
    set root='(hd2,10)'
    search --no-floppy --fs-uuid --set e008f348-b4b9-48dd-9c72-709364d3c1ba
    linux /boot/vmlinuz-2.6.35-5-generic root=UUID=e008f348-b4b9-48dd-9c72-709364d3c1ba ro quiet splash
    initrd /boot/initrd.img-2.6.35-5-generic
}
EOF

```Ok now I have this here I can always come back to it ... too ....
The boot system did worry me but - now I have this to fall back on it saves me 40 mins
reloading another system up ..... to get my menu back.

---

