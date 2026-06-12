---
title: "New User Question!"
date: 2009-07-12
forum: Multimedia Software
---

### Post by Grimmjow-Akutabi on 2009-07-12
Hey there guys,

I'm not really sure about the best place to post this so i'm hoping im roughly in the right direction.

Basically, i'm wanting to Dual-boot Ubuntu on my desktop with Windows (Probably 7 as i'm currently running XP and will be upgrading soon). I'm gonna be using it as a general browser, and use to watch and listen to my media.

I've tried running off of a disc, and I must say Ubuntu looks beautiful, however i've not been able to get any sound as of yet. Is this because of the disc-boot? Is there any way to check if my speakers are working?

Also, my main question regarding all this is, if I made a 10gb partition, can I still play my music/video off of my Windows partion/other internal hard drive.

Thanks for all the help!

Grimmjow-Akutabi

---

### Post by igorzwx on 2009-07-12
If it would be Ubuntu 7.10 or 7.04,
you would get what you want.
Too late my friend.
But if you want to learn something
you may try this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

What you need to do is to hack Linux kernel. Just a little.

read this too:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

---

### Post by Grimmjow-Akutabi on 2009-07-12
> **igorzwx said:**
> If it would be Ubuntu 7.10 or 7.04,
you would get what you want.
Too late my friend.
But if you want to learn something
you may try this:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

What you need to do is to hack Linux kernel. Just a little.

read this too:
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

I've not installed it yet.

I'm confused to what you mean. What will be the problem using Ubuntu 9.04?

---

### Post by igorzwx on 2009-07-12
I am afraid it is not now a "new user" friendly.
I have Ubuntu since 2006.
The problems began when I changed from Ubuntu 6.10
to Ubuntu 9.04. It took some months to fix the problems.

In short, if you have a powerful box with quadro core inside
and it is certified for Ubuntu 9.04, you may not have problems at all.

But you can try.
The Ubuntu howtos are easy to follow.
Just copy and paste to terminal some commands.
In general, you can rely on official documentation.
If you do not understand the command, try to google it,
or ask somebody to explain.

If you have both Windows and Ubuntu,
you can use Windows and learn Ubuntu.

---

### Post by Grimmjow-Akutabi on 2009-07-12
> **igorzwx said:**
> I am afraid it is not now a "new user" friendly.
I have Ubuntu since 2006.
The problems began when I changed from Ubuntu 6.10
to Ubuntu 9.04. It took some months to fix the problems.

In short, if you have a powerful box with quadro core inside
and it is certified for Ubuntu 9.04, you may not have problems at all.


Mhm.

Well I built the PC myself using about 600 pounds worth of parts back in October. I'm using a quadcore processor (Q6600) so power shouldnt be a problem. However, I obvioulsy don't know if it's certified for Ubuntu 9.04

Does that help?

---

### Post by igorzwx on 2009-07-12
It is likely to work, I presume.

In any case, read this:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://wiki.archlinux.org/index.php/OSS](http://wiki.archlinux.org/index.php/OSS)

---

### Post by Grimmjow-Akutabi on 2009-07-12
I'll read those now :)

Out of interest, im about to install Ubuntu 9.04 tommoro, if I create a 10gb partition first, name it "LINUX" (or similar), and then tell Ubuntu to install there, will it just take to it nicely? Will I still be dual booting fine?

