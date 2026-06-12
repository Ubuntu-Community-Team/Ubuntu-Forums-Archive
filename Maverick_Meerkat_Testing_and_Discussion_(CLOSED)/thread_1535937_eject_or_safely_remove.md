---
title: "eject or safely remove ?"
date: 2010-07-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ronacc on 2010-07-21
when you have a usb stick mounted and wish to remove it the RT click menu shows an entry for eject and an entry for safely remove . Selecting safely remove does not work because it immediately remounts automatically  and opens a nautilus window . This is confusing and counter intuitive  since you do not "eject" a usb stick you remove it . what package should I bug about this ?

---

### Post by dino99 on 2010-07-21
i guess you might report against usbmount:

This package automatically mounts USB mass storage devices (typically
USB pens) when they are plugged in, and unmounts them when they are
removed. The mountpoints (/media/usb[0-7] by default), filesystem types
to consider, and mount options are configurable. When multiple devices
are plugged in, the first available mountpoint is automatically
selected. If the device provides a model name, a symbolic link
/var/run/usbmount/MODELNAME pointing to the mountpoint is automatically
created.

The script that does the mounting is called by the udev daemon.
Therefore, USBmount requires a 2.6 (or newer) Linux kernel.

Firewire devices are also supported by USBmount.

USBmount is intended as a lightweight solution which is independent of
a desktop environment. Users which would like an icon to appear when an
USB device is plugged in should use the pmount and hal packages
instead.

---

### Post by VMC on 2010-07-21
> **ronacc said:**
> ... Selecting safely remove does not work because it immediately remounts automatically  and opens a nautilus window . This is confusing and counter intuitive  since you do not "eject" a usb stick you remove it . what package should I bug about this ?

This topic has come up before in recent memory, but you bring up something new that I also have experienced. Not just flash drive, but my USB hard drive behaves the same way. No matter which option, it removes all partitions on the hd but then promptly brings them back to life. If I then remove it again, then everything is removed. This behavior doesn't happen using Lucid.

---

### Post by zekopeko on 2010-07-21
> **ronacc said:**
> when you have a usb stick mounted and wish to remove it the RT click menu shows an entry for eject and an entry for safely remove . Selecting safely remove does not work because it immediately remounts automatically  and opens a nautilus window . This is confusing and counter intuitive  since you do not "eject" a usb stick you remove it . what package should I bug about this ?

General rule: If you don't know what package it is file it against the user visible component, in this case Nautilus. The devs will reassign it if it's incorrect.

---

### Post by ranch hand on 2010-07-21
And there is not unmount option.  I am running on a usb HDD.  There are times I need to unmount all drives except the one I am on.

I can only do this with Disk Utility one at a time.  This is a real waste of time with the number of partitions I have on the HDD.

On other versions I can highlight all I want closed, right click, unmount.  Fast and easy.

---

### Post by seeker5528 on 2010-07-21
> **ronacc said:**
> when you have a usb stick mounted and wish to remove it the RT click menu shows an entry for eject and an entry for safely remove . Selecting safely remove does not work because it immediately remounts automatically  and opens a nautilus window . This is confusing and counter intuitive  since you do not "eject" a usb stick you remove it . what package should I bug about this ?

The last time I used usbmount it's OOB configuration was not set up to make your FAT or NTFS filesystems RW for user access and I had to drop to the command line and do 'eject /media/blah' if I wanted to unmount my flash drive without using sudo. 

So pmount still seems like the way to go to provide the automounting and whatever umount/eject/safely remove type features that go along with that, which are provided by Nautilus.

You might, after doing 'safely remove' open a terminal window and type:

```
dmesg
```

: to see what kind of messages may be reported there.

Since using 'safely remove' typically makes your flash drive unavailable until you unplug it then plug it in again, I would guess that it's not "remounting", but that it fails to even unmount the partion or partitions on the flash drive, which then blocks the ability to shut off the flash drive. 

