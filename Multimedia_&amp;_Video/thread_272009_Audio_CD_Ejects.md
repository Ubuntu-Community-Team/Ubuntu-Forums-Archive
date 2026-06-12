---
title: "Audio CD Ejects"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by almal on 2006-10-05
I'm having a problem playing audio CDs on both CDROM and CDRW. I have tried using both CD players with Sound Juicer and Rhythmbox to play audio CDs. In all cases, the song will play for a 10-15 seconds and the CD will eject. The same thing happens when attempting to extract a song with Sound Juicer.

Any help would be appreciated.

Thanks

---

### Post by almal on 2006-10-23
Seems this was a HW problem. I installed a new CD drive and it works fine.

---

### Post by sedstevo on 2006-11-27
I have this issue too  :-k 
My CD drive is an FX4010M.  Soundjuicer reads the disc OK, displays the contents and then ejects.

Are there other CD ripper tools I can install?

---

### Post by cmh on 2006-12-19
I'm having the same problem.  Either listening to or ripping a disc with Grip, it'll go for a while, then eject.  During the ripping process, it'll spin down, and eject.  If I push it back in, it will spin back up and resume right where it left off.  Listening to the resulting WAV file, doesn't seem to be any skips where it ejected.  (that's pretty impressive, but more impressive would be not having to deal with unexpected ejects!)

It's not a hardware issue... this system is dual-boot with Windows 2000 and has ripped MANY discs using Audiograbber with no problems at all.

Update:  CD is sitting in the drive, completely inactive, and just ejected.  I wasn't doing anything with Grip.  Looked at the Grip status window, no errors or messages about ejecting except the final one at the end of the rip.

---

### Post by msjulie on 2007-01-02
Hello All,

I too am having frequent and random ejects of Audio CDs.  I have an old HP 8565C Pavilion.

relevant output from **lshw**
```
              *-cdrom:0
                   product: Hewlett-Packard CD-Writer Plus 8000
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   capabilities: packet
              *-cdrom:1
                   product: FX4821T
                   physical id: 1
                   bus info: ide@1.1
                   logical name: /dev/hdd
                   capabilities: packet
```

I've read various related threads, and saw no need to start another.  Unfortunately, I saw no solutions to the problem in any of them.

Maybe, someone could step up to the plate.  I struggled to get sound up--stupidity on my part, but it now works; I worked very hard to get wireless networking up--got it too; found a work around for distorted audio CD...

**but I really need some help on this one.**

What other information would be helpful in solving this?

Julie

---

### Post by msjulie on 2007-01-02
Hello All,

Still no luck in solving my audio CD eject problem.

I searched gnome bugzilla for gstreamer bugs and didn't find anything there.

I yahooed a bunch of stuff and didn't get anything real useful except:

Audio CD's are **not** mounted since they don't have a file system.  They are directly read,

I'm thinking this might be a clue as to why only my audio CD are randomly ejecting, since they are not mounted like data CDs.  I'm imagining that this could be a gnome / ubuntu issue.

When I insert the CD, Sound Juicer opens, an icon appears on the desktop with the description 'Audio Disc'

It also ejects randomly even if not playing, about three times during the writing of this post.

Any thoughts?

I'll keep hunting, though.

Julie

---

### Post by zspdude on 2007-01-05
I´m also having the same problem on a HP Pavilion XE734. Seconds after a disc is inserted (audio OR data) it ejects. The drive in question is a Mitsumi CR-4804TE.

The lshw info:

*-cdrom
                   description: CD-R/CD-RW writer
                   product: CR-4804TE
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 2.6C
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc

The drive reads and writes perfectly under Windows 98SE. It also functions perfectly under SuSE 10.0. (Which I removed to try out Edgy)  The lens has been freshly cleaned.


Here´s what I´ve observed with Data CDs (if you don´t want details skip to  ¨The Bottom Line¨:
When I insert a Data (mountable) disc, the KDE Daemon prompt appears (as expected) to ask what I wish to do (mount it/ignore it/whatever). By the time I can choose an action the disc simply ejects and I´m forced to close the prompt and do this again. If I´m quick in chosing an option (it doesn´t matter which) the disc pops out anyway.
If I´m quick and I mount it manually from the terminal right after I insert it (´mount /media/cdrom0´) it still ejects if I then close the KDE Daemon and wait a couple seconds. (I assume the Daemon umounts it)
However, if I prevent the disc from being umounted by accessing it ...

mount /media/cdrom0
cd /media/cdrom0

...the disc doesn´t eject (I´d say obviously - but nothing is obvious anymore).
As long as I can keep the disc mounted it´s perfectly happy to stay in (obviously). As soon as I manually umount the disc, it ejects.



The bottom line - if an unmounted data disc is in my drive it gets ejected within a few seconds. As long as I can keep it mounted it remains.

Here´s what I´ve observed for Audio CDs: 
If I insert an Audio CD in the drive it ejects within a few seconds. I´ve been able to play perhaps the first second or so of an audio disc in KsCD, but generally the disc is ejected before a player application has time to start up.

Sadly I have no answer for this problem -but  hopefully this might provide a bit more of a perspective. I´m not sure if we share the same issue, but I think it likely that we do.

I don´t think the drive is defective issue as the drive runs flawlessly in Windows and SuSE. Whenever I have it mounted in Kubuntu it r/ws perfectly. Perhaps Debian doesn´t like this drive (or HP in general) though? Someone else has the same problem with the same kind of drive - [http://ubuntuforums.org/showthread.php?t=231805](http://ubuntuforums.org/showthread.php?t=231805)

I don´t think it´s a user level application issue because regardless of whether or not I run grip/kscd/whatever, ANY disc put into my drive (even a blank) gets ejected unless I manage to mount it. In most cases these applications don´t even have a chance to run - the disc is ejected before they´ve started up.

msjulie - you might be right that it´s a gnome issue - although I´m running kubuntu I have most gnome packages installed (enough libraries to run grip anyway - which should include most of the packages relevant to the problem).
 
I might do some further testing on this. I´m reluctant to do a fresh re-install just to see how the drive functions on a  bare bones KDE system, however.

Any thoughts?

-- Scott

---

### Post by theWrkncacnter on 2007-01-05
I also had this problem on an old gateway computer, and could never fix it. The only solution was to build a new computer. I doubt that it's a hardware problem though, because the drive worked properly when installing ubuntu, and worked with win98se, as zspdude said. However, my computer did not eject the disk immediately if I just put it in and left it alone. With sound juicer, or any other media player, it worked for about 30 seconds. If I double clicked on it, it might eject. If I ignore my computer completely, the disk might stay in there for an hour or two, and then eject. I have no idea why this happened, but it was a pretty old and outdated (read only) drive anyway .
> : - (

---

### Post by msjulie on 2007-01-06
Hello all,

Thanks for your input.

I'm really believing this is a software bug.

My issues are more like yours theWrkncacnter.  I can let the disk sit idle without an application and it might eject it 10 seconds later or a couple hours later.

Here is what I found In [Ubuntu Malone]("https://bugs.launchpad.net/ubuntu/+bugs"):
[edgy Sound-Juicer ejects musik-cd]("https://launchpad.net/ubuntu/+source/sound-juicer/+bug/76817") (not much there)

[Apple media keyboard eject key only opens cd tray, doesn't close it]("https://launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/37785")

Basically, it appears to be a gnome-volume manager issue, but I didn't find much in [gnome bugzilla]("http://bugzilla.gnome.org/").

I might have to file a bug report somewhere, but I'm not certain where.  I debating if I have the time this week to deal with it.  I might put it off until things are calmer here.

Julie

---

### Post by zspdude on 2007-01-06
I don´t have gnome-volume-manager installed so that´s obviously not what´s causing my hassles. :( 

The kicker for me is that if I only login in using a shell (Cntrl-Alt-F1-6) I have no problems with either audio or data cds at all. I can mount/umount to my heart´s content, and audio cds stay in the drive. They also play  correctly via cdcd. 

This tells me there´s definitely a software bug out there. However almal´s comments (and the fact that this is not a widespread problem) seem to point to a hardware specific software bug.
I also find it oddly coincidental that we´re both running older HP Pavilions and that someone else with the same model drive as I have experienced the exact same problems. msjulie - which drive are you having problems with? I´m curious because the FX4821T is also a Mitsumi drive.

I smell a rat.

-- Scott

---

### Post by msjulie on 2007-01-06
Hello Scott

I have two drives:
Hewlett-Packard CD-Writer Plus 8000
FX4821T

Sorry I don't have more for the second drive.  There is no other labeling on it.

I just put a data CD in.  I closed Nautilus.  Eventually the Data CD just popped back out by itself.  A notification appeared that I just unsafely removed the media.  Odd.  Maybe this isn't just an Audio CD thing.

I believe the gnome-volume manager is a package of routines such as the *eject* command.  That is why I'm thinking it is there.   I believe gnome-volume manager also handles CD ROM mounting and unmounting.

I'm guessing my drives are receiving eject commands from one of the routines.  I can't think of another culprit.

When I get some time I might start the triage for this, but I haven't committed to it yet.

Any thoughts on your end.

Julie

---

### Post by Gremlinzzz on 2007-01-06
eject

eject [options] [device]

Eject removable media such as a CD-ROM, floppy, tape, or JAZ or ZIP disk. You may name the device by its /dev or /mnt filename. The /dev and /mnt prefixes are optional for any items in the /dev and /mnt directories. If no device is named, it is assumed that "cdrom" should be ejected      [http://www.oreillynet.com/linux/cmd/cmd.csp?path=e/eject](http://www.oreillynet.com/linux/cmd/cmd.csp?path=e/eject)

---

### Post by zspdude on 2007-01-06
msjulie - you´re no doubt familiar with the gnome-volume-manager bug already registered here...
[https://launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/47516](https://launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/47516)

(The bug report describes the exact same problem I am experiencing - with the exact same drive model as I have - He calls it a Matsusushi but I´m positive he means Mitsumi since it´s a CR-4804TE, and googling Matsusushi gives nada (except maybe this post - and his))

At the same time, I think this bug is mis-attributed to g-v-m - I don´t think gnome-volume-manager is really to blame. There´s a few reasons for this:

1) G-v-m is not even installed on my machine - (I´m running KDE, albeit with some gnome libraries installed).

2)My understanding is that g-v-m **merely handles requests** to eject the drive - and is actually working correctly.

Here´s what I think is happening (for data cds). The daemon will be the KDE Daemon (in my case) or g-v-m (in yours): 

- Disc is inserted
- Daemon automounts disc (correctly)
- For some inexplicable and obviously bug related reason a request is generated (from where???) to eject the drive
- Daemon is asked to umount the disc so that the disc can be ejected
- Daemon umounts the drive correctly (if nothing is directly hogging it) and hey presto!  The disc is ejected.

If I quickly mount a disc via xterm and actually access it the KDE Daemon can´t umount it (because the xterm is accessing it) - and the disc stays in. If I mount it ** but don´t access it** the Daemon is able to umount it (and does so) - and the disc ejects.

My point is that I can´t see anything that indicates that my KDE daemon is misbehaving - the mounting/umounting behaviour is rational and seems to operate correctly. 

For audio CDs - since they can´t be mounted/locked anyway the disc just gets ejected.

3)The only documented drives experiencing this problem seem to be Mitsumi drives (Or perhaps HP boxes) . If the problem were not hardware specific we´d find *way* more forum threads on it ;).

So the bug lies in software loaded when X/Gnome/KDE starts - but it´s low level enough to care what kind of drive it´s abusing.

I don´t think g-v-m handles any hardware details - my guess is hal is the culprit. (I could be wrong on this - I´m currently doing a bit of reading to figure out how the whole process works). But g-v-m shouldn´t care who made a drive - that should be hidden a good deal further down the software chain.
In addition, the fact that g-v-m is at version 1.0.2 or thereabouts and hal lurks at around 0.5.7 hints at relative maturity. (It´s a grossly subjective measure but hal *is* pretty raw).

BTW - The fact that I don´t have it installed is enough to convince me absolutely that g-v-m is not the culprit ;)

-- Scott

P.S. Here are a couple links I´m following up on as I suspect they´re relevant.
[http://www.mythic-beasts.com/~mark/random/hal/](http://www.mythic-beasts.com/~mark/random/hal/)
[http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co#ov_hal_linux26](http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co#ov_hal_linux26)

P.P.S. (Apologies for the lengthy posts... I tend to think with my keyboard ;))

---

### Post by msjulie on 2007-01-06
Hello All,
[B]
Gremlinzzz:[/B]
I read through man eject, but I don't think it is going to help...or am I missing something?
[B]
zspdude:[/B]
Looking at HAL also makes sense.  I can see why your thinking HAL might be the cause and not g-v-m.  Your right, g-v-m or KDE may just be acting--properly--to commands from elsewhere.

Oh, and no, I wasn't aware of that bug report.  I didn't see a resolution to it either.  The last comment was that it was going to get looked into.  If your right scott, and it is a HAL issue, the search in g-m-v would have been for naught.

Well, I do need to get on with the night.

I'll give this all some more thought.

Julie

---

### Post by zspdude on 2007-01-07
I have a sneaking suspicion that Gremlinzzz believes this to be yet another ¨I can´t get my cd eject button to work in Ubuntu¨ thread.

His comment is enlightening in that context - yet ultimately proves to be merely ironic. :D

I am now supremely confident that hal package is to blame - when i remove it (¨sudo aptitude remove hal¨)
...TA DA! My cd stays in the drive. 

On KDE this completely cripples the automounting system but I can manually mount data cds and I can play audio cds, all as normal and without issues. I´m not sure what gnome dependencies exist so this may or may not be a viable solution for you, Julie.

It´s certainly not preferable - perhaps tomorrow I´ll try installing whatever version of hal was running with SuSE... if I can. Hey, it worked with SuSE, but I have to consider it a long shot (and a poor solution).

I also might do some more playing around and submit a hal bug report. But not tonight.

--Scott

P.S. With a name like HAL I should have guessed :P

---

### Post by msjulie on 2007-01-07
Hello Scott,

I'd like to try removing hal as well, but my limited knowledge is keeping me back.

First, when I type 'sudo aptitude remove hal'

It tells me there are about 6 different packages that will be broken.  So I didn't do it.
So if I go ahead and remove hal.  Will 'sudo aptitude install hal' fix everything that is 'broken' or do I have to do something else to fix the damage.

Second, after I remove hal, how would I gain access to the CD drive?  what commands would I issue?

I'd like to try, but I really, don't want a broken system right now.

Yes, my ignorance is showing.  Sorry.

Julie

---

### Post by zspdude on 2007-01-07
First of all, you don´t have to apologize for not knowing something - we´re all guilty of that ;)

Secondly - this post is obscenely long and if you just want the beautifully optimal solution I´ve discovered just go the bottom - where it says the beautifully optimal solution.

To quickly answer your questions....

** First **
I also had to remove five or six packages when I removed hal. Because I was also concerned about keeping a functional system, I googled each package individually to see what it did. In my case they were all fairly trivial packages that weren´t  crucial to any important system function.
For the record, they were:

hwdb-client-common
hwdb-client-kde
kde-guidance-powermanager
kubuntu-desktop
ttf-kochi-gothic

The good news is that aptitude is smart enough, when removing a package, to recursively find all packages that depend on it, directly or indirectly. For example ttf-kochi-gothic doesn´t actually depend on hal, but it is used only by kubuntu-desktop. Removing k-d would leave it unused and so it is removed.

Since aptitude checks not only packages that directly depend on hal, but also packages that depend on **those**, etc, etc, when it says that you need to remove six packages, you can be sure you need to remove only those six.(It´s already checked those six to make sure nothing depends on them.)

Unless aptitude tells you that you´re removing half your system, you´re not going to wind up removing half your system. And if you check to make sure that there´s nothing really important being removed, you´re safe.

When you type in ´sudo aptitude install hal´ right after removing hal, it only re-installs hal, not the others.. At first glance this stinks but on second glance it´s not so terrible. Why?
Because aptitude is also smart enough to automatically install all the packages that a package to be installed depends on, or needs. If you use this correctly it can save you great gobs of time.

For example, the worst case scenario would be if you wrote down all the package names that you had been required to remove, and reinstalled them one by one. In this case it´s not a great hardship because there´s only a few. 

But even if there were many you could make it easy by installing the ´neediest´ packages first. For example, I got lucky. When I re-installed hal during my testing, I only had to run ´sudo aptitude install kubuntu-desktop´.
k-d is an incredibly needy package - it actually depends on all the other packages that were also removed when I removed hal. So aptitude automatically installed them when I installed it. If you google the packages you remove and take a look at what packages they depend on, you can restore your system with very little work. So don´t be fearful on that account.

But you shouldn´t be removing hal anyway - more on that later. See the very bottom of my post if you don´t want an overview of mounting in Linux.

But first,

**Second**
(Apologies if you already know this and were looking for more detail - this is a brief very incomplete overview)

To manually mount, the mount/umount commands are used. (The lack of an ´n´ in umount is not a typo)

**Mounting/Umounting - Theory**
Mounting from the command line dates back to the stone age. It´s crude but effective.
In Linux, any device (whether removable or not - eg a hard disk, cdrom, floppy, usb key, digital camera, etc) with a filesystem on it must be mounted before the filesystem on it can be accessed.
Note - audio cds don´t have a filesystem as such - they are unmountable (well, it can be done but it requires extra effort). Playing an audio cd does not involve mounting it at all. Blank cds don´t have a filesystem either.

Once  a filesystem is mounted, it can be accessed - files can be read from it or perhaps written to it, etc. If there is no application that is actively accessing the filesystem, it can also be umounted. When an application is accessing the filesystem, it prevents it from being umounted. Why? Because if filesystem is umounted and ´disappears´ in the middle of transferring data to and from it, it has serious consequences both for the application that was transferring data and (more importantly) for the integrity of the filesystem.

(If you manually mount a cd and press the eject button on the drive itself, nothing will happen. This is because physically removing a device which has a mounted filesystem on it would have the same effect as if you were allowed to umount in the middle of a data transfer. I can´t stress just how horrible a thing this is from a data integrity viewpoint. (shudder) )

Mounting/umounting isn´t a big issue for hard drives or tape drives (the kind of devices it was written for). You don´t mount/umount them or remove them very often. But for cds, floppies or usb keys it can be a real pain to mount and umount them manually every time you pop them in/out. Hence the automounter, which will do this hum-drum stuff for you behind the scenes.

**Mounting/Umounting - practice**
/etc/fstab is a config file that lists all the known mountable devices and their ´mount points´. Mount points are just regular empty directories where filesystems ´appear´ when they´re mounted. /etc/fstab allows for a short hand form of mounting - it also records the options for mounting these devices, the type of filesystem it expects, etc.

For example, the relevant entry in /etc/fstab for my cd-rw is 

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/hdc says which device is to be mounted, /media/cdrom0 is the mount point, and the rest are options. Notice that data cds use the iso9660 filesystem.

Since I have an entry in /etc/fstab that gives all the nitty gritty details, I can just say 
´mount /media/cdrom0´
and the mount command knows which device to mount, and all the options, etc, etc. If I didn´t I´d have to pass all the options directly (read man mount for all the gory details)

To unmount the command is just
´umount /media/cdrom0´

umount will fail if an application is actually accessing the filesystem when you try to umount it. You have to close all applications that are accessing that filesystem before it will agree to umount. This can get annoying.

/etc/mtab is a file which has an entry for every device that is currently mounted. Useful to know.

So...
- run ´cat /etc/fstab´ to find where your drive mounts, if you don´t know
- put a disc in
- ´mount mountpoint´
- do whatever
- ´umount mountpoint´
- remove the disc.

Simple, but tedious.

**The Beautifully Optimal Solution **

Disclaimer: This is a hack. Uninstalling hal is a hack. The only proper solution is painstakingly hunting down the bug, fixing it, and installing the patched hal. Unfortunately this will probably take a while so this should work in the meantime ;)

You don´t have to uninstall HAL or worry about manually mounting anything because, well, you don´t. 

hal runs a daemon (/usr/sbin/hald) which is perpetrating all the evil.
if you run
´ps -e´  //this will list all the processes running on your system
and find the process id (PID) for ´hald´
and then kill the daemon using the kill command and whatever PID hald is at the moment (don´t assume it´s always the same)
´sudo kill <PID>´

This will solve the problem without uninstalling hal. You can always restart hald - 
´sudo /usr/sbin/hald´
once you´re done doing whatever audio cd stuff you want to do.
This way you avoid removing/reinstalling anything, and you still get all the benefits of automounting/g-v-m/whatever during the times that the hald is running. So if you´re happy with how hald is treating your data discs, this will work well for you.

I´ll probably remove hal again, because automounting does nothing for me anyway (the disc ejects too quickly for it) and I´m used to mounting manually. But you shouldn´t have to.

--Scott

---

### Post by msjulie on 2007-01-08
Hello Scott,

Thank you for your 'long' post.  I didn't know what mtab was about or the simplicity of mount/umount--since I have my cdroms setup in ftabs.  That will make the process easier.

I will try 'kill' hald and see what happens on my end...no time to play tonight.  Sorry.

I also am grateful that you explained aptitude install and remove.  Next time I remove an package, I'll just cut and paste the list it provides, so I'll have a reference incase of a reinstall.  The needy package idea is a good way to reduce the number of packages to reinstall.  I'll keep that in mind as well.

Now, what to do about HAL?

Did you have time to file and follow through on a bug report?  I don't at this time, but I could here shortly.  I have three young children--girls--who are quite demanding on my time, but I still find moments to have some 'fun.'  Yeah, that's pretty sad, to say this is fun.

Well, I need to go.  Thanks again.  I'll report back and let you know how my non-HAL system is working.

Julie S.

---

### Post by zspdude on 2007-01-09
Don´t worry about filing a bug report - I can take care of that.

I haven´t done so yet because I want to muck about a bit first, try the newest version of HAL, and capture some log information that will make the bug report meaningful when I do submit it.

I also want to guarantee that hal is the ultimate source of the evil (something else might be (incorrectly) telling hal to misbehave). 

I´ll probably have some time over the next few days to poke around with this - and I´ll post any relevent developments.

I´ve always found Linux to be ´fun´ in that deranged sense. It´s like a learning game - Unix has been around for so long that 99% of the time there´s a tool that does exactly what I´m trying to do. I just don´t know that it exists. Or how to use it. The discovery process can be pretty torturous, but it´s usually quite rewarding once the giant (of the moment) is slain.

-- Scott

---

### Post by msjulie on 2007-01-09
Hello Scott,

Thanks for taking that on (HAL bug report).

You mentioned that you wanted to do some poking around first to see if it wasn't another package that was misbehaving and telling HAL to eject the CD's.

That was the same thought that crossed my mind when you suggested killing HAL.  That HAL may only be taking orders from another application.

This is a vicious circle of sorts.  Since HAL could be getting the message from multiple sources.

So therefore wouldn't be a HAL issue.  I wish you good luck in tracking it.  If you get stuck (or have success) let me know.  Also let me know when you file the report.  If for some reason you don't get around to it.  Maybe I can in a week or two.

Thanks again.

Julie

---

### Post by msjulie on 2007-01-11
Hello Scott,

I've had a few moments to fiddle with things.

As I mentioned, briefly, my problem is not only with Audio CDs as I first suspected.  My system is also ejecting Data Discs.

I was able to disable HAL as you mentioned and mount and umount Data CDs without a hitch or any sign of the random eject.

Unfortunately, disabling HAL caused some programs to claim I didn't have a CD ROM in the drive (Audio CDs).

I did come up with an alternative to disabling HAL for Data CD's:

In fstab
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

I changed 'user' to 'nouser' giving:

```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Data CDs need to be mounted using:
```
sudo mount /media/cdrom0
```

and to un-mount the CD:
```
sudo umount /media/cdrom0
```

Of course this disables the eject button for anyone without root privileges, but the Data CD seems to stay mounted and doesn't eject.

I know it is not a goos solution, but at least it seems to be working.

Audio CD do not get 'mounted.'  They do get recognized in some way though.  I haven't figured that out yet.  Any suggestions?  I was hoping I could do a similar trick to keep the Audio CD's in place.

I'd still like to use Sound Juicer and Rhythem Box to play CD's.  If I 'kill' HAL then that doesn't seem possible.

Thanks again,
Julie

----Additional

I ran **lshal -m** and got this with an Audio CD
```
Start monitoring devicelist:
-------------------------------------------------
volume_part_1_size_550311936 added
storage_model_Hewlett_Packard_CD_Writer_Plus_8000 condition EjectPressed = 
volume_part_1_size_550311936 removed
```

When I did a dmesg | tail and received:
```
[17191382.492000] cdrom: dropping to single frame dma
```

I don't think I'm getting the "dropping to single frame" message for a Data CD, but will check it out.

Are you getting similar output?

I'm going to try lshal -m with a Data CD and see what I get also.

---Another Addition

I tried lshal -m with a Data CD using my 'nosuer' option in fstab.

My first attempt I did not mount the Data CD the second attempt I opened another terminal and mount the Data CD.

```
Start monitoring devicelist:
-------------------------------------------------
volume_label_srcd_0_2_19 added
storage_model_Hewlett_Packard_CD_Writer_Plus_8000 condition EjectPressed = 
volume_label_srcd_0_2_19 removed
volume_label_srcd_0_2_19 added
volume_label_srcd_0_2_19 property volume.mount_point = '/media/cdrom0'
volume_label_srcd_0_2_19 property volume.is_mounted_read_only = true
volume_label_srcd_0_2_19 property volume.is_mounted = true
storage_model_Hewlett_Packard_CD_Writer_Plus_8000 condition EjectPressed = 
storage_model_Hewlett_Packard_CD_Writer_Plus_8000 condition EjectPressed = 
storage_model_Hewlett_Packard_CD_Writer_Plus_8000 condition EjectPressed = 
```

Notice the second time that something was signaling to HAL to Eject (or is HAL hallucinating) but doesn't eject.

I don't know which is true:
A) HAL is deciding to eject CD's on its own
B) Something is triggering an Eject event and HAL is acting on it

Hhmmm....

---

### Post by zspdude on 2007-01-12
Just some quick thoughts - I'll post more in a bit...

Mounting audio CDs is "impossible" because they don't have an ordered filesystem that Linux recognizes - they just have the raw audio tracks - not a proper filesystem. Applications simply read from the CD - they don't mount.

(I say "impossible" because if you really really want to you can install kernel drivers such as cdfs or cddafs which interpret the audio cd data as a filesystem of sorts. Once you have such a driver in place, you can actually mount an Audio cd and read off of it as if it were a data disc.)

So why don't these applications run? I'm assuming Sound-Juicer is one of them - Sound-Juicer depends on HAL (libhal1 is the edgy package) so if you kill hald s-j will naturally complain because it actually uses it. I'm pretty sure that's the problem rhythm box is having as well. (For the record, KsCD on KDE suffers the same problem - even though it doesn't list hal as a package dependency. (I'm pretty sure this is the fault of the kscd folks).

You're right - forcing processes to have root priviledges if they want to mount/umount the cd-rom drive will prevent hald from ejecting it - but it won't get you any farther with audio discs. 

The bottom line is that s-j and (probably)r-b genuinely need hal running to do their audio stuff. This is a pain but until hal gets working correctly, this is the fact of the matter.

I know for a fact that Grip (which does not depend on hal) both plays and rips cds.
I personally like it and think it's a great application. It's what I use myself, and while it's probably not a permanent solution for you, might work in the meantime. I'd encourage you to check it out.

Scott.

---

### Post by whatteaux on 2007-02-04
A similar thing is happening to me with audio CDs in a Pioneer DVD-115 reader. It plays for half a minute or so then stops, then re-starts for a while, stops, etc...

The same CDs play perfectly with the same drive in Windows XP, or in a different drive (Sony DRU-810A DVD burner) on either Ubuntu or XP..

Looking at /var/log/syslog, I see the following:
```
hdb: status error: status=0x00 { }
ide: failed opcode was: unknown
hdb: status error: status=0x00 { }
ide: failed opcode was: unknown
hdb: status error: status=0x00 { }
ide: failed opcode was: unknown
hdb: status error: status=0x00 { }
ide: failed opcode was: unknown
hdb: DMA disabled
hdb: ATAPI reset complete
cdrom: dropping to single frame dma
```

Then again, for the other "successful" drive, it gives even more equally arcane errors but somehow soldiers on.

The same effect occurs whether playback is via XMMS (via CD-ROM headphone socket) or the Ubuntu 'CD player' application (via sound system & speakers).

So, it's possibly a lowish-level software problem, not the hardware or the apps. The drive works fine for reading data CDs.

The CD never actually ejects, as such, unless I tell it to.

---

### Post by msjulie on 2007-02-06
Hello whatteaux,

I'm sorry to hear you are having CD ROM difficulties.  I still haven't found a satifactory solution to this issue.

you mentioned that you get the follow error.
```
cdrom: dropping to single frame dma
```
That is an error I receive also.  This occurs right before it ejects.

zspdude, aka Scott, thinks it has to do with the Haldameon.  He was going to submit a bug report.  I hadn't followed up on that though.

The more I think about it, the more I "don't" think it is Haldameon.  I think it is just issuing commands it receives.

Scott and I have hashed this out in previous posts, and he thinks otherwise.  I can't be certain, either.

Any good suggestions would be appreciated though.

Sincerely,
Julie

---

### Post by mb26 on 2007-02-08
just fyi this happens on the ps3 drive also with ubuntu.

---

### Post by benny_de on 2007-02-20
i have this problem too, running on edgy eft. has someone maybe found a decent way to fix this problem?

---

### Post by Kathmandu on 2007-04-25
I had two Mitsumi drives -- one just a regular CD drive, the other a CD recorder -- in the old PIII 600 I just installed Feisty on.  I got spontaneous ejections from both drives with both audio and data CD's inserted.  I had the same problems with Dapper and Edgy...

So I swapped out one of the drives for an MSI burner I had lying around the shack and now everything is fine.  The remaining Mitsumi drive still ejects all CD's, but the MSI drive works normally.

Luckily, it was a cheap way for me to fix my problem...

Kat

---

### Post by msjulie on 2007-05-27
Hello Kathmandu,

I just upgraded to Fiesty Fawn.  I'm getting much better results with the HP CD Writer Plus 8000 series. I haven't thoroughly tested it.  It ejected my audio CD on me once,   But overall, it plays much better.  I'll play more CD's and see what happens.

My other drive doesn't seem to be reading at all...hhmmm.

Just thought I'd throw an update here.

I'll play more when I have time...I don't right now.

Sincerely,
Julie

---

### Post by msjulie on 2007-08-21
To anyone with ejecting CD's:

I switched to Feisty Fawn and my CD still ejected.  I loaded the low latency kernel and got better results but the CDs still eject.

It appears a bug crept into the code but has not been isolated.  [Technical Answers]("https://answers.launchpad.net/ubuntu/+question/3385") appears explains it bit and gives this solution:
[B]
Replace the CD ROM.[/B]

I replaced my CD-ROM today and it solved the problem.  I now use a *Memorex 52MAXX 3252AJ1*.

Summary:
Hewlett-Packard CD-Writer Plus 8000, FX4821T and similar models found in many HP Pavilion PIII system--1999ish eject cds.  No good fix found, just replace the drive--yuck!

Sorry, the news is not good.

---

### Post by rrkryder on 2008-06-10
I too, have an older pavillion. An HP 8766C.
I don´t know what kind of drive or how to check it, but my cd writer is the one that ejects after seven moments of time.
So, I tried it in my DVD ROM and it works great.
Hardy Heron rocks, by the way.

---

