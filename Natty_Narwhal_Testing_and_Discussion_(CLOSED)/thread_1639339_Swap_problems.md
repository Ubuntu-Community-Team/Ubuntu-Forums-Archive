---
title: "Swap problems"
date: 2010-12-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-12-06
Over last two weeks or so since I installed Natty, I have has a problem with the swap partition not mounting after hibernating, or a reboot. I normally use a shared swap between Maverick and Natty. The swap partition isn't a problem when running Maverick.

I have tried recreating the swap partition on the command line and using gparted, but no go. I used gparted to resize the /home partition and added a swap partition on my Natty install, and I still have the same problem.

Has anyone else run into this?

---

### Post by ronacc on 2010-12-06
I have a shared swap also but I never paid any attention to whether or not it actually mounted until you mentioned it , its there , at least this boot . I'll keep checking now that you called attention to it .

---

### Post by Quackers on 2010-12-06
I have a shared swap partition. It's shared between the Natty install that was upgraded from Maverick and the current Alpha 1. It seems to be mounting ok here.

---

### Post by ratcheer on 2010-12-06
I too have not noticed any problems with swap, but I will keep an eye on it and let you know if I do.

Tim

---

### Post by cariboo on 2010-12-06
This is only on my netbook, the other 4 systems I have Natty installed on aren't a problem. It's also the only system I hibernate.

---

### Post by MacUntu on 2010-12-07
A random shot: now that you've recreated your swap partition, did you check that the UUID in /etc/initramfs-tools/conf.d/resume matches the UUID of your swap partition? If not, change and update the initramfs (`sudo update-initramfs -c -k all` is how I do it to be on the safe side).

---

### Post by VinDSL on 2010-12-07
Along the same lines...

The only time I've had problems with swap space is when the UUID of the swap partition didn't match up with the entry in fstab.

When the UUIDs didn't match, I could swapon manually, during the session, but it would be swapoff after a reboot, et cetera.

---

### Post by MacUntu on 2010-12-07
> **VinDSL said:**
> with the entry in fstab

Man, how could I forget to mention the obvious other place. ](*,) :D

---

### Post by coffeecat on 2010-12-07
On a fresh install of yesterday, I'm not seeing this. Swap is mounted just fine. This is on a machine with a swap shared with other versions of Ubuntu and other distros. I'll check my laptop later - similar multiboot with shared swap.

> **MacUntu said:**
> A random shot: now that you've recreated your swap partition, did you check that the UUID in /etc/initramfs-tools/conf.d/resume matches the UUID of your swap partition?

Good point. Just for the record, with this installation the installer threatened to reformat the pre-existing swap partition - as it has done since for as long as I can remember - but the swap UUID is unchanged, so it obviously didn't.

---

### Post by MacUntu on 2010-12-07
> **coffeecat said:**
> but the swap UUID is unchanged, so it obviously didn't.

You can make mke2fs use a given UUID with the -U switch, so it might as well could have been formatted preserving its UUID.

---

### Post by coffeecat on 2010-12-07
> **MacUntu said:**
> You can make mke2fs use a given UUID with the -U switch, so it might as well could have been formatted preserving its UUID.

Yes, that may well explain it. Which would mean that the Ubuntu devs are more foresighted than those of certain other distros I could mention (*cough* openSUSE *cough*). Somewhere around Hardy/Intrepid days, installing another distro in your multiboot could lead to your swap UUID changing with loss of the usplash when booting Ubuntu. Easily fixed of course, but a cause of many threads on this forum.

But this all begs the question: why reformat a perfectly good swap partition? Seems pointless to me.

By the way, can you create swap with mke2fs? I thought it would be mkswap. I know all the mk* commands are a family with some being frontends for others, but I couldn't see whether there was a valid argument for swap for the -t option for mke2fs. The manual pages are somewhat - er - baroque.

Apologies, cariboo907, if this is going a bit OT.

---

### Post by ronacc on 2010-12-07
I don't recall the installer ever defaulting to format an existing swap , if if finds one it just uses it unless you specifically tell it otherwise .

---

### Post by MacUntu on 2010-12-07
> **coffeecat said:**
> I thought it would be mkswap.

You got me there! Anyways, the -U switch is available for mkswap too:

