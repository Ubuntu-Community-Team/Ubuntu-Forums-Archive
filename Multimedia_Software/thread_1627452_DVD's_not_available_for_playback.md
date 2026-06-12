---
title: "DVD's not available for playback"
date: 2010-11-21
forum: Multimedia Software
---

### Post by Fixitall on 2010-11-21
Hi all.

Need some help on this one.

Problem:
DVD drive is detected by BIOS and Ubuntu 10.10
Ubuntu 10.10 was installed from scratch using a DVD RW for installation
Everything works OK
When trying to use the DVD for normal playback of DVD's with a movie on  it (legal ones), the DVD is not recognized, not mounted, etc. 
When browsing with VLC for a disc to play it there is nothing showing up, nor in the 'places' menu.
When using Brasero, disc copy, it states 'no disc avaialble.

Hardware / SW:
Ubuntu 10.10
TSST SH-S182M IDE
WD EARS 1,5 TB SATA
See attached picture.
The firmware version on the DVD is v05. I tried to install the V06 but was not succesful. Seems the one click installer is only written for Windows?

Any suggestions where to start? I am not very experienced with ubuntu but average on computers in general.

Any help is much appreciated.

---

### Post by SirGrant on 2010-11-21
To enable DVD playback you need to install libdvdcss.  You can install it by running this command at your terminal.

sudo /usr/share/doc/libdvdread4/install-css.sh

Be aware depending on the laws where you live installing libdvdcss may or may not be illegal.

---

### Post by Fixitall on 2010-11-21
Yes, already did that after reading some posts. But still no luck. 
Tried your command just in case but by what it says in the terminal, the file is already installed.

I am sure it is a security problem because I found one that plays.

Most of them just don't play or are selectable in VLC player

Is there a way to check what is actually installed and compare it to what should be installed?

Thanks.

---

### Post by mc4man on 2010-11-21
Out of curiosity - if you go to places -> computer and then insert an encrypted dvd movie - does the drive icon disappear?

---

### Post by deanjm1963 on 2010-11-22
Is libdvdread4 & libdvdnav4 also installed as well as libdvdcss2? You also need those files.

---

### Post by Fixitall on 2010-11-22
[deanjm1963]("http://ubuntuforums.org/member.php?u=85163"):
Yep, all packages are installed, see screenshot.

[mc4man]("http://ubuntuforums.org/member.php?u=320715"):
Well, not exactly. In places/computer there is no DVD player unless it is one with recognizable (=not encrypted?) data. Then it is mounted. I am not sure if that behavior is normal. (see screenshot)

So I tried all hints and tips that I could find but still no success. Anyone?

---

### Post by deanjm1963 on 2010-11-22
It seems like ubuntu "recognizes" your dvd drive, but at the same time it doesn't. This might be a long shot, but what kind of motherboard/cpu do you have. Can you enter the bios and see how your dvd is configured? I know it's IDE, but are there options, e.g. [Auto] [CROM] or [ARMD] - if you have an option to set it to [ARMD] (ATAPI Removable Media Device) try that, if it's already set to that, try changing it to [Auto]. You seem to have all the right software installed etc.

---

### Post by mc4man on 2010-11-22
I would check in your bios as mentioned above, also you could try booting w/ a commercial dvd in the drive and see what happens.
While it shouldn't make any difference you could try creating a static mountpoint (the previously typical /media/cdrom0) and adding an fstab entry (if so and unsure of proper entry just ask.

Unfortunately there seems to be quite a number of corner case bugs in this area, starting with karmic. I'd say the main cause is specific hardware in combo with the ubuntu release and kernel being used.
This leads to many variations of mis-behavior and any number of possible solutions, workarounds, or possibly none at all.

To note a few things - 
when you go to places -> computer you should see the drive or drives if more than one, whether or not media is inserted or not.
Drives don't get mounted, only the filesystem on inserted media (exception being audio cd's which have no filesystem and are accessed from a location/device. You should 'see' audio cd's in ~/.gvfs/cdda mount on /dev/XXX

In some of these mis-behaviors dvd's can still be played even though no filesystem is reported as mounted - try from terminal
vlc dvd://

---

### Post by Fixitall on 2010-11-24
Deanjm / mc4man
 
Thanks for your replies.
 
I will try your suggestions in the BIOS tonight although I have been in there several times without seeing something obvious.
 
I noticed that the DVD player is recognized in Places and shows up under computer if it is booted without a disc. When booted with a protected disc it will not show up (see previous screen shot). I am not sure if it will actually dissapear when I insert a protected DVD after booting up. Will try that tonight.
 
I will also post my configuration MB, CPU.
 
Anything else I should collect?
 
Thanks.

---

### Post by mc4man on 2010-11-24
> I noticed that the DVD player is recognized in Places and shows up under computer if it is booted without a disc. When booted with a protected disc it will not show up

Atm I have trouble with 1 specific dvd drive and in this case only in maverick. The drive is a 'new' plextor 712a (never opened from a batch of plextors and benq's I bought several years ago

The drive works perfectly with all media except commercial (encrypted) dvd movies. In that case, when a dvd movie is inserted,  - the drive disappears, no icon on desktop and sudo lshw -C disk, while still showing the drive, reports no mounted filesystem.
(I can however play the movie thru vlc (which is set to use the device - /dev/sr0) from command line as noted previously.

The 'fix' - (which borders on pure non-sense
Inserting an audio cd, removing the audio cd. Then the plextor acts as 'normal' for the life of the session. A reboot will cause the misbehavior to begin again until an audio cd is again inserted and removed (and only an audio cd will work to make comm. dvd media mount and the drive be seen. (by 'seen' mean in places/computer and dvd movie icon on desktop

You could try this though this may be just peculiar to certain plextor and ubuntu/kernel combo's (on same machine when booting to lucid the plextor is fine

---

### Post by Fixitall on 2010-11-24
Ok,

My configuration:
Processor P4 2.8 Ghz
MB: Asrock P4i65G

Next, I went into the BIOS.

My DVD was detected as:
Device: ATAPI CDROM
Vendor: TSST Corp CD/DVDW SH-S182M
LBA: Supported
PIO mode: 4

The type selection was configured to 'auto', so I put it on ARMD as suggested. During re-boot this causes the following error:secondary master drive: ATAPI incompatible.

So, I guess it doesn't like that:D. Put it back to CD/DVD

Booting without a disc makes it available in Places /computer.

When inserting a protected  DVD, it doesn't do a thing. It shows' unknown volume' see attachment.

When trying to play it anyway via the command line, it fails too. See other attachment.

When I insert a (protected) audio CD, everything works as it should. See other attachment.

Trying the DVD again, no luck. Unknown volume.

So, am I having one of those specific hardware combination bugs? It feels like it. I could try another DVD player although this is my newest one, not used much:(

Anyone more ideas?

---

### Post by mc4man on 2010-11-24
> I having one of those specific hardware combination bugs?
Most likely. You may stumble upon a solution, like I did with the plextor which first happened 3 years ago w/ a plextor 708 on fiesty
([was my first post]("http://ubuntuforums.org/showthread.php?t=551147"), nobody knew anything, I happened to 'fix' it by accident. Then one day, (possibly gutsy), it just started working right and I've had no issues with any dvd drive till I threw that new 712 in on maverick.

So an update or upgrade may also resolve or it may never get better.
While it shouldn't matter you could try adding a mount point and fstab entry. If unsure then run this and post the -*cdrom section
```
sudo lshw -C disk
```

---

