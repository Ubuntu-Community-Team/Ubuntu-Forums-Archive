---
title: "Copy DVD directly (disc to disc), no image"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by jamespi on 2007-09-30
Hi,

I have a DVD-ROM drive and a dual layer+/- DVD RW. I want to duplicate a DVD but I only have a couple of gigs of hard disc space left. Is it possible to copy directly from disc to disc without creating an intermediate disc image on my hard disc?

Gnome baker doesnt seem to have the option to do this. K3b wont recognise the disc i am trying to duplicate.....

thanks,
james

Ubuntu 7.04, 1GHz duron, 1gb ram.

---

### Post by Benedolt on 2007-10-03
What you're trying to do is called "burning on the fly' and this is supported for example by brasero. 
(k3b should be able to do this also, though.)

---

### Post by jamespi on 2007-10-08
thanks for that. i tried brasero as well (figured out the on the fly options) but i get errors. I think my fstab file is not correct.

here is the error from brasero:

"Error while burning: the selected files did not fit on the CD"

and the log contains:

```
Session starting:
	flags			= 16503 
	media type	= 0
	speed		= 4
	track type		= 9
	track format	= 63
	output		= none
job (BraseroReadcd) set_source
imager (BraseroReadcd) set_output_type
imager (BraseroReadcd) set_output
job (BraseroReadcd) set_task
imager (BraseroReadcd) get_size
job (BraseroReadcd) set_task
imager (BraseroReadcd) get_track_type
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_source
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
imager (BraseroReadcd) get_track_type
imager (BraseroReadcd) get_size
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-speed=4
	-dvd-compat
	-use-the-force-luke=tty
	-use-the-force-luke=tracksize:507346944
	-Z
	/dev/hdc=/proc/self/fd/0
process (BraseroReadcd) getting varg
process (BraseroReadcd) got varg:
	readcd
	dev=/dev/hdd
	-nocorr
	-noerror
	-f=-
process (BraseroReadcd) launching command
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'builtin_dd if=/proc/self/fd/0 of=/dev/hdc obs=32k seek=0'
process (BraseroGrowisofs) stderr: :-( /dev/hdc: 4173824 blocks are free, 507346944 to be written!
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "The files selected did not fit on the CD"
iter (BraseroReadcd) stopping
process (BraseroReadcd) got killed
iter (BraseroReadcd) stopped
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : The files selected did not fit on the CD

```

The disc was definately a blank dual layer disc.

here is my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3 -- converted during upgrade to edgy
UUID=99324a7e-84c1-4828-83e0-6026a12be062 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=18E4AA37E4AA1752 /media/hda1 ntfs umask=0 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=188b360a-edcd-4f55-ba4d-86838bbda06d /home/jamespi/isos ext3 defaults,errors=remount-ro 0 2
#/dev/hda2       /media/hda2     ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1 -- converted during upgrade to edgy
UUID=DE74AE5574AE3067 /media/hdb1 ntfs umask=0 0 0
# /dev/hda5 -- converted during upgrade to edgy
UUID=3535d1eb-94e9-4885-bc41-01e08dd554d9 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

note there is no entry for the DVD writer there. 

in /dev there are dvd and dvdrw files so i dont know if these need to be used instead of /dev/cdrom or something.

brasero/k3b/k9copy all seem to reference my dvd drives through  /dev/hdc (dvd rom) and /dev/hdd (dvdrw). i dont know if this is the problem.

---

### Post by Tigera on 2007-10-08
Are you sure that hdc is the DVD ROM?  It looks like the program is trying to copy to the DVD ROM instead of from it.  I assume that the disc that you are using is in the correct drive and that it is blank?

---

### Post by jamespi on 2007-10-10
it's what every copying program that i've tried detects them as. how could i tell/correct the problem it they were wrongly mapped?

---

