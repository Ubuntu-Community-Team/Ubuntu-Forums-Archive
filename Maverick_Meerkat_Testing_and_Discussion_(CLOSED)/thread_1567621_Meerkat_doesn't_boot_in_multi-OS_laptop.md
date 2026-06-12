---
title: "Meerkat doesn't boot in multi-OS laptop"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2010-09-04
Hello,

I have a laptop that has Win7, Fedora Core 13, Ubuntu 10.04 and openSUSE 11.3.  OpenSUSE is the default or controlling system that boots all OS's. When I installed Meerkat a few hours ago in a new and separate partition (#12), it asked me where to put the boot loader so I said sda8 which is the root partition of openSUSE.  After installation is completed I rebooted the box and saw all other OS's and was able to boot into them individually, including Ubuntu 10.04, as before.

I then booted into openSUSE and added the following into its grub/menu.lst file, similarly to the entry for Ubuntu 10.04, because Meerkat was installed in sda[COLOR="Blue"]12[/COLOR]:

```
rootnoverify (hd0,[COLOR="DarkRed"]11[/COLOR])
chainloader +1
```

However, after rebooting, I was not able to boot into Meerkat. The error message was:

```
[COLOR="Blue"]Error 13: Invalid or unsupported executable format.  Press any key to continue[/COLOR]
```

Here's the output of /sbin/fdisk -l in openUSE, noting that sda8 is the root partition of openSUSE where the original Grub bootloader is situated, sda6 is Ubuntu 10.04's root partition, and sda12 is the root partition of Meerkat. I purposely did not create a /home partition for Meerkat:

```
# /sbin/fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00532bde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        3200    25600000    7  HPFS/NTFS
/dev/sda3            3201        7715    36266737+   7  HPFS/NTFS
/dev/sda4   *        7716       21051   107121389+   5  Extended
/dev/sda5            7716        7842     1020096   82  Linux swap / Solaris
/dev/sda6            7843       10459    21021021   83  Linux
/dev/sda7           10460       11766    10498446   83  Linux
/dev/sda8           11767       14335    20635461   83  Linux
/dev/sda9           14336       15623    10345828+  83  Linux
/dev/sda10          15624       17770    17245746   83  Linux
/dev/sda11          17771       19109    10755486   83  Linux
[COLOR="Navy"]/dev/sda12          19110       21051    15599083+  83  Linux[/COLOR]

```


Can you help me sort this problem out?
Thanks a lot for your help.

---

### Post by coffeecat on 2010-09-04
Installing grub 2 to the partition boot sector seems to be hit and miss - I think this is your problem - hence the failure with chainloading. Try doing a grub-install to a partition from the terminal with grub2 and you'll see a snotty error message.

When I say hit and miss, I can grub-install to a partition rather than the mbr with my two laptops, but not with my two desktops. Why? Haven't a clue.

What you can do is to create a boot stanza in your Suse menu.lst with the kernel line calling the symlink /vmlinuz in your Maverick root and the initrd line the initrd.img symlink also in root. This means that you can only boot the newest kernel and would have to edit the boot line on the fly if you need recovery mode, but at least it works.

**Edit:** just re-read your post and saw that you can successfully boot into Lucid which also uses grub 2. Hmm. Do you chainload into Lucid as well? If so, perhaps this isn't the issue affecting you.

Try setting up the stanza I suggested to get into Maverick and then do a sudo grub-install /dev/sda12 in the terminal (in Maverick). You'll probably still get the error message but that might enable you to chainload successfully.

---

### Post by iClouseau88 on 2010-09-04
> **coffeecat said:**
> 
...What you can do is to create a boot stanza in your Suse menu.lst with the kernel line [COLOR="Blue"]calling the symlink /vmlinuz [/COLOR]in your Maverick root and the [COLOR="DarkRed"]initrd.img symlink[/COLOR] also in root. This means that you can only boot the newest kernel and would have to edit the boot line on the fly if you need recovery mode, but at least it works.

