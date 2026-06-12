---
title: "todays build"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rbrick49 on 2011-04-05
what a god dam mess I had a corupt upgrade this morning it shot my last few days upgrade to the wall I just downloaded todays build the 4/4/2011 now I get no grub disc where is this distro going.I had an old kubuntu 9.10 it loaded no problems everything was ok I tried todays disc no go now I am angry

---

### Post by bluenova on 2011-04-05
lol, calm down. It's a beta, expect breakages.

---

### Post by rbrick49 on 2011-04-05
this is more than a breakage my friend I cant even recover from recovery option because nothing exists its gone I cant believe that I cant even get to a boot screen

---

### Post by TBABill on 2011-04-05
I had this exact same issue with Ubuntu and Xubuntu. It's the 64 bit iso that is a failure I think. I downloaded over and over, burned multiple disks, both CD and DVD, but I ended up at a grub rescue prompt every time. Downloaded the 32 bit...worked like a charm. But that's not the point. A beta should still install regardless of whether the software is finished or not. If you can't install it you can't test it. ISO testing should have caught these failures.

I share your frustration. I gave up. Now running LMDE 64 bit again and my cursing has stopped ;)

---

### Post by rbrick49 on 2011-04-05
> **TBABill said:**
> I had this exact same issue with Ubuntu and Xubuntu. It's the 64 bit iso that is a failure I think. I downloaded over and over, burned multiple disks, both CD and DVD, but I ended up at a grub rescue prompt every time. Downloaded the 32 bit...worked like a charm. But that's not the point. A beta should still install regardless of whether the software is finished or not. If you can't install it you can't test it. ISO testing should have caught these failures.

I share your frustration. I gave up. Now running LMDE 64 bit again and my cursing has stopped ;)
thanks mate I HAVING BEEN USING LINUX SYSTEMS SINCE 1995 I started with red hat then mandrake then ubuntu now I just dont now I just read another thread it seems to be an amd system issue I am 62 years old with no proper education I left school at 14 to work now I am just to tired to be bothered anymore I guess I will have to find something that just works for me no testing maybe I will give lmde a try is it ok
regards Ron
and many thanks to cariboo,lucazade,coffeecat and all the others that have helped me

---

### Post by lucazade on 2011-04-05
> **rbrick49 said:**
> thanks mate I HAVING BEEN USING LINUX SYSTEMS SINCE 1995 I started with red hat then mandrake then ubuntu now I just dont now I just read another thread it seems to be an amd system issue I am 62 years old with no proper education I left school at 14 to work now I am just to tired to be bothered anymore I guess I will have to find something that just works for me no testing maybe I will give lmde a try is it ok
regards Ron
and many thanks to cariboo,lucazade,coffeecat and all the others that have helped me

:)

---

### Post by Blasphemist on 2011-04-05
I'm not having the problems you guys describe and I just installed sunday from that daily build. I did a reinstall to clean up after lots of dinking and to go from 32 bit to 64 bit. I have a Toshiba L505 laptop and an Acer external monitor.

It sounds like some basic bases should be recovered. No offense. What all are you doing and documenting prior to your installs? What steps and options did you take in doing the install? I wrote down my installation choices as I made them just in case I needed to describe them later and rethink things myself. Do you know exactly what your hardware details are?

As is nearly always the case, the product is likely not at fault. Not every condition is tested before you get your hands on it but it doesn't get to your hands without many others using it successfully.

Breath deeply and let's rethink this.

---

### Post by TBABill on 2011-04-05
Yes, well aware of my hardware and not anywhere near my first rodeo. The breakdown is not due to hardware. All I run on this and the other machine are 64 bit distros unless I use PCLinuxOS because it only comes in 32 bit. I've installed somewhere between 250-500 distros and the Ubuntu installer is as easy as they come to use. 

The problem is the install routine. When it gets to the point where it should be installing grub (after formatting partitions, installing, etc.) it crashes, but still gives you a reboot prompt as if it finished correctly when in actuality grub never installed at all. And the installer also creates a new swap partition after every attempt...even when I identified the root, home and swap partitions.

Not a good experience. /dev/sda6 is what I always assign to root, /dev/sda8 is always /home and /dev/sda7 is always swap. Never changes....till I tried to test Natty beta.

I'll pass. Natty is a pain and it has nothing to do with bugs. Functionally it's just more time consuming to use than standard Gnome. Couldn't test Xubuntu because it crashed too (but ran great in Live mode).

I'll just watch the forums after final releases and see if they've worked this bug out of the install routine. Definitely not hardware and not a user error.