### Post by nzadLithium on 2007-10-10
I don't see how any program could do this. I'm am fairly certain that you will need to rip the iso unless you have two dvd drives. otherwise where is it going to store the contents of the dvd? it has to store it somewhere. It may be possible to load most of the dvd into your ram chips but i think it will also end up using your swap partition as well if you have set one or maybe copying to your hard disk.

You might be able to rip the dvd to a compressed format so that it doesnt take so much room when you copy.

If i'm wrong im interested to know how it would work. Plz post and explain if i am.

---

### Post by mc4man on 2007-10-10
While your fstab doesn't look right I've never done an upgrade "converted during upgrade to edgy", though one might expect to see 2 entries and a hdc(d) after  /dev/ 
In any event i seriously doubt brasero can rip and burn a dvd video on the fly. I think it needs a video_ts folder to work with first. Also I doubt  brasero can rip dvd video to begin with

edit: assumed dvd video  probably my mistake   Does brasero write to dual layer disks?

---

### Post by jamespi on 2007-10-14
nzadLithium:

yes i have two drives.



mc4man:

the copying i'm trying to do is just bit-for-bit duplication, ie. what you'd get if you ripped and iso then burnt it again. no "video_ts" involved. even if brasero couldnt do this, why doesnt k3b work either? I know k3b rips ISOs and burns them. The on-the-fly option just skips the part where it writes the ISO to disk, and simply streams the data from one disc to the other.


i think the problem is that when i installed the dvd rom drive in order to try this, i switched all my drives around on the IDE ribbons and now my fstab is out of date.

i used to have

ide channel 1 - master - A HARD DISK (hda)
ide channel 1 - slave - NOTHING

ide channel 2 - master - DVD RW (hdc)
ide channel 2 - slave - ANOTHER HARDISK (hdd)


then i jigged it all around and had:

ide channel 1 - master - A HARD DISK (hda)
ide channel 1 - slave - ANOTHER HARDISK (stilll mounted as hdd because edgy had updated my fstab to reference UUIDs instead of IDE channel position)

ide channel 2 - master - DVD RW (hdc)
ide channel 2 - slave -  DVD ROM (hdd)

so i had TWO hdds mounted somehow?!?. to fix this is modified fstab to mount the "ANOTHER HARDDISK" as hdb.

it didnt seem to have an impact on the problem i had with the various burner applications though.

---

### Post by Tigera on 2007-10-15
Well, I was at least wrong about the burner, with that setup, everything is detected correctly.  What concerns me is this line:

process (BraseroGrowisofs) stderr: :-( /dev/hdc: 4173824 blocks are free, 507346944 to be written!

How much space do you have left on the hard drive? (You can find this with the du / command).  If I'm right, Brasero is trying to copy stuff to the hard drive before burning it, which means that the options may be incorrectly set.
Keep in mind, though, you have a serious chance of buffer underruns since both optical drives are on the same IDE channel.

---

### Post by jamespi on 2007-10-15
hdc is one of the dvd drives though

---

### Post by mc4man on 2007-10-15
what version of brasero are you using, and is this a dvd video (encrypted?)

---

### Post by jamespi on 2007-10-17
brasero is v. 0.5.2 (standard feisty repo version), and the DVD is a CSS encrypted DVD video. It's worth pointing out that when i insert the DVD it launches totem and plays perfectly, so i have the necessary  deCSS / codecs installed.

---

### Post by mc4man on 2007-10-17
I dion't think that ver. supports ripping, newest does
```
29-08-2007 : 0.6.1

New release of stable 

- backported patches/fixes from trunk to the stable branch
- added multi session import in data project view
- use libdvdcss to copy protected DVDs
- updated libburn support to 0.3.4
- new small SCSI library for a better device detection that will hopefully lead us to drop nautilus-cd-burner
- small GUI improvements
- new icons (thanks to Josef Vybíra and Kalle Person)
- lots of fixes
- new translations
- Complete support for cdrkit.
- Added more mimetype to file chooser filter
- Support for libisofs 0.2.8
```
That being said take tigera's post to heart, using same ide is a bad idea

---

