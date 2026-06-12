---
title: "Audio CD won't mount - Xubuntu"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by coffeeshawn on 2007-08-26
I recently installed Xubuntu on my old Dell OptiPlex GXa, and love it.  Couldn't get M$ to breathe life into an old machine like this!

One issue I've encountered, though, is not being able to mount/play audio CDs.  When I try to mount by double-clicking in Thunar, I get two error pop-ups.  The first says, "**Failed to Mount 'Audio CD'.**  Unknown Error."  The second pop-up says, "**Cannot Mount Volume.**  Invalid mount option when attempting to mount the volume."

When I try to mount from a terminal by typing "mount /media/cdrom0", I get this message:

[INDENT]mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/INDENT]

The command "dmesg | tail" returns this:

[INDENT][18479.199819] ide: failed opcode was: unknown
[18479.200474] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[18479.200508] end_request: I/O error, dev hdc, sector 64
[18479.200655] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[18685.034018] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[18685.034072] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[18685.034099] ide: failed opcode was: unknown
[18685.034758] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[18685.034791] end_request: I/O error, dev hdc, sector 64
[18685.041235] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16[/INDENT]

Any ideas what might be causing the issue?  I installed Xubuntu from the live cd, so I'm pretty sure my cd-rom drive is okay.  I also tried downloading the XMMS player, in case it was something to do with gxine, but to no avail.

Thanks in advance for any assistance.

---

### Post by RageOfOrder on 2007-08-26
Can you post your /etc/fstab file for me?
It could just be that you need to tack 'users' onto the end of your mount option for the cdrom.

Also check that you are a member of the cdrom and audio groups
$ cat /etc/group
You can add yourself to a group using usermod.

---

### Post by raphha on 2007-08-26
Hello,
the reason why you can't mount this CD is that it is an Audio CD...
Try to open it with
* amarok if you would like to listen to it
* k3b if you want to copy it
* kaudiocreator if you want to rip it

hope this helps.
raph

---

### Post by amitst on 2007-08-27
When I insert the audio CD on my Xubuntu desktop (7.04) then an icon appears on the desktop stating "audio cd". If I right click it and select play, then gxine opens and returns some plug-in related error.

I am putting this request through my office PC (which has Ubuntu) as I am having some broadband issues for my home PC. Let me know if you need any other info and I will note it down and post it here.

I even tried using DSL which plays MP3 CDs fine but can't play audio CD through XMMS. :(

---

### Post by bomanizer on 2007-12-03
I'm also having this problem. I've checked groups, fstab, /dev/scd0 and /dev/cdrom, they're correct. My symptoms:

1. Put in audio CD, no icon appears on desktop.
2. VLC can play the CD, Sound juicer doesn't even recognize it..
3. I can rip CDs if I put the disk in before I boot up. Then I can change CDs, but the icon on the desktop doesn't disappear before I boot again with no CD in drive.

This is on a basic 7.10 install on a Thinkpad. My guess is that there's something wrong with gnome-volume-manager, or the like... did a reinstall of the packages, no avail... :(

WEIRD! :)

---

### Post by seul on 2007-12-04
> **bomanizer said:**
> My symptoms:

1. Put in audio CD, no icon appears on desktop.
2. VLC can play the CD, Sound juicer doesn't even recognize it..
This is on a basic 7.10 install on a Thinkpad. 
3. I can rip CDs if I put the disk in before I boot up. Then I can change CDs, but the icon on the desktop doesn't disappear before I boot again with no CD in drive

Same here. I have the feeling that it happened after I followed powertop's suggestion and typed
```
hal-disable-polling --device /dev/scd0
```
I don't know how to revert that.

```
hal-enable-polling --device /dev/scd0
``` returns 

```
bash: hal-enable-polling: command not found
```

[Shallowsky]("http://shallowsky.com/blog/2005/Jul/") mentions a file "/etc/hal/hald.conf":
> change true to false under <storage_media_check_enabled> and <storage_automount_enabled_hint>
 -- I don't seem to have this file.

Fstab entry looks like this:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by bomanizer on 2007-12-04
> **seul said:**
> Same here. I have the feeling that it happened after I followed powertop's suggestion and typed
```
hal-disable-polling --device /dev/scd0
```
I don't know how to revert that.


I did that too. And I'm adding Virtualbox on my list of culprits also :) ..don't know how Vbox could be responsible, but I'll dig in once I'm back home. Googling for that HAL command..

EDIT:

Found this, at [http://www.lesswatts.org/tips/disks.php](http://www.lesswatts.org/tips/disks.php):

"Note that this means that you will not get a pop-up window if you insert a CD. To enable this polling again, use the this command: 
hal-disable-polling --device /dev/scd0 --enable-polling"

Heh, kinda unlogical command that one :D

---

### Post by bomanizer on 2007-12-04
Disable the polling. That worked for me :). I think we should inform people using PowerTop about this? yes, no?

---

### Post by seul on 2007-12-04
Hey bomanizer, that went slick. I hereby bow to your finding skills. I googled everything I could possibly imagine to find the way out of the hal cul-de-sac but to no avail. You're right, it is a brilliant command, could come in handy if one had to quickly explain "counter intuitive" to an alien with a ray gun one day, 

I don't have a CD in my vicinity at the moment, so I'll test later and get back to you.

Informing the people is probably sufficiently done through this thread, I found it straight away. But maybe we could send the hal people a new command.

Thanks for your efforts, cheers.

---

### Post by bomanizer on 2007-12-04
If you compare my bean count with my joined date you'll see that I'm spending more time searching than writing...

---

### Post by seul on 2007-12-04
> **bomanizer said:**
> I'm spending more time searching than writing...

Same here. But that probably means most problems are already solved by someone. 

I'll let you know once I checked the CD, all the best in the meantime and thanks again.

---

### Post by seul on 2007-12-04
I can confirm the fix. Cheerio.

---

### Post by Phil Urich on 2008-03-01
The fix did NOT work for me, I get the error "Cannot find storage device /dev/scd0."  And indeed, there appears to be no such device; it isn't in /dev, and nothing shows up in System Settings -> Disks and Filesystems (I'm using Kubuntu 7.10, and it was blindly following Powertop's suggestion that got me into this mess as well).

---

### Post by 512mattw on 2008-03-26
I'm having the same exact issue.
did you resolve yours?
I have one drive cd/dvdrw. dvds play fine cds no

help please

matt

---

### Post by Phil Urich on 2008-03-26
I actually **did** resolve mine, it was just plain not working ](*,) but then one day I went "sudo su" to go to root and once again did ```
hal-disable-polling --device /dev/scd0 --enable-polling
``` and it worked!  Might be worth doing it immediately after rebooting and/or in recovery mode.

Also perhaps of help is that I know when it actually worked for me it went thusly:
```
Polling for drive /dev/scd0 have been enabled. The fdi file deleted was
  /etc/hal/fdi/information/media-check-disable-storage_model_DVDRW_SSW_8015S.fdi
```

So, it's quite possible you have a similar file sitting in /etc/hal/fdi/information/, which if the command refuses to work under any circumstances you could always go into recovery mode and delete...that, I can only assume, would also fix the problem!

I kept meaning to post this back here but I forgot, apologies; learn from my mistake and please reply whether or not this helped :)

(edit: just figured I'd note, there's no real reason I went "sudo su" and then did the command instead of just going "sudo <command>", but I've was really just trying everything I could and that happened to be the time it worked for me)

---

