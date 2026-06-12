---
title: "Encrypted DVDs play on 8.04 but not on 10.04"
date: 2010-11-06
forum: Multimedia Software
---

### Post by lungfish on 2010-11-06
OK, I know this question has been asked a million times already, but I haven't seen an answer for this exact problem, so I'm going to try again.

Before I get into the details:

[LIST]
[*][COLOR=Red]I have libdvdcss2 installed [COLOR=Black](it might not be working properly, but it is installed)[/COLOR]
[/COLOR]
[*]My DVD reader is set to region 2
[*]The DVDs I'm testing with are store-bought region 2 discs
[*]The test DVDs play fine on a standalone player and a Windows laptop
[/LIST]
Now the problem: This machine (a Dell T3400, very boring) was upgraded from Kubuntu 8.04.1 64-bit to Kubuntu 10.04 64-bit a couple of month ago.  Before the upgrade I was able to play and rip encrypted DVDs successfully using VLC and dvd::rip.  After the upgrade neither playing nor ripping works reliably.  *Some* DVDs will play in VLC, but a lot will stop halfway through or close to the end of a track.  I've not been able to rip any encrypted DVD at all.  Usually dvd::rip will get a failure when it runs lsdvd to read the DVD's table of contents.  If it gets past that it will inevitably freeze up part of the way through ripping a track.

I've booted the machine back into 8.04.1 64-bit from a USB key and verified that I can still play and rip DVDs that will not work in 10.04, so it doesn't seem like a hardware problem.  As I say above, the DVDs work fine in other players and machines.

The failures seem to be related to a libdvdcss seek error:
[FONT=Courier New]libdvdcss error: seek error
libdvdread: Can't seek to block 4072713
libdvdread: Invalid IFO for title 23 (VTS_23_0.IFO).
libdvdnav: ifoOpenVTSI failed
vlc: /build/buildd/libdvdnav-4.1.3/src/vm/vm.c:1485: process_command: Assertion `0' failed.
Aborted
[/FONT]The block number will be different with different discs/tracks but it's usually some variation on this.  I initially thought it might be this problem: [http://tobias.rautenkranz.ch/libdvdread_ifo.html.en](http://tobias.rautenkranz.ch/libdvdread_ifo.html.en), but that patch seems to have been merged in ages ago.

The attached logs show my attempts to run vlc, lsdvd and dvdbackup on both 8.04.1 (hardy.log) and 10.04 (lucid.log) with the same DVD ("The Shield", season 4 disc 3).  As you can see there are a lot of errors logged by libdvdread3 on 8.04.1, but it does work eventually.  No such luck on 10.04.

In case it matters, the DVD reader is one of these:
[FONT=Courier New]       description: DVD-RAM writer
       product: DVD+-RW AD-7200S
       vendor: Optiarc
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 101A
       serial: [Optiarc DVD+-RW AD-7200S101A Jan09,2008
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc

[/FONT]To me this feels like some kind of weird CSS decryption problem but I have no idea what to check next or how to go about fixing it.  The libdvdread seek error is mentioned in a few other posts but nobody seems to really know what causes it.

Any help or pointers will be greatly appreciated!

---

### Post by lungfish on 2010-11-06
Oops, apparently .log is not a permitted file extension!

The logs are attached to this reply, as "logs.tar.gz".

Apologies.

---

### Post by efflandt on 2010-11-06
AFTER you upgraded to 10.04 did you install ubuntu-restricted extras and follow instructions at [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) to make sure that is correct?

When I recently upgraded a system from 9.10 to 10.04, flashplugin-installer appeared to installed with the latest version, but did not show up in firefox Add-ons and did not work.  Also ubuntu-restricted-extras showed as not installed, but installing that did not restore flash.  I had to mark flashplugin-installer for Reinstall before it would work.

Many things have changed since 8.04, so it is possible that something is missing, incomplete, or wrong version after upgrading through two major versions.

---

### Post by lungfish on 2010-11-07
Yep, done all of that:

[FONT=Courier New](603) scott@phasmid:~/tmp $ dpkg -l | grep restricted
ii  kubuntu-restricted-extras            39                                              Commonly used restricted packages for Kubunt
[/FONT]
The "upgrade" to 10.04 was actually more of a "reinstall and restore my home directory from backups" kind of thing.  I get the same failures if I run as root, so I don't think the cause can be bad settings carried over from the old install.

Thanks.

---

### Post by mc4man on 2010-11-07
It's been mentioned that an Assertion `0' failure like yours  w/ vlc is a bug in libdvdnav/read4. If so it's a bit of a corner case, most don't have this problem.
I've only seen a couple of dvd's that failed to playback and those were due to a particular structure protection. As far as libdvdread/nav4 I've used it w/ no issue even back in hardy.