Hi,

I don't like the new installer, unlike the previous one for Lucid Lynx which has a box where during installation I could get grub bootloader to be placed in Ubuntu's own boot/root partition (to avoid messing up grub in a multiboot situation).
 
Could you show me the exact commands for doing these 2 things?  I don't know details such as kernel description and version.

Thanks a lot for your help.

---

### Post by coffeecat on 2010-09-04
> **iClouseau88 said:**
> Could you show me the exact commands for doing these 2 things?  I don't know details such as kernel description and version.

Post the contents of your Suse menu.lst and then mount your Maverick partition from Suse so that you can post the contents of your Maverick /boot/grub/grub.cfg.

From those two I'll be able to cobble together a working stanza in the way I suggested. Once we've got you booting into Maverick we can see about trying to reinstall grub2 to your Maverick partition.

Oh - while you're about it, post the output of 'blkid' from a root terminal in Suse or 'sudo blkid' in Lucid. That's to get the UUID of your Maverick partition. It should be in your Maverick grub.cfg but I'd like to double-check this.

---

### Post by coffeecat on 2010-09-04
> **coffeecat said:**
> Post the contents.....

Sorry - that was unhelpful of me. I can do this with the information you've already posted.

Add this to your Suse menu.lst:

```

title     Maverick, direct boot
root      (hd0,11)
kernel    /vmlinuz root=/dev/sda12 ro quiet splash
initrd    /initrd.img
boot

```That should get you booting into Maverick and then we can see about reinstalling grub to sda12 to get you chainloading.

**Edit:** and also just noticed this (I need some coffee :p):

[quote="iClousea88"]it asked me where to put the boot loader so I said sda8 which is the root partition of openSUSE[/quote]

That wouldn't work. You should have specified sda12 in order to chainload from the Suse menu, except that installing grub2 to the sda12 partition boot sector may or may not work for the reasons I explain in my first post. Whatever - if the above stanza gets you into Meerkat, we can see about chainloading then if you want.

---

### Post by vishalrao on 2010-09-04
what if you simply run "update-grub" as root in opensuse? does it not auto-detect other OSes that way?

---

### Post by coffeecat on 2010-09-04
> **vishalrao said:**
> what if you simply run "update-grub" as root in opensuse? does it not auto-detect other OSes that way?

Good point. You've reminded me that in Suse, if you edit system files it tends to tidy them up again. Which is why, iirc, there's a facility in Yast for doing this, rather than running from the terminal. Can't remember the details.

---

### Post by iClouseau88 on 2010-09-04
Hi,

I booted into openSUSE and got the following from the terminal:

```
#update-grub
If 'update-grub' is not a typo you can use command-not-found to lookup the package that contains it, like this:
    cnf update-grub

```

```
# grub-install /dev/sda12
WARNING! You are trying to invoke the unsupported grub-install script
with a parameter. To really do this, call grub-install.unsupported.
You should rather call "yast2 bootloader" or create configuration files
appropriate for the intended target.

```

Now I have 2 choices:
1) Try the suggestion by coffeecat in Post#5;

2) Re-install Meerkat in partition sda12 but choose to boot from the same partition, and pray that I will still be able to boot into any OS on Suse's GRUB menu.  I am not sure if I ever saw in the (new) installer the ADVANCED button (like in Lucid) that gives me a choice where to put the bootloader. 

What do you suggest?

---

### Post by ktp on 2010-09-04
> **iClouseau88 said:**
> 
2) Re-install Meerkat in partition sda12 but choose to boot from the same partition, and pray that I will still be able to boot into any OS on Suse's GRUB menu.  I am not sure if I ever saw in the (new) installer the ADVANCED button (like in Lucid) that gives me a choice where to put the bootloader. 

What do you suggest?

the new installer doesn't seem to have place, at least right now, for grub location.  See following thread, which as bug link also:

