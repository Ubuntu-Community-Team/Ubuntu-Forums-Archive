---
title: "Brasero can't burn VideoDVD/SVCD"
date: 2010-07-26
forum: Multimedia Software
---

### Post by M4he on 2010-07-26
Dear ubuntu community,

I was playing around with Brasero a bit recently. Data and audio projects seem to work fine but I'm running into some issues when trying burn a Video DVD or SVCD.

The first time I clicked on video project in Brasero it told me that it would need the following packages:
**vcdimager**, **mplex **and **dvdauthor**

So I installed **vcdimager**,** gstreamer0.10-plugins-bad-multiverse** (containing mplex), **dvdauthor** and their dependencies.

Then I feeded Brasero with the desired video file (tried different formats like avi or mpg, but mostly mkv);


[LIST]
[*]When I try to burn a **SVCD** it completes the conversion to mpeg2 successfully but when it attempts to start recording it ejects the CD-R. (see SVCD.log in attached [ATTACH]164558[/ATTACH])
[/LIST]
 
[LIST]
[*]When I try to burn a **Video DVD** it doesn't even start conversion, it ejects the DVD+R one second after I press burn. (see VideoDVD.log in attached [ATTACH]164558[/ATTACH])
[/LIST]
[SIZE=1]Note: Both the drive and the blank CDs/DVDs were successfully tested under windows.[/SIZE]


Another thing I wonder about are those plugins. Brasero seems to have different plugins for one action, i.e. on my system it uses:

**growisofs** - burns and erases DVDs and BDs
**wodim** - burns, erases and formats CDs and DVDs
among some others...

So **wodim** and **growisofs** both burn and erase DVDs and both Plugins are activated!? 
There's also **cdrecord** available (which isn't installed) for burning, erasing and formatting CDs, DVDs and BDs.
What would happen if I install this? Which plugin is Braser going to choose? I'm a bit confused with those plugins...
[SIZE=1][SIZE=2]
Any help would really be appreciated.
Thanks in advance!

[/SIZE][/SIZE][SIZE=1]Note: Please *do not* give me recommendations like  using K3B, DeVeDe or any other app! I like Brasero, it's UI and it's  integration into gnome and want to keep using it.[/SIZE]

---

### Post by mc4man on 2010-07-26
Well I don't use brasero but if I was and having issues with it I'd take a look at this ppa and consider trying it

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

---

### Post by M4he on 2010-07-26
Thanks for the quick reply,

I tried out installing the cdrtools. At least this answered my questions about the plugins. All other conflicting ones are automatically removed upon the installation of cdrtools. So cdrtools replace genisoimage and wodim.

Unfortunately that didn't solve the burning problem. I also already updated the firmware of my dvd writer.
I also found out that the writer (which is a GSA-H55N from LG) isn't really compatible to ubuntu as it seems, since it can't read any DVD I put into the drive (however Windows can).

Maybe I'll go and buy a new DVD writer to see if that was the problem...

---

### Post by M4he on 2010-07-26
Okay so I decided to buy a new CD/DVD-burner...

Can somebody please tell whether **P-ATA** (IDE) or **S-ATA** has better compatibility with ubuntu regarding *optical drives*?

Thanks in advance!

---

### Post by mc4man on 2010-07-26
I've never had any problem with ide dvd drives of varying types (lite-on, plextor, Benq, pioneer.