Can you get playback w/ a xine based player? They generally use a libdvdread/nav from xine-libs. Not sure what's avail. in kubuntu for dvd playback w/ navigation, maybe xine-ui?

Ex. from a totem-xine on maverick
"libdvdnav: Using dvdnav version 1.1.18.1 from [http://xine.sf.net](http://xine.sf.net)"

It could be interesting to see if taking the hardware (dvd drive & disk) out of the equation makes a difference with vlc.

To try then dump a dvd (the shield would be fine) to an encrypted .iso.
 dd would work but you may find dvdisaster to work faster and better.

To try - 
install dvdisaster
put a dvd in the drive, let a player open it even if it crashes. This will authenticate the the disk/drive. (otherwise dvdisaster will fail
Then pause or close the player if it didn't crash and  start dvdisaster, The drive to use is shown in left box, name of .iso in center, defaults to medium.iso saved to home folder. 
Click on the 'read' tab, the first time you'll get a popup as in screen. Check the box and click on the 'skip'

After .iso is hopefully produced try playing it in vlc. 
It could also be mounted and you could try ripping, I've found [CDEmu]("https://launchpad.net/~cdemu/+archive/ppa") to be the way to go there for ripping.

screen of dvdisaster in [this thread]("http://ubuntuforums.org/showthread.php?p=6139837#post6139837")

---

### Post by lungfish on 2010-11-07
Thanks for the replay - good questions and some really interesting results... I tried your suggestions (playback with Xine, copying with dvdisaster and playback from copied .iso) with three different discs:

1. The Shield, Season 4 Disc 3 (R2, encrypted)

[LIST]
[*]VLC: Failed
[*]Xine: Failed
[*]dvdisaster: Started hitting unreadable sectors around 2.5GB in, did not recover after 15 minutes.  Error message was: "Medium error; No seek complete; Skipping 15 sectors" repeated endlessly.
[/LIST]
2. Airplane (R2, encrypted)

[LIST]
[*]VLC: Failed
[*]Xine: Started to play, aborted before main feature start
[*]dvdisaster: Successfully copied to Airplane.iso
[*]VLC Airplane.iso: Played successfully
[/LIST]
 3. My sister's wedding video (R0, not encrypted)

[LIST]
[*]VLC: Failed
[*]Xine: Failed
[*]dvdisaster: Successfully copied to Wedding.iso
[*]VLC Wedding.iso: Played successfully
[/LIST]
I've attached logs from all three sets of tests.

I really don't know quite what to make of these results.  It seems that if I can successfully read the disc with dvdisaster then it will play (and presumably rip) with no problems.  I guess it's possible the "Shield" discs have some unusual copy protection that libdvdread/css2 can't handle.  But I just don't get why the unencrypted homemade disc would cause any problems.

Thanks.

---

### Post by lungfish on 2010-11-07
P.S. Tried another of the Shield discs from the same set just in case the first one really does have unreadable sectors.  Got the same failure at an earlier point in the disc.  Gave up after it had skipped 1000+ sectors.

---

### Post by mc4man on 2010-11-07
A few thoughts...
first, concerning The Shield
That's a sony release so if it has s.p. it would be sony's ARccOS which seems likely.
(didn't in R1, but R2 is treated more 'harshly'.

While no need to get into exactly how it works -  2 things - one element is usually a huge # of unreadable sectors (10000+), and the protection **is not** the type that should cause any playback/navigation issues.
K9copy can usually handle ARccOS quite easily, though with a 'tv series' you'd need to do a full disk w/ orig. menus. (k9 can be set to not transcode by setting the target size above disk size.

as to the other titles and overall

What's more interesting is that you're getting playback failure w/ both xine and vlc, (2 different dvdread/nav's), but after creating an .iso playback is ok.
The .iso from dvdisaster is exactly like the orig. disk minus the area holding the decryption keys.
This somewhat points to your drive being part of the problem, if it is not sure why.

(though I just replaced a drive yesterday w/ a 'new' plextor 712a I had never opened and it may be showing signs of an extreme corner case bug, I'll need to reboot to ck. out
All that indicates is there are certain hardware/ubuntu combos that can have issues almost no-one else does.
( the bug here may be the drive won't recognize dvd video  media after a reboot unless an audio cd is inserted/ejected first..

The failure to read a non-encrypted title is also a complication, otherwise I'd say delete the .dvdcss folder in your home folder and start fresh. (you can still try that, if so, then use xine first on any title.

A long shot would be totally removing libdvdread, nav, the .dvdcss folder, (losing some players) and then re- install the whole mess.

What happens with a movie (not a series), if you use the the 'no dvd menus' option in vlc.

It might be interesting to install a ppa mplayer w/ a frontend like smplayer and see what happens - dvdnav in mplayer is possible but I'd try on a movie title. (mplayer has it's own version of dvdread/nav4
A good mplayer ppa
[https://launchpad.net/~motumedia/+archive/mplayer-daily](https://launchpad.net/~motumedia/+archive/mplayer-daily)

I'll look thru your logs this evening, maybe something is there..

Is there another drive available to test w/ on this box, either internal or external?

---

### Post by lungfish on 2010-11-08
First of all - many thanks for all your help so far, I really do appreciate it.

It might take a couple of days to get through them all but I will try your suggestions and report back.  So I will try:

[LIST=1]
[*]Ripping the discs with k9copy
[*]VLC with the "no DVD menus" option
[*]Nuking ~/.dvdcss directory and trying again (have already tried this but I should be a bit more methodical about it)
[*]Nuking dvdread, dvdnav, dvdcss2, all the players, reinstall everything and try again (Again I have already tried this once but another attempt won't hurt)
[*]mplayer from a PPA
[*]A different drive (if all else fails I can pull the LG drive out of my server box although that would require shutting it down first!)
[/LIST]
I agree that it does look like the hardware is somehow involved.  Which makes it even weirder that this stuff all worked on an earlier version.

---

### Post by mc4man on 2010-11-08
> like the hardware is somehow involved. Which makes it even weirder that this stuff all worked on an earlier version.
It certainly seems it can happen  - the combo of a ubuntu release and specific hardware.

So for ex. I rebooted to ck. this new plextor drive on a maverick install.

In this case commercial dvds absolutely are not recognised from a fresh boot.
Data and ripped dvds are found and mounted, w/ the comm. ones nothing, even dmesg shows nothing.
In computer, as soon as the drive settles after inserting a comm.dvd the icon disappears.

The dvd can be played back in an unmounted state from players though navigation is spotty. Even after playback there is no sign of the drive or the udf filesystem anywhere, not in /media/, not in lshw, not in computer.

The 'fix' - insert an audio cd, let it get recognised, then eject. After that comm. dvd's are found and mounted fine till a reboot. While there is a clue there somewhere it's still non-sense.

At the same time booting to a lucid or karmic install everything works fine, I'm 90% sure if I was to do a reinstall of maverick then it would work fine, probably will try.

All this goes to show is that odd. corner case behaviour based on hardware is quite possible.

---

### Post by mc4man on 2010-11-09
> I'm 90% sure if I was to do a reinstall of maverick then it would work fine, probably will try.
Well a fresh install of maverick and no go. With an obviously good dvd drive (the plextor 712a), the udf filesystem on   css encrypted disks will not be detected or auto mount. (seen as an 'empty' disk, no filesystem found

Once an audio cd is inserted/ejected then they will mount properly.
So clearly odd behavior can occur dependent on hardware/ubuntu release.

---

### Post by lungfish on 2010-11-09
OK, some interesting results from my experiments today.

I accidentally booted the machine with one of the Shield discs in the drive.  I had already installed k9copy and deleted the ~/.dvdcss directory before I noticed this.

After that, almost everything suddenly started working: I could play with vlc (with and without menus), xine and mplayer, and rip with k9copy.  lsdvd and thus dvd::rip still didn't work.  Same behaviour for other discs from the same set.  For other discs without the extra Sony copy protection, everything including dvd::rip was now working.

Rebooting again with a non-Sony disc in the drive, again I had complete success with all non-Sony discs, but anything that tried to scan the TOC (lsdvd, dvdbackup, k9copy) would fail.

I'm still going to try reinstalling all the players and DVD reading/navigation libraries, so at least I know exactly what I have installed.  However it looks like I at least have a workaround, if not a real solution, or an answer to why the problem happens at all.  Will also try a different drive when I can, although it might take a while to get that test done.

I guess I'd agree with you that there seems to be some weird corner case related to my particular hardware, probably together with some bugs in libdvd{read,nav}4 in this version of Ubuntu.

Thanks again.

---

### Post by henrywm on 2010-12-04
My laptop with Ubuntu 10.10 will not even detect DVDs. I have ubuntu-restricted-extras, libdvdcss2, and libdvdread4 installed.

---