[http://ubuntuforums.org/showthread.php?t=1548416](http://ubuntuforums.org/showthread.php?t=1548416)

---

### Post by cariboo on 2010-09-05
The installer does allow you to select where to install grub if you use the manual partition option, it's only if you use automatic partitioning that you don't get a choice.

---

### Post by iClouseau88 on 2010-09-05
> **ktp said:**
> the new installer doesn't seem to have place, at least right now, for grub location.  See following thread, which as bug link also:

[http://ubuntuforums.org/showthread.php?t=1548416](http://ubuntuforums.org/showthread.php?t=1548416)

@ktp:

Thanks for your reply.  Now I am aware of this bug.

By the way, I was just able to boot into Meerkat by following coffeecat's suggestion in Post#5 and I am writing this reply on my laptop!

It's strange that "aptitude" and "safe-upgrade" no longer work when I am trying to update Meerkat:

```
~$ sudo aptitude update && sudo aptitude safe-upgrade
sudo: [COLOR="Blue"]aptitude: command not found
E: Invalid operation safe-upgrade[/COLOR]

```

I was able to update using sudo apt-get instead.

@coffeecat:

```
~$ sudo [COLOR="DarkRed"]blkid[/COLOR]
 
/dev/sda12: [COLOR="DarkRed"]UUID="998b88b4-d861-4c3f-a154-ac2cbb0979bc" TYPE="ext4"[/COLOR] 
```

Now how can I get the chainloading to work for Meerkat (meow! meow!)?

Cheers!

---

### Post by iClouseau88 on 2010-09-05
Hello cariboo907,

Greetings! I used to live in BC for many years!
Anyway, I did choose manual partition.  I was afraid that if I were to put the bootloader in Meerkat's root partition sda12 I would mess up Suse's (default) grub bootloader which controls all the OS's loading.  I forgot that Suse would "hand over" grub bootloading to any OS that is installed after it, if the new bootloader is placed in the new OS's root or boot partition.

---

### Post by ranch hand on 2010-09-05
> **iClouseau88 said:**
> @ktp:

Thanks for your reply.  Now I am aware of this bug.

By the way, I was just able to boot into Meerkat by following coffeecat's suggestion in Post#5 and I am writing this reply on my laptop!

It's strange that "aptitude" and "safe-upgrade" no longer work when I am trying to update Meerkat:

```
~$ sudo aptitude update && sudo aptitude safe-upgrade
sudo: [COLOR=Blue]aptitude: command not found
E: Invalid operation safe-upgrade[/COLOR]

```I was able to update using sudo apt-get instead.

@coffeecat:

```
~$ sudo [COLOR=DarkRed]blkid[/COLOR]
 
/dev/sda12: [COLOR=DarkRed]UUID="998b88b4-d861-4c3f-a154-ac2cbb0979bc" TYPE="ext4"[/COLOR] 
```Now how can I get the chainloading to work for Meerkat (meow! meow!)?

Cheers!
Aptitude is no longer installed by default in 10.10.  I don't want to hear about it.  I use apt but still put my "me too" on the bug objecting to this.

You need to install it if you want to use it.
```

apt-get install aptitude

```

But hey, you don't need it, you have the Ubuntu Software Center.

---

### Post by cariboo on 2010-09-05
> **iClouseau88 said:**
> Hello cariboo907,

Greetings! I used to live in BC for many years!
Anyway, I did choose manual partition.  I was afraid that if I were to put the bootloader in Meerkat's root partition sda12 I would mess up Suse's (default) grub bootloader which controls all the OS's loading.  I forgot that Suse would "hand over" grub bootloading to any OS that is installed after it, if the new bootloader is placed in the new OS's root or boot partition.

It's not only openSUSE, but any disto that uses grub. It's always the last install that controls grub by default, if you don't do anything.

---

### Post by iClouseau88 on 2010-09-05
Hello ranch hand,

I found "aptitude" in Synaptic so it was installed from there.

Me think Ubuntu Software Center is trying to make Windoz refugees feel more at home!

I am still trying to get used to some of the new "quirks" in Meerkat, such as the set of Close, Minimize, Maximize buttons being on the left, or Network Manager icon (up/down arrows).  I don't see where I can find network info as I used to be able to, by hitting the interface in NM.

---

### Post by coffeecat on 2010-09-05
> **iClouseau88 said:**
> Now how can I get the chainloading to work for Meerkat (meow! meow!)?

Cheers!

Assuming that Meerkat is still on sda12, boot into it with the stanza I posted in post #5 and do this from the terminal:

```
sudo grub-install /dev/sda12
```By specifying sda12, you are attempting to install grub2 stage 1 (plus whatever used to be called stage 1.5) to the partition boot sector rather than the disc MBR. Bear in mind my comments in post #2. This may or may not work for reasons that are beyond me. Either way you will probably get a sniffy error message. All you can do is to then reboot and try your original chainloading stanza in the Suse grub menu.

If that doesn't work, then sorry, I have no alternative. With my two laptops I can chainload. With my two desktops I have to use something along the lines of what I gave you in post #5.

Good luck.

---

### Post by iClouseau88 on 2010-09-05
Hello coffeecat,

Thanks for your reply. Yes, Meerkat is still  on sda12 and I was able to boot directly into it thanks to your Post#5 suggestion.  Here's what the terminal shows when I try to install grub in sda12:

```
~$ sudo grub-install /dev/sda12
 
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..

My note: Suse's grub is installed in the MBR
 
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, [COLOR="Blue"]blocklists are UNRELIABLE and their use is discouraged[/COLOR]..

/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```

If I want to use blocklist, do I have to replace /dev/sda12 with its UUID like the following?

```
sudo grub-install "Place UUID here"  --force
```

---

### Post by coffeecat on 2010-09-05
Yes, that's the error message I get. This.....

> /usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..... gets so far up my nose it exits out the back of my head. Bad idea indeed. It was a perfectly good idea in legacy grub, and is the only way I know to chainload successfully. Grub is meant to be an OS-agnostic bootloader and as such is used by people wanting to multi-boot different OSs, many of whom find chainloading to be a convenient way of doing this. And to chainload Linux you need to install grub to a partition.

Bah! I don't care if there are technical problems installing whatever replaced the old legacy grub 1.5 to a partition rather than the embedding area. I don't care at all. The grub devs should have thought this one through before embarking on grub 2.

Bah indeed!

[/rant_over] :wink:

Anyway....

Try the force option with '/dev/sda12' - I have no idea what using the UUID would do. With my laptops, if I use the --force option I get the error message, but it works. With my desktops, it doesn't work. :confused: If anyone more knowledgeable than me can shed any light on this, I would be glad to be enlightened.

---

### Post by VMC on 2010-09-05
> **coffeecat said:**
> Yes, that's the error message I get. This.....

... gets so far up my nose it exits out the back of my head. Bad idea indeed. It was a perfectly good idea in legacy grub, and is the only way I know to chainload successfully. Grub is meant to be an OS-agnostic bootloader and as such is used by people wanting to multi-boot different OSs, many of whom find chainloading to be a convenient way of doing this. And to chainload Linux you need to install grub to a partition.

Bah! I don't care if there are technical problems installing whatever replaced the old legacy grub 1.5 to a partition rather than the embedding area. I don't care at all. The grub devs should have thought this one through before embarking on grub 2.

Bah indeed!

[/rant_over] :wink:

Anyway....

Try the force option with '/dev/sda12' - I have no idea what using the UUID would do. With my laptops, if I use the --force option I get the error message, but it works. With my desktops, it doesn't work. :confused: If anyone more knowledgeable than me can shed any light on this, I would be glad to be enlightened.
I wouldn't call what you stated a rant. Its the way you want grub to work. Using chainloading. Many people still prefer that method. I always smile when I see folks circumvent the purist way of doing things. Its your computer after all.

There was a topic on "Is this a bid idea" during the Lucid cycle. It had some informative posts.

---

