---
title: "Banshee Media does not show cd"
date: 2011-01-14
forum: Multimedia Software
---

### Post by ukbeast on 2011-01-14
Hi I am running Ubuntu 10.10 Desktop and I have installed banshee media player version 1.80-2ubuntu1~maverick.

I have a netbook with a external DVD-RAM drive and Banshee does not recognise a CD in the drive.

Rhythmbox does and my pc can recognise cdda.

Please help.

BTW the CD support plugin is on;)

---

### Post by mc4man on 2011-01-14
I'm using natty (which has latest banshee), and don't have a netbook. I do however have external usb cd/dvd drives and it does appear that banshee will not recognize the drive.

Considering that in natty banshee has replaced rhythmbox as the default player you'd hope this is addressed.

Couldn't find an open bug on this (though there very well may be), so [filed one.]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/703007")
If it's answered at some point i'll post back

---

### Post by ukbeast on 2011-01-14
> **mc4man said:**
> I'm using natty (which has latest banshee), and don't have a netbook. I do however have external usb cd/dvd drives and it does appear that banshee will not recognize the drive.

Considering that in natty banshee has replaced rhythmbox as the default player you'd hope this is addressed.

Couldn't find an open bug on this (though there very well may be), so [filed one.]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/703007")
If it's answered at some point i'll post back

Thank you mate 
:P

---

### Post by ukbeast on 2011-01-14
> **mc4man said:**
> I'm using natty (which has latest banshee), and don't have a netbook. I do however have external usb cd/dvd drives and it does appear that banshee will not recognize the drive.

Considering that in natty banshee has replaced rhythmbox as the default player you'd hope this is addressed.

Couldn't find an open bug on this (though there very well may be), so [filed one.]("https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/703007")
If it's answered at some point i'll post back

Thank you mate 
:P

---

### Post by ukbeast on 2011-01-14
Thank you

---

### Post by mc4man on 2011-01-22
There has been a bit of response to your problem on the filed bug
[https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/703007](https://bugs.launchpad.net/ubuntu/+source/banshee/+bug/703007)

There may or may not be some use to additional hardware info and or debug from hardware other than mine. (only if requested.

If inclined or any one else with your need - playback w/ external drive, you may wish to keep an eye on and supply if needed

---

### Post by kakaw on 2011-06-03
Same problem here, but with Banshee 2.0.1 on Ubuntu 10.04 (EasyPeasy). I've added to the existing report at Launchpad.

---

### Post by mc4man on 2011-06-03
> **kakaw said:**
> Same problem here, but with Banshee 2.0.1 on Ubuntu 10.04 (EasyPeasy). I've added to the existing report at Launchpad.

You may want to add your drive info here and not hold your breath on this. Still see the same here on natty and probably the O release (11.10
[https://bugzilla.gnome.org/show_bug.cgi?id=640452](https://bugzilla.gnome.org/show_bug.cgi?id=640452)

To get relevant info go,(with drive attached - 
```
sudo lshw -C disk
```
Look for the *-cdrom  section

Edit - will test O tomorrow

---

### Post by kakaw on 2011-06-03
```
*-cdrom
       description: DVD-RAM writer
       product: CDDVDW SE-S204S
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: TS01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: status=ready
```

I'll add this to the bug report as well.

Good call on not holding my breath, though.  I'm 0 for 3 here: SoundJuicer recently stopped downloading any track info, and RubyRipper has a bug in 10.04 that causes it to rip impossibly slowly.  I only just discovered that Banshee was supposed to rip from CD also, which I thought would solve my problems... but then, this.  Can you recommend another CD ripper?

---

### Post by mc4man on 2011-06-03
> RubyRipper has a bug in 10.04
It's fairly simple to fix the slow RR rip (long pause between tracks)

I have a posted method for 10.10, for 10.04 only needs one small thing changed (name change of a build dep
(involves adding a ppa to get an alternative for ruby and building a new ruby-gtk, takes about 10 min. to do
If desired I'll link and edit to make that change for 10.04

Edit: just to note  - you can set RR up in the gui and then run from the cli - the bug is in ruby-gtk, not ruby
The old command for non-interactive is 
rrip_cli -a
For newer RR it's
rrip_cli -d

abcde also works great, though the RR gui fix really is quite simple - 

made an edit - this page, post 174
[http://ubuntuforums.org/showthread.php?t=799621&page=9](http://ubuntuforums.org/showthread.php?t=799621&page=9)
If inclined to try read carefully, quote boxes should match what you see - will be around later...

---