I would expect if it unmounted the partition on the flash drive, then failed to shut off the flash drive, that the partition would stay unmounted, but that's just a guess, you never know for sure.

Don't know what the difference between 'safely remove' and 'eject' is, the results are the same on my machine, with my flash drive, with pmount installed, usbmount not installed.

Later, Seeker

---

### Post by ronacc on 2010-07-21
I have basically a vanilla maverick install , uptodate . I have neither usbmount or pmount installed . safely remove does unmount the pen drive but then imeadately reconnects to it (it does the same with a usb HD) and after the  remount files are still accessible by ordinary user . Eject unmounts the drive and then it can be removed because it does not remount . Dmesg shows that when safely remove is used as soon as it disconnects it reconnects at the next usb address for example was on 5 remounts on 6 . when eject is selected dmesg just shows that it disconnects and then does not remount .

note to ranch hand try eject with your usb HD it works with mine .

I'll bug nautilus and let the devs sort it out .

---

### Post by ronacc on 2010-07-21
bug# 608508

---

### Post by VMC on 2010-07-21
> **ronacc said:**
> bug# 608508

Thanks. I will "me too" it.

Edit: I missed your note. that's why the added comment.

---

### Post by hugmenot on 2010-07-22
Nautilus and gvfs are the packages that this pertains to. It would be good i people searched a bit before spamming launchpad with new bugs. This issue is an old one. There used to be three options even.

There is a clear rationale, why you need two different menu items.

The kernel can&#8217;t meaningfully distinguish between devices that need an eject and powerdown and devices that just need an unmount.