---

### Post by MKdx on 2011-04-05
rbrick49, 
your system is 64 bit like TBABill?

---

### Post by cariboo on 2011-04-05
I've had the same thing happen on a 32-bit system, it's fairly easy to fix, just boot from the Live CD, chroot the partition you installed on and run:

```
grub-install
```

and then

```
update-grub
```

I know this doesn't solve the problem, but at least you can get your system up and running. If it was me, I'd start worrying if this still happens after beta 2 is released.

---

### Post by iClouseau88 on 2011-04-05
> **cariboo907 said:**
> I've had the same thing happen on a 32-bit system, it's fairly easy to fix, just boot from the Live CD, chroot the partition you installed on and run:

```
grub-install
```

and then

```
update-grub
```

I know this doesn't solve the problem, but at least you can get your system up and running. If it was me, I'd start worrying if this still happens after beta 2 is released.
How do I "chroot the partition..."?

Thanks!

---

### Post by iClouseau88 on 2011-04-05
> **cariboo907 said:**
> I've had the same thing happen on a 32-bit system, it's fairly easy to fix, just boot from the Live CD, chroot the partition you installed on and run:

```
grub-install
```

and then

```
update-grub
```

I know this doesn't solve the problem, but at least you can get your system up and running. If it was me, I'd start worrying if this still happens after beta 2 is released.
How do I "chroot the partition..."?

Thanks!

---

### Post by ELD on 2011-04-05
> **rbrick49 said:**
> thanks mate I HAVING BEEN USING LINUX SYSTEMS SINCE 1995 I started with red hat then mandrake then ubuntu now I just dont now I just read another thread it seems to be an amd system issue I am 62 years old with no proper education I left school at 14 to work now I am just to tired to be bothered anymore I guess I will have to find something that just works for me no testing maybe I will give lmde a try is it ok
regards Ron
and many thanks to cariboo,lucazade,coffeecat and all the others that have helped me
 
You are kidding right?
 
For one thing Natty is not a stable release, the amount of people that complain because x doesn't work right on a daily build and say they will jump to Microsoft or another distro is shocking.
 
Are you using the Beta or a daily build? As a daily build not not be fully tested as the name suggest it's just a daily build of the packages.
 
As for the beta if your using that - the name Beta should tell you it will break, so expect it.
 
If you want something that "just works" as you say...then go to Maverick or submit bug reports on what you find with Natty and don't expect the world of a development release.
 
(I hope that doesn't come off to harsh - but the point is it's in development, try to keep a more open mind!)
 
This is coming from someone who can't even use Unity at the moment because of the panel superposition bug

---

### Post by cariboo on 2011-04-05
> **iClouseau88 said:**
> How do I "chroot the partition..."?

Thanks!

Becuase you are running a testing version, we assume you know how to do things like that. To chroot your install boot from the Live CD and open a terminal and enter the following commands:

[LIST=1]
[*]sudo mount /dev/sdxX
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Where /dev/sdxX = the partition you installed Ubuntu on. Once at the root prompt enter the following commands:

```
grub-install
```

and then when it's finished:

```
update-grub
```

once the second command is finished, press Ctrl-d twice and reboot.

---

### Post by rbrick49 on 2011-04-05
> **MKdx said:**
> rbrick49, 
your system is 64 bit like TBABill? yes asus motherboard amd 5000+ dual core processor

---

### Post by rbrick49 on 2011-04-06
> **ELD said:**
> You are kidding right?
 
For one thing Natty is not a stable release, the amount of people that complain because x doesn't work right on a daily build and say they will jump to Microsoft or another distro is shocking.
 
Are you using the Beta or a daily build? As a daily build not not be fully tested as the name suggest it's just a daily build of the packages.
 
As for the beta if your using that - the name Beta should tell you it will break, so expect it.
 
If you want something that "just works" as you say...then go to Maverick or submit bug reports on what you find with Natty and don't expect the world of a development release.
 
(I hope that doesn't come off to harsh - but the point is it's in development, try to keep a more open mind!)
 
This is coming from someone who can't even use Unity at the moment because of the panel superposition bug

i am not worried about unity I know it is broke its the fact I wasted another disc by downloading something that wont install a boot loader and no one can answer why beta,daily build or whatever the boot loader should work.as of today I have got over my pissed off mood from last night everything loaded ok this morning after I did a dd-if on the hard drive but the boot loader wouldnt install so I did the manual code that cariboo gave its ok now thank you

---

