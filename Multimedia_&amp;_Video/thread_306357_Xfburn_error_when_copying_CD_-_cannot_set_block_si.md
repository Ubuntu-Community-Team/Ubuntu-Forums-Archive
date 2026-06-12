---
title: "Xfburn error when copying CD - cannot set block size"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by vodsonic on 2006-11-24
I just installed Xubuntu 6.10 (Edgy Eft) on my old Dell notebook. The new OS is pleasingly fast, and looks great.

However, I ran into a problem when I tried to copy a data CD with Xfburn. This computer copied and burned CDs just fine in the past with k3b under SuSE Linux, and Roxio and Nero under Windows XP.

Within about 30 seconds of starting the copy process in xfburn, it gave back an error message in the output. 

```
ERROR: Cannot set block size.
WARNING: Padding with 358923 zero sectors.
ERROR: Cannot set block size.
Please insert a recordable medium and hit enter.
```

At this point xfburn pops up a window requesting that I 'Please insert a recordable medium and hit enter.' There is an 'OK' button but no option to cancel. But there has clearly not been time for the program to read a 600+ MB disc.

If I hit OK with or without removing the CD I was trying to read from, the same window asking for a recordable medium comes right back. I didn't kill Xfburn at this point (although I think I could figure out a way to do so if need be) - I just shut down Xubuntu.

I understand that Xfburn is a frontend for cdrtools (cdrecord, cdrdao, mkisofs, and maybe readcd). I googled the following phrases, but the only hit I found that appears to be in some way relevant happens to be in German.

'cdrtools cannot set block size'
'cdrecord cannot set block size'
'cdrdao cannot set block size'
'readcd cannot set block size'
'mkisofs cannot set block size'

Does anyone have any ideas how to fix this and proceed with burning CDs on my Xubuntu desktop?

---------------

This is my first post on the Ubuntu forums. I began my journey with Linux some years ago when I tore my hair out trying to install Debian on this same Dell laptop. Then I tried Ubuntu, and it worked beautifully. Unfortunately, I was dual booting with a certain bloated, crufty OS that will here go unnamed. When said crufty OS got too gummed up, as it inevitably does sooner or later, I reinstalled it. This killed GRUB and locked me out of my Ubuntu install (have since learned how to fix this). 

After a couple of years and several crashed hard drives, I got fed up again with the cruft and the bloat and again returned to Linux. Have been using a major .rpm-compatible distro since it plays well with my USB wifi card, but it's a bit big and commercial, too. I've tried to move in the direction of simpler, faster distributions, and Puppy Linux is a big favorite. 

I was thrilled when I heard about Xubuntu recently - now we have a sleek and stripped down OS backed by the Ubuntu community and package repositories.

---

### Post by vodsonic on 2006-11-25
I did some more looking around, and while I didn't find anything that directly addressed the problem I detailed in the first post, I did find a post in another thread that seemed relevant: 
[B]
xfburn won't burn image[/B]
[http://ubuntuforums.org/showthread.php?p=1795017](http://ubuntuforums.org/showthread.php?p=1795017)

A reply in that thread claims that xfburn in Edgy is "screwed", and recommends downgrading to the Dapper version of xfburn. I downloaded the .deb package for xfburn/Dapper as linked from that thread.

However, when I opened up Synaptic and marked xfburn for removal, I was immediately warned that:

```
The chosen action also affects other packages. The following changes are required in order to proceed.
To be removed:
	xubuntu-desktop
```
	
Surely I can't remove that - that's what makes it Xubuntu, right? I'm not even sure that the desktop will load without that package.

I'm just trying to uninstall a single app, not the whole desktop. :-k

---

### Post by vodsonic on 2006-11-29
Hmmm...

I installed k3b on my system and it copies discs without any problems.

Going back to xfburn, I started it from a terminal, which then outputs this: 

```
user@linux:~$ xfburn
** Message: No existing settings file, using default settings
** Message: Using Thunar-VFS 0.3.3
** Message: looking for device [1]
** Message: device [1] found : SD-R2102 (/dev/hdb)
** Message: device [1] capabilities : CD-R CD-RW
** Message: looking for device [2]
** Message: Requested device index [2] is out of bounds. All devices have been read.
```

Then the GUI loads. When I try to copy a CD to make a backup, the output looks like this [cd track information edited down to save space]:

```
Cdrdao version 1.2.1 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

Using libscg version 'ubuntu-0.8ubuntu1'

/dev/hdb: TOSHIBA DVD-ROM SD-R2102	Rev: 1A15
Using driver: Toshiba CD-ROM Reader - Version 0.1 (options 0x10000)

Starting CD copy at speed 0...

Track   Mode    Flags  Start                Length
------------------------------------------------------------
 1      AUDIO   0      00:01:00(    75)     03:18:01( 15269)
## etc. etc.
13      AUDIO   0      59:12:24(270043)     05:31:70( 25414)
Leadout AUDIO   0      64:53:24(290475)

Copying audio tracks 1-13: start 00:00:00, length 65:53:24 to "/tmp/xfburn.bin"...
Analyzing...
Track 1...
Track 2...
Track 3...
Track 4...
Track 5...
Track 6...
Track 7...
Found pre-gap: 00:03:13
Track 8...
Track 9...
Track 10...
Track 11...
Track 12...
Track 13...
Found pre-gap: 00:03:18
Reading...
Track 1...
ERROR: Cannot set block size.
ERROR: Cannot set block size.
ERROR: Cannot set block size.
ERROR: Cannot set block size.
ERROR: Cannot set block size.
ERROR: Cannot set block size.
ERROR: Cannot set block size.
ERROR: Cannot set block size.
```

And it continues outputting new "ERROR: Cannot set block size." lines until I hit the stop button.

So it does seem to be a problem with cdrdao. I would guess that k3b is also using cdrdao under the hood, but I'm not sure. 

Aparently this is not a very common problem, since googling "xfburn cannot set block size" or even "cdrdao cannot set block size" finds nothing relevant.

k3b is fine, but I would rather use the smaller xfburn that is integrated into Xubuntu. Any suggestions?

---

### Post by vodsonic on 2006-12-18
***BUMP***

](*,) ](*,) ](*,) ](*,) ](*,) 

Hmm. I haven't been able to solve this one with man cdrdao or google. I tried to find out who develops xfburn to contact them directly, and it seems it's a part of xfce, so I also posted about this problem on the xfce forum. No replies yet.

[SIZE="4"][COLOR="Red"]Is anybody else experiencing this problem?[/COLOR][/SIZE]
[SIZE="4"][COLOR="Navy"]If so, please reply here, and maybe we can put our heads together and get it solved.[/COLOR][/SIZE]

---

### Post by vodsonic on 2006-12-19
I contacted the author of xfburn to see if he had any suggestions. He was kind enough to respond, and while he did not offer any imminent solutions, he pointed out a couple of things.

1. xfburn and k3b both use cdrecord to burn discs, but it is possible that k3b utilizes some other options that xfburn doesn't, hence the difference.

2. In future releases, xfburn will most likely utilize libburnia instead of cdrecord.

This may be as far as I go with xfburn for now, but I'm looking forward to the next release.

And, unless anyone else has anything to add, here ends the One Man Thread!

---