(though the plextor and benq are from a batch of them I purchased several years ago when the models were being discontinued.

Over time have noticed some people having issues with sata models though very, very few thru the more recent ubuntu releases so I think support for sata dvd drives is vastly improved and shouldn't be an issue.

(if it was me I'd be inclined to stay away from samsung sata dvd drives even though they may work fine, but at least here am sticking with an ide even though I could install a sata

---

### Post by M4he on 2010-07-27
Reporting back with a brand new **Samsung P-ATA (IDE) DVD-writer** '**SH-S222L**' !

**[SIZE=1]Note: Don't use the S-ATA one 'SH-S223' (tried that one, only got issues like the whole S-ATA connection crashing affecting my HDD as well)[/SIZE]**

Things that are working now:

[LIST]
[*]Burned a **SVCD** now - Content was playing fine on our TV
[*]Burned a **Video-DVD** now - Content was playing fine on our TV
[/LIST]
Things that still have issues (same behavior like the old drive):

[LIST]
[*]Refuses to read any **DVD-RWs** no matter if burned with some other device or itself
[*]Only accepts **blank** **RWs**; once written on and put in, the drive disappears everywhere in nautilus
[/LIST]
So ok that's a progress!:o Only need to get RWs working now...

Any ideas? ;)

---

### Post by mc4man on 2010-07-27
> Any ideas?

Can't really help there because I only use ImgBurn for dvd and cd burning (Pretty much the only reason I've installed wine

Are all your dvd-rw's the same brand?

I'd put a burned dvd-rw in and run the sudo lshw -C disk command and also 
```
dmesg |tail -n 20
```

---

### Post by M4he on 2010-07-28
> **mc4man said:**
> Are all your dvd-rw's the same brand?

Yep, they are all Sony DVD-RWs. They all work perfectly fine under Windows on any of our PCs and also on our DVD Recorder of the TV. Only ubuntu is having problems with them.

**sudo lshw -C disk**
```
  *-cdrom                 
       description: DVD-RAM writer
       product: CDDVDW SH-S222L
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: SB03
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```and

**dmesg | tail -n 20**
```
[  184.844640] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  184.844645] sr 6:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  184.844651] sr 6:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  184.844658] sr 6:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  184.844670] end_request: I/O error, dev sr0, sector 0
[  184.845555] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  184.845560] sr 6:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  184.845566] sr 6:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  184.845572] sr 6:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  184.845584] end_request: I/O error, dev sr0, sector 0
[  184.846463] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  184.846468] sr 6:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  184.846473] sr 6:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  184.846479] sr 6:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  184.846491] end_request: I/O error, dev sr0, sector 0
[  184.847359] sr 6:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  184.847364] sr 6:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  184.847369] sr 6:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  184.847376] sr 6:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[  184.847387] end_request: I/O error, dev sr0, sector 0

```after putting in a written DVD-RW.
Btw what does the "dmesg | tail -n 20" command?

---

### Post by M4he on 2010-07-29
Ok since the topic's main problem of not being able to burn Video DVDs and SVCDs is solved, I'll mark this thread as solved as well.

---

### Post by mc4man on 2010-07-29
If still having issues with dvd-rw's I would wonder what program or app you are using to burn the disk. (windows and linux

---

### Post by M4he on 2010-07-29
One of the DVD-RWs it refuses to read was burned by Brasero on Ubuntu itself the other one was burned by one of our HDD-Recorders connected to the TV.
Another one which was burned by nero on Windows doesn't work either but I believe that one was already broken as far as I can recall.

However the two DVDs mentioned first are working fine on any other device here...

---

### Post by tmsbrdrs on 2010-11-06
I tried burning a DVD earlier today, didn't work. There were two possible causes, one of which stopped me from burning a CD earlier in the year. 
First, I dragged a directory and allowed brasero to pull the video files out. Since it found the files with no problems and showed them all in the queu, this didn't seem likely. 
Second, the normalize plugin had stopped me before, though it shouldn't have anything to do with burning a DVD. 

I tried changing both and voila. my DVD is currently being converted to an appropriate file format. so far, it's working properly and I expect I will be watching my DVD in an external player soon. :popcorn:

---

### Post by sodoscar on 2011-01-04
hi there,

I'm having the same problem now after months of this working fine... heres the output from terminal when running as root:

```
** (brasero:16771): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed

** (brasero:16771): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed

** (brasero:16771): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed

** (brasero:16771): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed

** (brasero:16771): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed

** (brasero:16771): CRITICAL **: murrine_style_draw_box: assertion `width >= -1' failed

** (brasero:16771): WARNING **: Failed to inhibit the system from suspending: The name org.gnome.SessionManager was not provided by any .service files

```Also I can't seem to configure the plugins as they are grey-ed out.

I'm convinced its nothing to do with my hardware.. can anyone help at all?  

Cheers

---