[http://thread.gmane.org/gmane.linux.usb.general/22706/focus=22748](http://thread.gmane.org/gmane.linux.usb.general/22706/focus=22748)

[http://git.gnome.org/browse/gvfs/commit/?id=6e70902ee77cb0bd6063bcf4d215b13a13bf5ee4](http://git.gnome.org/browse/gvfs/commit/?id=6e70902ee77cb0bd6063bcf4d215b13a13bf5ee4)

[https://bugzilla.gnome.org/show_bug.cgi?id=598690#c8](https://bugzilla.gnome.org/show_bug.cgi?id=598690#c8)

---

### Post by ronacc on 2010-07-22
the bug is not about the number of choices it is about the fact that "safely remove" does NOT allow you to safely remove the drive .IMHO that is a serious bug .

---

### Post by philinux on 2010-07-22
> **VMC said:**
> Thanks. I will "me too" it.

Edit: I missed your note. that's why the added comment.

Dont just me too. Change the status to Confirmed.

---

### Post by VMC on 2010-07-22
> **philinux said:**
> Dont just me too. Change the status to Confirmed.
Thank you. I thought that was up to the dev's to do that.

---

### Post by philinux on 2010-07-22
> **VMC said:**
> Thank you. I thought that was p to the dev's to do that.

Yes. Obviously it's not launchpad netiquette that the Bug raiser should confirm his/her own bugs. Thats why someone else needs to do it.:p

I've seen some bugs with lots of me too comments and still at status new.

---

### Post by andrewabc on 2010-07-22
On ubuntu 9.10 for a usb I have
unmount
eject
safely remove drive

Is it the same on 10.10? That's a lot of options for dumb users. Eject sound like good one to get rid of. Safely remove drive is best sounding. unmount only makes sense if multiple partitions loaded on usb stick (or wanting to unmount to format it?).

When I turn on external esata 3.5" I only get unmount option. Which makes sense I guess since ubuntu only sees it as sata connection. And I have 2 partitions on the 1tb external.

---

### Post by davideotape on 2010-07-22
For my external hard drive partitions I only have 'Safely Remove Drive'
For my iPod touch I have 'Unmount'

That sounds fine to me

---

### Post by ranch hand on 2010-07-22
> **andrewabc said:**
> On ubuntu 9.10 for a usb I have
unmount
eject
safely remove drive

Is it the same on 10.10? That's a lot of options for dumb users. Eject sound like good one to get rid of. Safely remove drive is best sounding. unmount only makes sense if multiple partitions loaded on usb stick (or wanting to unmount to format it?).

When I turn on external esata 3.5" I only get unmount option. Which makes sense I guess since ubuntu only sees it as sata connection. And I have 2 partitions on the 1tb external.
The unmount option is missing.  This is a real bummer if you, for instance, have 20 partitions on an external usb HDD.

Unmounting the buggers one at a time with Disk Utility, which I really like for other jobs, truly sucks.

---

### Post by andrewabc on 2010-07-22
> **ranch hand said:**
> The unmount option is missing.  This is a real bummer if you, for instance, have 20 partitions on an external usb HDD.

Unmounting the buggers one at a time with Disk Utility, which I really like for other jobs, truly sucks.

Would gparted be faster for unmounting/mounting specific partitions?
Although if I remember correctly it has to refresh the list every time it does it (or maybe you can tell it to mount/unmount everything then 'apply' it).

---

### Post by mc4man on 2010-07-22
> Selecting safely remove does not work because it immediately remounts automatically and opens a nautilus window

Don't see that here at all, 2 installs with different  hardware.
Tried with 3 externals and a handful of various flash with varying fs's.
safely remove performs exactly as intended.

So there's something in common between you and at least VMC, (haven't seen any other direct y or n


Ot. - At this point the paring down of the context menu should have removed eject which is of no apparent value and left unmount which does have a little to offer for some.

---

### Post by ranch hand on 2010-07-23
> **andrewabc said:**
> Would gparted be faster for unmounting/mounting specific partitions?
Although if I remember correctly it has to refresh the list every time it does it (or maybe you can tell it to mount/unmount everything then 'apply' it).

I actually tried gparted and it does work but it is slower (for the reason you mention) than Disk Utility which is really a slick app and you do not have to give a password to unmount stuff with it.

---

### Post by Starks on 2010-07-23
I'm usually lazy and just pull out. It's dangerous, but I can't be bothered to choose either safe removal option.

---

### Post by hugmenot on 2010-07-23
> **Starks said:**
> I'm usually lazy and just pull out. It's dangerous, but I can't be bothered to choose either safe removal option.

That’s what she said.

---

### Post by ronacc on 2010-07-23
> **Starks said:**
> I'm usually lazy and just pull out. It's dangerous, but I can't be bothered to choose either safe removal option.

that can bite you . the safely remove options flush the buffers and complete any delayed writes , neglecting them can result in problems including data loss .

---

### Post by DanaG on 2010-07-24
> **ronacc said:**
> Selecting safely remove does not work because it immediately remounts automatically and opens a nautilus window."

Hmm, that sounds like what my external drive+enclosure used to do: when I did "Safely Remove" on Firewire or USB in Linux, or on eSATA in Windows (since Linux doesn't even try to comprehend eSATA as removable), the drive spun down and then immediately back up.  That turned out to be a firmware bug -- upgrading the enclosure's firmware fixed it.  Oddly enough, the bare drive (with power taken from elsewhere) did the same when SATA link went down: it spun down and then back up.

One example (from Windows): when I have my CD drive hooked up to eSATA, it offers both "Eject CD-ROM Drive (F:)", and "Safely Remove HL-DT-ST GSA-T50L Optical Drive".  The difference there is clear.

---

### Post by seeker5528 on 2010-07-24
The 'safely remove' thing works fine on the system I'm on at work with my flash drive. 

But I have this USB doohickey that has connetors for SATA, PATA for your desktop sized hard drives, and PATA for you Laptop sized hard drives. On the hard drive I typically use with this I have two partitions, so I thought I would see what happens when I chose the 'safely remove' option instead of 'unmount', looked like it was unmounting both the partitions, but soon the icons for them show right back up again.

Ubuntu is not functional on that system at the moment, since I ran the Ubuntu partition out of space and I haven't been too pressed to do anything about it, but Ubuntu is the only distribution on my second computer, so I will have to try it there later.

Later, Seeker

---