[http://manpages.ubuntu.com/manpages/maverick/en/man8/mkswap.8.html](http://manpages.ubuntu.com/manpages/maverick/en/man8/mkswap.8.html)

---

### Post by coffeecat on 2010-12-07
> **ronacc said:**
> I don't recall the installer ever defaulting to format an existing swap

If you choose manual/advanced it does indeed pick up the swap partition automatically, but it always says it is going to format it somewhere in the following screens. Although, tbh, I've never seen this happening in the progress feedback.** So whether it merely threatens to and then chickens out, or does so using a -U switch as MacUntu suggests, I don't know.

**Edit**

** I just have. Doing an (unsuccessful) install with manual/advanced from a Natty daily live I briefly saw a message about the swap partition being reformatted. So MacUntu's theory must be correct.

**/Edit**

---

### Post by ronacc on 2010-12-07
I'll have to pay more attention next install , I always use manual/advanced and I see on the summary page that it has picked up the existing swap partition but I don't remember it saying that it was going to format it , tbh I don't pay that much attention to the swap parition since I never allow my boxes to actually use it .

---

### Post by VMC on 2010-12-07
I've been using the same swap since Jaunty, and have never needed to touch swap. 
The UUID for swap hasn't changed and I have formatted the partition I use for Natty each and every day, as I have for Lucid and Maverick.

---

### Post by ronacc on 2010-12-07
I think my swap dates back to jaunty when I put that test box into service , never had a reason to change it .

---

### Post by cariboo on 2010-12-07
I tried MacUntu's initramfs suggestion, the swap survived a reboot, but not a hibernate,. trying to turn swap on after hibernate, I get a message saying:

```
swapon: cannot find the device for UUID=08ea8abf2-7c65-40a0-a007-0045622dco4
```

I've tried mounting the swap partiton using both UUID and device, and it doesn't make a difference.

The command to format a swap partition is:

```
sudo mkswap /dev/sdaX
``` 

When the command completes, it prints out the UUID of the swap partition.

I'll keep looking to see if the problem can be solved, I really don't want to create a bug, if I'm the only person affected by this problem

---

### Post by MacUntu on 2010-12-07
> **cariboo907 said:**
> trying to turn swap on after hibernate, I get a message saying:

```
swapon: cannot find the device for UUID=08ea8abf2-7c65-40a0-a007-0045622dco4
```

What's in your /etc/fstab?

---

### Post by VinDSL on 2010-12-07
> **MacUntu said:**
> What's in your /etc/fstab?Heh!  :)

---

### Post by cariboo on 2010-12-07
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=0539ff32-679f-453c-8ce8-9c67c244e2c2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=e7cd0050-78cb-4c39-9898-ce0badbc24cd /home           ext4    defaults        0       2
# swap was on /dev/sdb2 during installation
UUID=a3631d00-45e7-4b44-8b31-a8b51b56f1cf none            swap    sw              0       0

```

I reformatted the swap since my last post, so the UUID is different, 

there is something weird going on, when typing :

```
sudo swapon -a
```

I get :

```
swapon: cannot find device for UUID=27e5dc88-512e-44c4-aee8-4e7a814c7e00
```

Which doesn't show up when I type:

```
sudo blkid 
```

---

### Post by VMC on 2010-12-07
Your right something weird going on. Since last post I tried to hibernate natty, and it just shutdown. Never again did I see the hibernate again, so I then close suspend. After it came back up swap was totally screwed up. Opening gparted showed swap partition  in an error state. I tried to use tune2fs -U to get my original uuid number back, all to no avail .I eventually just used the supplied uuid once I re-created the swap and changed fstab in all the right places. Also reflected it at "/etc/initramfs-tools/conf.d/resume".

---

### Post by cariboo on 2010-12-07
This install started out as Maverick UNE and was upgraded to Natty, I'm just about ready to do a fresh Natty install to see if I can replicate the problem.

---

### Post by VinDSL on 2010-12-07
> **cariboo907 said:**
> This install started out as Maverick UNE and was upgraded to Natty[...]You might try  using PySDM, if you haven't done so already, and see if it gives any clues...  ;)

---

### Post by dino99 on 2010-12-08
Pysdm does not work at all under Ubuntu 10.04 LTS, and 10.10 (some scores may appear missing, and the disk structure is not similar to that described by GParted on a system configured for dual-boot Linux / Windows)

Limitation

Pysdm can not handle the devices identified by a UUID, as this is handled by default in Ubuntu since version 7.04. If you want to use pysdm, you need to create a new file management mount points that do not contain the old values associated with partitions.

---

### Post by VinDSL on 2010-12-08
> **dino99 said:**
> Pysdm does not work at all under Ubuntu 10.04 LTS, and 10.10 (some scores may appear missing, and the disk structure is not similar to that described by GParted on a system configured for dual-boot Linux / Windows)

Limitation

Pysdm can not handle the devices identified by a UUID, as this is handled by default in Ubuntu since version 7.04. If you want to use pysdm, you need to create a new file management mount points that do not contain the old values associated with partitions.Good to know... but wait!

Why does it work for me?!?!?  LoL!  :D


(Click image for full-size-view)
[INDENT][[IMG]http://vindsl.com/images/pysdm-10.10(550x440).png[/IMG]]("http://vindsl.com/images/pysdm-10.10.png")[/INDENT]


Can't say that I've ever had a problem with PySDM...

---

### Post by VinDSL on 2010-12-08
> **dino99 said:**
> Pysdm does not work at all under Ubuntu 10.04 LTS, and 10.10 (some scores may appear missing, and the disk structure is not similar to that described by GParted **[COLOR="Red"]on a system configured for dual-boot Linux / Windows[/COLOR]**)[...]Sorry, I missed that, on the first reading.

Is *cariboo907*'s computer infected with Windows???

---

### Post by cariboo on 2010-12-08
> **VinDSL said:**
> Sorry, I missed that, on the first reading.

Is *cariboo907*'s computer infected with Windows???

Windows was only on the system long enough to run the system restore backup utility. :) Since then it's been a pure Ubuntu system. At the moment it dual boots Maverick and Natty.

I did a fresh install last night, because of the weird problems I've been having I created a swap partition for this install, now the system is using both swap partitions, the one from the Maverick install and the new one.

This morning after coming out of hibernate the maverick swap partition is missing, and after a second hibernate, the natty swap partition is missing.

---

### Post by cariboo on 2010-12-08
I'm seem to be making some progress on my journey to diagnose the problem. I installed the hibernate package, and now I can hibernate without the swap partition being destroyed. Now though, there is a black rectangle in the upper left corner of the screen, about the size of an open terminal, when coming out of hibernation, restarting makes it go away, but that defeats the purpose of hibernation.

---

### Post by samfreed on 2010-12-18
I am having similar problems, a simple 10.10 system on a laptop. Occasionally my sway UUID changes, and running firefox-minefield which is a memory hog, I get slowdown to freeze.

---

### Post by cariboo on 2010-12-18
There has been a fix committed, see bug# [lpbug]683605[/lpbug]. I'm not sure when we'll see the fix, but it should be released before the end of the testing cycle.

---

