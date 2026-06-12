---
title: "Natty Kubuntu hijacking the MBR"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-03-13
I have a multiboot with Maverick, Lucid, Natty Ubuntu, Natty Kubuntu and a few other OSs on different partitions on my main machine. At the moment I am using Maverick's grub as my master bootloader with everything set up the way I want it in 40_custom.

When there's a grub update in Ubuntu Natty, things are left as they are. When there's a grub update in Kubuntu Natty, the update process hijacks my mbr and I get the biggest purple grub menu I've ever seen. There are a lot of kernels in them thar partitions, you see. :| So I have to reinstall grub to point to my Maverick partition again. Which is a pain.

I haven't been getting that 'keep maintainer's version?' type prompt with either Ubuntu or Kubuntu Natty, nor any other sort of prompt. Ubuntu leaves my mbr alone; Kubuntu writes to it without telling me.

Is there any configuration I can change or is this just one of those Kubuntu things?

---

### Post by ejket on 2011-03-13
Reinstall grub to the Natty partition.  I also have a multiboot -- Arch and Debian -- and I've been sticking with legacy grub.  On the original Natty install, I saw no option to skip grub, so I put it on the Natty partition and it hasn't been bothering me.

---

### Post by kansasnoob on 2011-03-13
Does Kubuntu use dpkg? I'd assume so :D

Basically grub "saves" prior installation info, so in Ubuntu I have to run:

```
sudo dpkg-reconfigure grub-pc
```

Then when asked where to install grub just uncheck all devices. After that when grub updates it'll remain "uninstalled".

---

### Post by coffeecat on 2011-03-13
Thank you both kindly. I was trying to remember what I did differently with the Ubuntu Natty install that meant that it wasn't reinstalling grub to the mbr every time grub was updated. Looking at the dates of system folders I see that I first installed it early December, which would have been around alpha1. If I remember correctly, Ubiquity in the daily CD about then got confused by my partition layout, so I did a netinstall from the mini.iso. I guess I must have passed when it asked me which device to install grub to.

kansasnoob's command seemed to run OK although it had a little moan at me when I opted not to install grub anywhere. Which makes a change from the moan grub2 has when you try to install it to the boot sector of a partition. :rolleyes:

Many thanks! :)

---

### Post by ejket on 2011-03-13
> **kansasnoob said:**
> Does Kubuntu use dpkg? I'd assume so :D

Yes, dpkg is a core part of all *buntu flavors -- in fact of all debian-based systems.

Thanks for the specifics -- it hadn't occurred to me that reconfiguring grub would offer the option to uninstall it.  Even though grub wasn't bothering me from where I'd put it, I decided that there was no harm in ditching it entirely if I wasn't using it.

---

### Post by Quackers on 2011-03-13
I've recently started running Fedora 14 and 15, and they both use grub legacy. As I needed grub legacy to install (so I could install the nvidia driver) I decided to install it to each of the Fedora root partitions, so as to avoid the over-writing of my controlling grub2 installation (Natty).
It does have a downside in that whenever there is a new kernel in Fedora, or a grub update of any kind, I have to reboot, login to Natty, run sudo update-grub, then reboot in to Fedora, but I see this as the lesser of 2 evils :-)

---

### Post by ejket on 2011-03-13
> **Quackers said:**
> I see this as the lesser of 2 evils :-)

I think it's better to stick with legacy grub when you have a fancy multiboot.  Grub2 is now like lilo in that you have to run a binary to update the configuration.  This is a huge pain when you have a fancy setup, as you are discovering first hand.  With legacy grub you just need to mount the /boot and edit the menu.lst -- why wouldn't you prefer that?

---

### Post by Quackers on 2011-03-13
Because grub2 is infinitely more configurable than grub legacy, imo.
(Not to mention the fact that grub legacy does not recognise some Linux OSes at all.)
Why stay in the past rather than finding a way of moving forward with the new? :-)

---

### Post by coffeecat on 2011-03-13
Welcome to the grub configuration megathread! :p

> **Quackers said:**
> It does have a downside in that whenever there is a new kernel in Fedora, or a grub update of any kind, I have to reboot, login to Natty, run sudo update-grub, then reboot in to Fedora, but I see this as the lesser of 2 evils :-)

I have another solution. Indeed, two solutions. :cool:

If you have installed Fedora's legacy grub stage 1 to the partition boot sector of your Fedora root partition, simply set up a chainloader stanza for Fedora in the Natty grub menu. You can chainload grub 2 to legacy grub because you can install legacy grub to a partition, but not usually the other way round. If you try to install grub2 to a partition, you get this:

>  /usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.This was one of the  moans I mentioned. Despite the "No error reported.", it usually fails to work for chainloading. 

Anyway, if you chainload to the Fedora partition, your Ubuntu grub menu will pass control to the Fedora grub menu, so long as you have uncommented the hiddenmenu line in Fedora's menu.lst.

The other solution makes use of the vmlinuz and initrd.img symlinks that most distros set up, which are updated each time a new kernel is installed so that they are linked to the new kernel. In Ubuntu they are in the root of the filesystem and it's easy to set your grub.cfg (40_custom) up so that when make your choice in the grub menu, you always boot into the latest kernel. 

I don't know where Fedora's kernel symlinks are, if indeed they have them. If not in the root of the filesystem have a look in /boot.

---

### Post by Quackers on 2011-03-13
Hmm, chainloading one grub to another grub sounds like doubling the chance of failure :-)
I'm quite happy with how things are currently, as my grub menu is er, sizable :-) (as well as Lucid, Maverick, 2 x Natty, I have Win 7, 2 x openSUSE, 2 x Fedora plus 6 iso's bootable from Natty's grub2 menu).
It is heavily modified with title changes and splash image, so I prefer to keep that one in control.

---

### Post by coffeecat on 2011-03-13
> **Quackers said:**
> Hmm, chainloading one grub to another grub sounds like doubling the chance of failure :-)

Hmmm. Possibly. :) If the second grub fails you get an error and after you press a key  you get dumped back to the first grub menu. If the first grub fails then you're snookered anyway. :wink:

---

### Post by Quackers on 2011-03-13
That's also true :-)
It's all good fun though!

---

### Post by ejket on 2011-03-13
> **Quackers said:**
> Because grub2 is infinitely more configurable than grub legacy, imo.
I'm sure you're right, but I couldn't find anything grub2 did extra that I personally wanted to do.  I just want to boot OSes, and the simpler the method and configuration, the better.  Grub2 is a mess, IMO -- too fancy, too automated, too many configuration files, and you need to update with a binary.

> (Not to mention the fact that grub legacy does not recognise some Linux OSes at all.)
When I actually encounter that, I'll have to deal with it, of course.

> Why stay in the past rather than finding a way of moving forward with the new? :-)
Despite my complaints above, I do use grub2 on machines with simple setups, because it's all automatic and it works.  But I have 8 distros on my main machine, and I find grub2 too annoying to use in this situation.

Also, I've been around for a long time, and I can tell you with some confidence that newer is not always better :)

I'd like to see a fork that kept legacy grub viable with future distros, or some new alternatives apart from lilo (which I've always disliked a lot).  But maybe grub2 will get better.

---

