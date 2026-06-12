---
title: "[SOLVED] Functionality questions and a HDD issue..."
date: 2008-04-07
forum: Mythbuntu
---

### Post by Skawn on 2008-04-07
Hi all,

I'll start off by saying I'm totally new to linux so please be patient!

My first questions are about functionality and the file structure used for Mythbuntu:

1) I currently have an 80Gb drive which I've installed Mythbuntu and XP on and a 500Gb disk full of data (films, music etc).  It it possible to get Myth tv to browse the 500Gb disk when I choose 'Watch a video' or 'Listen to Music' from the main menu?  It seems to only want to use it's own file structure. 

2) I set the video folder to be shared and dropped an AVI into it from my over the network (from an XP machine) but it wasn't then visible when selecting 'Watch a Video' from the menu.  Any reason for this?  Does it need a reboot to pick new media up?


Finally, an HDD problem...

I installed Mythbuntu this weekend but have had some HDD problems since. At the start of the day, I had an 80Gb SATA drive with XP installed and an older ATA 500Gb drive connected with 'oldschool' IDE ribbon.

This worked fine before I started!

I then disconnected the 500Gb drive so I could pop a CD drive in (it's a HTPC and I've not bothered with an optical drive before) and reinstalled XP on a 10Gb partition on the 80Gb drive. Once that was fully patched, I installed Mythbuntu on the remaining space on that drive.

That worked fine and the system will happily dual boot either XP or Mythbuntu. However, when I now remove the CD drive and pop the 500Gb back in, BIOS won't allow me to choose the SATA drive to boot from.

BIOS still sees the SATA drive in the summary screen showing what is connected but won't let me pick it as the boot disk, only offering the 500Gb drive (which has no OS installed).

Anyone have any idea why that might be? I was wondering it it might have something to do with GRUB?

---

### Post by johnnybirdman on 2008-04-07
I can't help with HD issue, but I think I can answer the other quesitons.

> **Skawn said:**
> 
1) I currently have an 80Gb drive which I've installed Mythbuntu and XP on and a 500Gb disk full of data (films, music etc).  It it possible to get Myth tv to browse the 500Gb disk when I choose 'Watch a video' or 'Listen to Music' from the main menu?  It seems to only want to use it's own file structure. 
you can use a symlink, they are like shortcuts but more powerful.  look here [**[COLOR="DarkOrange"]http://ubuntuforums.org/showthread.php?t=255573[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=255573")

> 
2) I set the video folder to be shared and dropped an AVI into it from my over the network (from an XP machine) but it wasn't then visible when selecting 'Watch a Video' from the menu.  Any reason for this?  Does it need a reboot to pick new media up?
I don't remember the exact menu selections but you need to go to 'options/setup' then to 'manage videos' it will then scan the drive/file location for new/existing media.  It should then find what you put in there.

I just set up my first mythbuntu box a few days ago.  After only  a short time I find it to be very functional and easy to use.  Play with it some and you will get the hang of it.
J.

PS.  I'm running version 8.04, not sure what you are running.

---

### Post by Skawn on 2008-04-07
I think I'm running 7.10?  It was the latest non-beta build... I'm sure the scan disk option will be in the same place, probably just missed it /facepalm

I'll do some reading on the Symbolic Links stuff, thanks for the info.

---

### Post by Skawn on 2008-04-09
Progress!  I found the option to scan for media and am really impressed with the playback.  I also managed to get it to boot from the drive with the O/S installed instead of my media disk... was an option for which drive to use in BIOS which I'd missed...

Still not having any joy with getting MythVideo to use my media disk though.  I've found the screen where you can give MythVideo other directorys to look at but have no idea how that drive is addressed in Linux/ubuntu format!  In windows, I'd be pointing it to D:/media - whats the linux equiv?

EDIT:  I thought I had it!  dev/disk/by-label/storage is the disk but that doesn't work to address it in MythVideo, nor does it make it available to my XP machine when I set it to be shared... I get the feeling I'm so close and yet...

EDIT2: From what I've read since posting, I meed to mount the drive to be able to view it in the file structure.  I tried opening terminal and typing  "mount /dev/disk/storage /mnt/media" and "mount /dev/disk/by-label storage /mnt/media" both of which give the error "mount: command not found".  Am I on the right lines?  If so, could someone correct my syntax please?


[crossposted: [http://www.linuxforums.org/forum/ubuntu-help/118981-hdd-no-longer-available-boot.html#post576357]](http://www.linuxforums.org/forum/ubuntu-help/118981-hdd-no-longer-available-boot.html#post576357])

---

