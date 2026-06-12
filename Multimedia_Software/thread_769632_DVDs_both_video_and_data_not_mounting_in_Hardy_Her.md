---
title: "DVDs both video and data not mounting in Hardy Heron"
date: 2008-04-26
forum: Multimedia Software
---

### Post by pcmantinker on 2008-04-26
I just recently did a clean install of ubuntu Hardy Heron and I am unable to watch DVDs. I have followed a few tutorials on how to do so, but for some reason, the DVD isn't mounting. When I put the DVD in the drive and  double click on my CD/DVD+-RW drive, it says "Unable to mount location no media in the drive". I tried a data DVD backup of some of my documents and got the same message. Then when I try to mount a CD-ROM, it gives me the same error. I restart ubuntu and then it works. I have installed libdvdcss2 and libdvdread3. I have run this script also:
```

sudo /usr/share/doc/libdvdread3/install-css.sh

```
I am curious as to why this isn't working because it worked in Gutsy Gibbon just fine. Could it be that there is something more that I have to do for Hardy Heron to read DVDs? It's not a big deal if I can't get DVD mounting working, but I would like to try. I have recently become a big fan of Ubuntu. I like its simplicity of use and stability.

---

### Post by odin79 on 2008-04-26
You are not alone, these problems are mounting up it seems like. I have been scouring the forums for to long now, but no use so far. For me all the problems started after installing Hardy. All was well in Gutsy. For me this is a major show-stopper!

---

### Post by pcmantinker on 2008-04-26
I hope that this issue is resolved soon. I don't want to have to revert back to Gutsy Gibbon if I don't have to. I know that my drive isn't bad either because Windows XP can play DVDs with no problem at all. I think that I'm missing some sort of file system library allowing me to read DVD file systems. I've looked at several tutorials without any success however.

---

### Post by odin79 on 2008-04-27
Yeah me to, I really don't want to do a reinstall as it will take forever. We have discussed it in this thread: [http://ubuntuforums.org/showthread.php?t=767449](http://ubuntuforums.org/showthread.php?t=767449) , but without finding any solutions so far...

---

### Post by pcmantinker on 2008-04-27
Thanks. I will take a look at that thread.

Edit: I have figured out how to play DVDs on my ubuntu Hardy system. Make sure that you have libcssdvd2, libdvdread3 and other libraries installed. Then, make sure that your /etc/fstab is configured correctly. I have my dvd drive setup to this in fstab:
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

```
Then download a media player such as vlc or kaffeine and try to play a DVD. Each system is different, but let me know if this works.

---

### Post by odin79 on 2008-04-27
No it didn'n make any difference at all. I will make a fresh install tomorrow if I bothers and let you know how it goes.

---

### Post by alexforcefive on 2008-04-27
Agh, upgrading to hardy broke my dvd-rom drive too. Discs mount but dvds won't play, and cd playback is horrible. Everything worked in gutsy. I honestly have no idea where to start with this, does anyone have any ideas?

---

### Post by mc4man on 2008-04-27
If the disks _mount_ follow some sugg. in thread linked a few posts above or ck. this [http://ubuntuforums.org/showthread.php?p=4734003#post4734003](http://ubuntuforums.org/showthread.php?p=4734003#post4734003)
or here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
If can't get working start vlc in terminal and post output

---

### Post by Therion on 2008-04-28
Same issue for me.  I couldn't even INSTALL Hardy until I swapped my DVD-RW with an aging DVD-ROM drive I had lying around.  I've tried two different, known-good,  DVD-RW drives (a Plextor 716A and a Sony DRU190); neither would install Hardy from the LiveCD or mount if installed on an otherwise working Hardy system.  

The ancient DVD-ROM drive I dug up installed Hardy and mounts without a single problem.  Had I not run across the solution of swapping the burner for a ROM drive by scouring the intarwebs I never would have been able to even install Hardy.  Talk about a show stopper!

Right now I'm just living without being able to burn optical media but it sucks *hard*.  I'll have no choice but to bite the bullet and  revert to another version if there's no solution forthcoming.

I'll try some of the things I see listed here and see what I can get going... Until then, I'm in this boat as well.

---

### Post by pcmantinker on 2008-04-28
I was able to install Hardy just fine, but I couldn't get DVD playback working from the get go. I think I may have found a permanent solution, but I am unsure yet. I will let everyone know if I do find one.

---

### Post by alexforcefive on 2008-04-28
After reading [this thread](http://ubuntuforums.org/showthread.php?t=756200) (last post), I tried going back to the old kernel and the problem has cleared up! Probably not the optimal solution, but it works. It also solved an unrelated issue with my midi controller

---

### Post by mc4man on 2008-04-28
@ alexforcefive
If you have occasion to boot back into latest kernel it would be interesting to see what dvd links you have in /dev and what they link to
there could be up to 4 -  dvd,dvdrw,dvd1,dvdrw1,

---

### Post by epedersen on 2008-04-28
I'll second the motion about booting back into the older kernel.  My DVD was MIA after doing an in-place upgrade from 7.10 to 8.04.

Booting to the 2.6.24-16-generic kernel, versus the 2.6.24-16-i386 kernel fixed the DVD.

---

### Post by alexforcefive on 2008-04-29
> **mc4man said:**
> see what dvd links you have in /dev and what they link to

Ah, now here's something interesting - with the OLD kernel, I have dvd and dvdrw. With the NEW kernel I have dvd1 and dvdrw1. Could that be causing the problems? Can I just rename the links?

*edit* I just created new links named dvd and dvdrw - didn't help :( I also noticed that only root has permission on those files, so I tried adding read/write permission for other users but that didn't help. Bleh, I dunno

---

### Post by mc4man on 2008-04-29
q

---

### Post by hardy_heron on 2008-05-10
Thanks PCMANTINCKER

I also found a solution for AMD users

First you need to install the following packages

sudo apt-get install debhelper build-essential fakeroot

Now download the libdvdcss2 library using the following command

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

use the following command as PCMANTINCKER gave

sudo /usr/share/doc/libdvdread3/install-css.sh

---

### Post by kadrach on 2008-06-28
I have the same problem, CD's and non-commercial DVD's mount just fine. A commercial DVD will spin up a few times, but will not mount.

I also get no errors in dmesg or syslog. Manual mount gives the error "special device /dev/sdc0 does not exist", regionset tells me that there is no media in the drive. None of the suggested solutions have worked so far.

This is not solved by changing to an older kernel version. I currently run 2.6.24-19-generic and use the most recent libdvd* from the medibuntu repository.

```

**Relevant part of lshw -C disk**
  *-cdrom
       description: DVD reader
       product: COMBO SOSC-2483K
       vendor: Slimtype
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: KKU1
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open

```

```

**/etc/udev/rules.d/70-persistent-cd.rules**
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
```

---

### Post by dtl on 2008-09-17
Hi everybody,
 I'm not sure i belong here since I'm still a newbie and don't understand much of the technical talk and have just moved over to Kubuntu from Mandriva. I thought I might do no harm in adding that I have resolved my problem by restarting the pc. Then the dvds play. Don't have a clue why and it's a typical "windows" ignorant solution but so far it's the only thing that works for me. :)
 I will follow this thread for a better solution.

---

### Post by alexforcefive on 2008-09-17
Just a wee quick update since someone's bumped this thread... I built a new computer recently, and the same cd drive I was having trouble with now works! So err.. I have no idea what the problem was, but the new motherboard seems to have resolved it

---

