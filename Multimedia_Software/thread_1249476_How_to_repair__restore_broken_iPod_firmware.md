---
title: "How to repair / restore broken iPod firmware"
date: 2009-08-25
forum: Multimedia Software
---

### Post by calcio1 on 2009-08-25
(copied from a blog post i just wrote to help others. Hopefully this is ok)

I have recently moved to linux and been pleased with the results. So pleased in fact that I decided to port my iPod over to an open-source OS, Rockbox.

The Rockbox OS has a lot of admirers but I found it fiddly, buggy and counter-intuitive. The simple matter that you can't simply select a 'shuffle' equivalent put paid to it for me.

But after uninstalling, I found my iPod buggy. There were clearly some remnants left of the Rockbox OS. I tried deleting everything I could find on the disk to no avail, so took the nuclear option of deleting the drive's partitions, figuring it would be easy to restore the original iPod firmware later. Nope.

Apple, helpfully, no longer supply individual firmware files: you must install iTunes. So I tried installing it in Wine. Nope.

A quick Google should provide the solution right? Nope. Nearly all the posts I found simply said, 'You're screwed, use a friend's Windows machine'.

That wasn't good enough. Eventually, after about two days' trying, I finally figured out what to do and was so pleased I decided to post about it to hopefully help other people.

First, go to this old but useful guide to see how to set up partitions on iPod. Ignore the stuff about HFS unless your iPod was originally formatted under Mac.

These are the relevant commands:

    % fdisk /dev/sd*
    n   [make new partition]
    p   [primary]
    1   [first partition]
    [just press enter -- default first sector is 1]
    5S  [5 sectors -- big enough to hold 32MB]
      [on 20GB models, Corrin Lakeland suggests using "+33MB" instead of 5S]

    n   [make new partition]
    p   [primary]
    2   [second partition]
    [just press enter -- default first sector is 6]
    [just press enter -- default size uses all remaining space]

    t   [modify type]
    1   [first partition]
    0   [first partition has no filesystem; ignore warning]

    t   [modify type]
    2   [second partition]
    b   [second partition is FAT32]

    p   [show partition map]

    Device Boot    Start       End    Blocks   Id  System
    /dev/sd*1          1         5     40131    0  Empty
    /dev/sd*2          6      3647  29254365    b  Win95 FAT32

    w   [commit changes to disk]

* You need to know what the device name of your iPod is. Find out by 'sudo fdisk -l' without it attached then with it attached and note what was added. It will probably be sda, sdb, etc.

This creates two partitions on your iPod, sd*1 for the firmware and sd*2 for storage.

Then download the right firmware for your iPod from this site. Extract it somewhere convenient. Note the name of the firmware file.

To install the firmware type this command 'sudo dd if=FIRMWAREFILENAME of=/dev/sd*1.

BE 100% CERTAIN YOU TYPE THE RIGHT SD*1 NAME! For example, don't do what I did and try to install iPod firmware on your computer hard disk by accidentally typing 'sda1' instead of 'sdb1'. Unless you like reinstalling your operating system.

To format the storage partition type this command: 'mkfs.vfat -F 32 -n "ipod" /dev/sd*2.' This creates a vfat partition of F32 type named "ipod".

Unplug your iPod. Reboot if necessary. You should see a picture on the screen telling you to plug it back in. Do so - hopefully all should be fixed, it will automatically mount and Rhythmbox or whatever iTunes equivalent you use will recognise it. Then you can select 'initialise iPod' to create the directory structure.

Appendix - this site is also useful for editing fstab if your iPod does not automount.





[URL="http://josemousetrap.blogspot.com/2009/08/how-to-repair-restore-ipod-firmware-on.html"]
http://josemousetrap.blogspot.com/2009/08/how-to-repair-restore-ipod-firmware-on.html[/URL]

---

### Post by Chronon on 2009-08-25
In fact you can find similar instructions on the Rockbox wiki (how to restore your iPod in linux).  I can't link to =it right now due to an attack on the ISP where the site is hosted. (Actually, here's the [cached version from Google](http://74.125.155.132/search?q=cache:TQ7MzKgpTiwJ:www.rockbox.org/twiki/bin/view/Main/IpodManualRestore+http://www.rockbox.org/twiki/bin/view/Main/IpodManualRestore&cd=1&hl=en&ct=clnk&gl=us&client=firefox-a)

A couple of responses:
I'm not sure what you mean about lack of an easy "shuffle" equivalent since this is one of the options in the quick menu by default.  

If the iPod seemed buggy after you removed Rockbox do you think it's possible that a corrupt file system may have played some part?  There shouldn't be any pieces left of Rockbox after uninstalling. If the bootloader was removed and the .rockbox folder was deleted then there would be no trace of it left on the player.  Lingering buggy behavior points to some other underlying origin.

---

### Post by calcio1 on 2009-08-25
Possibly. There was definitely some remnants of rocbox left that led to hanging and crashes. On reset it would try to load rockbox, despite uninstalling and deleting everything. 

Can't remember exactly what my problem with shuffle was on rockbox, sure you had to set up a playlist of all your music first then put in on random which annoyed me.

---

### Post by Chronon on 2009-08-27
That tells me that you never removed the bootloader.  

To each his own.  Use what works for you.

Tip: You can create a dynamic playlist containing all tracks by going to Database > Tracks > select the first track.

The Rockbox wiki page is accessible again. Here is the relevant page for restoring your iPod manually in Linux.
[http://www.rockbox.org/twiki/bin/view/Main/IpodManualRestore](http://www.rockbox.org/twiki/bin/view/Main/IpodManualRestore)

---