(This is my first time ever trying to dual boot sorry! I'm new to this!)

---

### Post by igorzwx on 2009-07-12
Just for booting 10gb is enough.
But 20GB is more comfortable.

Hint. 
Make defragmentation of your Windows partitions
Boot LiveCD. 
Check internet connection.
Run partition editor (gparted) System->Administration->Partition Editor
Create free space (not occupied by any partition) 10GB, for example
Reboot
Select install to HardDisk
Then select install to the largest continuos free space (it means without partitions)
It will make then everything automatically.
Install GRUB, of course.

Read something additional.
Ubuntu Linux for Dummies.chm (the best for you, with pictures)

---

### Post by Ekeluo on 2009-07-12
For partitioning, it might be good to consider doing it with a windows program (partition magic, etc). After you have defragged several times. Also, since you plan to upgrade to windows 7, it will overwrite your grub entry when you do so and you'll  need to recreate your grub entry after the upgrade is done.

---

### Post by Grimmjow-Akutabi on 2009-07-13
> **Ekeluo said:**
> For partitioning, it might be good to consider doing it with a windows program (partition magic, etc). After you have defragged several times. Also, since you plan to upgrade to windows 7, it will overwrite your grub entry when you do so and you'll  need to recreate your grub entry after the upgrade is done.

It's a clean 1tb harddrive so no need to defrag :)

I was hoping to just create a new partition there and be done with it...

---

### Post by Grimmjow-Akutabi on 2009-07-13
> **igorzwx said:**
> Just for booting 10gb is enough.
But 20GB is more comfortable.

Hint. 
Make defragmentation of your Windows partitions
Boot LiveCD. 
Check internet connection.
Run partition editor (gparted) System->Administration->Partition Editor
Create free space (not occupied by any partition) 10GB, for example
Reboot
Select install to HardDisk
Then select install to the largest continuos free space (it means without partitions)
It will make then everything automatically.
Install GRUB, of course.

Read something additional.
Ubuntu Linux for Dummies.chm (the best for you, with pictures)

I'm on XP Pro so you know, and I couldn't find Partition Editor in system. I'll try what I mentioned about, at worst i'll just have to reformat the 1tb hard drive to get all the space back since I don't have PartitionMagic or anything like that. (I just go through Disk Management).

---

### Post by Grimmjow-Akutabi on 2009-07-13
Okay i've just tried to do what I mentioned above and have had no results. I'll explain more technically what I wanna do here.

I have 2 internal hard drives. A 500gb and a 1tb. Windows XP is installed on a 130gb Partition on the 500gb harddrive, and the remaining space is storing my music files, data, etc.

The 1tb hard drive is completely empty and due to a format is ALL unallocated space. I want to install Ubuntu on THIS hard drive.


Will I still be able to dual boot Ubuntu and windows due to them being on different hard drives?

When I format my XP partition at a later date to install Windows 7, should there be a problem since Ubuntu was installed "first"?


Sorry for all these noobish questions, i'm just seriously confused here :(

---

### Post by martinbaselier on 2009-07-13
I don't really understand the replies here. If you install ubuntu, it will automatically ask you how you want it installed. The standard option is to create it's own partition (shrink your original ones, create a new partition and install into that one). 

You can also choose there to partition your HDD.(with gparted) If you do so, it would be wisest do it on a partioned HDD to prevent eventual dataloss. Normally it shouldn't be a problem though. 

It's easier to install linux on a machine with windows installed, than to install windows on a machine where any other operating system is installed (including newer windows versions). It can be done, though no easily, you would have to research this at the time you're planning to install. 

Regarding your sound, it normally works out of the box. Have you checked your volumesettings? There should be a speaker icon visible. Otherwise open a terminal and type alsamixer. 

If it's not a volumesetting, then it's a driver issue. You would have to check into that. Do you have more than one audiocard in it? Maybe one from the motherboard and a seperate one?

About the windowspartitions. There will be icons on your desktop for each one of them (just like on the lifecd). You can doubleclick and play all the media.

---

### Post by Grimmjow-Akutabi on 2009-07-13
> **martinbaselier said:**
> I don't really understand the replies here. If you install ubuntu, it will automatically ask you how you want it installed. The standard option is to create it's own partition (shrink your original ones, create a new partition and install into that one). 

You can also choose there to partition your HDD.(with gparted) If you do so, it would be wisest do it on a partioned HDD to prevent eventual dataloss. Normally it shouldn't be a problem though. 

It's easier to install linux on a machine with windows installed, than to install windows on a machine where any other operating system is installed (including newer windows versions). It can be done, though no easily, you would have to research this at the time you're planning to install. 

Regarding your sound, it normally works out of the box. Have you checked your volumesettings? There should be a speaker icon visible. Otherwise open a terminal and type alsamixer. 

If it's not a volumesetting, then it's a driver issue. You would have to check into that. Do you have more than one audiocard in it? Maybe one from the motherboard and a seperate one?

About the windowspartitions. There will be icons on your desktop for each one of them (just like on the lifecd). You can doubleclick and play all the media.

Thanks :)

I've spoke to a friend who's used Ubuntu in the past, and i'm doing things a much simpler way now.

I'm backing up all my data onto my 1tb hard drive, and then creating a new partition on the hard drive with Windows using the Ubuntu partion-making-thing.

As for my sound queery, i've not been able to test it yet, so was wondering whether there was a way to find out whether it works.

See, i've had a problem getting online via the Disc Boot, hence me installing to see if I can:

[http://ubuntuforums.org/showthread.php?p=7605237#post7605237](http://ubuntuforums.org/showthread.php?p=7605237#post7605237)

Thanks again! :)

---

### Post by martinbaselier on 2009-07-13
Regarding your sound problem: (assuming you checked the volumsettings; best to use alsamixer, cause it will you all settings)
in a terminal, type (or paste->ctrl+shift+v) the following line:
lspci | grep Audio
It will show you your soundcard
On my pc it shows:
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
Then to get more verbose information use:
lspci -s 00:1b.0 -vv
You would of course need to change 00:1b.0 to the number of your card.
Then to check if there are drivers installed. 
It will also show you if you have a kernel module (this is the linux equivalent for a driver) in use. 

If not, you would need to google for kernel modules and your specific sound card.

---

### Post by nancy0903 on 2009-07-13
i don't know too.

---

