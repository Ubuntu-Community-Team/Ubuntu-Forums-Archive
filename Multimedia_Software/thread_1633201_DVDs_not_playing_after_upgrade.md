---
title: "DVDs not playing after upgrade"
date: 2010-11-29
forum: Multimedia Software
---

### Post by MST3Kakalina on 2010-11-29
I know this has been posted a billion times---but I've followed all the instructions I can find and I still am hosed.

When I try to play DVDs (in this case, Airplane!, RIP Mr. Nielsen) in VLC, I get this:

```
katherine@Priscilla:~$ vlc dvd:///dev/scd0 
VLC media player 1.0.6 Goldeneye
[0x9ccd668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title:  
libdvdnav: DVD Serial Number: 
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/katherine/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[0x9f3b830] main access error: no access module matched "dvd"
[0xb7300bc0] main input error: open of `dvd:///dev/scd0' failed: no access module matched "dvd"

```

I've followed the How-To at the top of this forum, in addition to all of the relevant threads in here. I have Medibuntu added to my repositories, and I have all of the assorted restricted packages properly installed. DVD-ROMs work fine; it's just commercial movie ones. Everything worked beautifully before the upgrade to Lucid.  (I didn't do that until October, because I'm slow.)

For reference, here is my fstab which is all commented out anyway:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bb2646cf-6789-4b69-b72d-8f0304cb300b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=81ade131-2a58-425f-9814-2f6b5bf4061c none            swap    sw              0       0
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```


and from lshw -C disk


```
*-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-4084N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: KQ09
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=ready
```


Is there something really stupid and simple that I'm overlooking?  I'm tearing my hair out over here! ](*,)

---

### Post by carl4926 on 2010-11-29
It looks like you have all the codecs etc...
Are you saying these same DVD's worked before?

---

### Post by mc4man on 2010-11-29
It would be better to show the lshw with a comm. dvd in the drive, unless that's what you did post?
If so, this says no filesytem (disc) found or mounted
> configuration: ansiversion=5 status=ready
So that's worth clearing up.

---

### Post by MST3Kakalina on 2010-11-29
mc4man: that lshw -C disk was after the DVD was in the drive, yes. With DVD-ROMs, they mount just fine:

```
*-cdrom                 
       description: DVD-RAM writer
       product: DVDRAM GSA-4084N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: KQ09
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
```

carl: yeah, this and other commercial DVDs worked before the upgrade.

Sometimes, if I leave a DVD in for long enough, it *eventually* mounts and works (this particular one included).  Obviously this is not the best solution possible for me. :P

---

### Post by carl4926 on 2010-11-29
What about if you try ripping the DVD?

Sometimes I try (Need mplayer)
```
mplayer dvdnav://
```

---

### Post by MST3Kakalina on 2010-11-29
No dice with ripping in mplayer, either. :(  Nor with uncommenting the appropriate line in fstab and changing it from "noauto" to "auto." Unless I need to reboot each time I edit fstab?

---

### Post by carl4926 on 2010-11-29
fstab edits do require reboot

But I don't think that's the issue. I have Never edited fstab for this

---

### Post by carl4926 on 2010-11-29
By ripping I meant dvd95 or k9copy

The mplayer was playback trick

---

### Post by MST3Kakalina on 2010-11-29
Trying to use dvd95 just crashes: "Error reading DVD structure."

---

### Post by mc4man on 2010-11-29
I have generally the same deal with a newly installed dvd drive on maverick, though in this case I believe is very specific to the drive and kernel/ubuntu release.
Described here in a similar thread which you may want to glance thru, the Op has/had similar behaviour with a totally different semi-solution
[http://ubuntuforums.org/showthread.php?p=10158192#post10158192](http://ubuntuforums.org/showthread.php?p=10158192#post10158192)

However before I 'fix' my drive with an audio cd I can play the 'unmounted' dvd by having the player access the drive, vlc would be best if you wish to try.
Set vlc in tools - preferences  - input & codecs to /dev/sg0 or /dev/sr0
then
vlc dvd://

---

### Post by MST3Kakalina on 2010-11-29
I don't have an audio CD on hand, unfortunately.  Will have to burn one and then get back to you.  However, your suggestion of changing  the access point in VLC (from /dev/scd0 to /dev/sr0) wasn't enough to do the trick.

Since this is a problem for you in Maverick, I assume upgrading won't fix anything, either.  :(

---

### Post by mc4man on 2010-11-30
> I assume upgrading won't fix anything, either
Not at all, in my case this is a very specific issue that only occurs in maverick and possibly only with certain plextor drives. (the drive is fine in lucid/karmic

My point was that there are a bunch of similar behaviours, but possible solutions, if any,  will vary. So it's worth trying what's worked in similar situations, maybe something will work for your hardware.

---

### Post by Simon_WM on 2010-11-30
you need to download this " libdvdcss " from MediBuntu libdvdcss

[10.04.x]("http://packages.medibuntu.org/lucid/libdvdcss2.html")

[10.10]("http://packages.medibuntu.org/maverick/libdvdcss2.html")

Download that and install it ! that should solve your problem

---

### Post by MST3Kakalina on 2010-11-30
@Simon: I've already installed libdvdcss2 (and all of the other relevant [restricted?] medibuntu packages). Unless there's something unique about those libdvdcss packages you linked to, then I don't think they'll work. :(

@mc4man: do you (or anyone!) at least know *why* this is happening, ie why some drives have issues with some kernels/whatever but not others?  

Also, with your audio CD workaround, does it have to be a commercial CD? Or can it be a burned one?


Failing that, I'm up to my eyebrows in coursework for a TEFL cert.  But once that's over, I'll have a go at updating to maverick.  It's at least worth a shot.

---

