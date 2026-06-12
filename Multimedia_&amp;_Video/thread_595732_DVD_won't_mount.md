---
title: "DVD won't mount"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by sonicsmooth on 2007-10-29
7.10 Gutsy

I'm having trouble mounting DVDs to view, but I can mount a cdrom and view its contents.

I've tried in xine, mplayer, and vlc, and they all give me some form of "can't mount device" error.  It looks like xine is trying to use libdvdcss, but it looks like I have libdvdcss2 installed.  I'm not sure if that's relevant.

My drive is on /dev/hdb (Slave on first IDE channel).
My fstab entry looks like this:
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

My /dev links look like this:
0 lrwxrwxrwx  1 root   root           3 2007-10-28 21:57 cdrom -> hdb
0 lrwxrwxrwx  1 root   root           3 2007-10-28 21:57 dvd -> hdb

my /media links look like this;
0 lrwxrwxrwx  1 root root   13 2007-10-28 21:12 cdrom -> /media/cdrom0
4 drwxr-xr-x  2 root root 4096 2007-10-28 21:10 cdrom0

Sometimes the DVD player won't eject, as though hitting the eject button causes it to re-insert.  I have to use a pin to open the drive.  Then the next time around it ejects fine.  This matches attempts with the eject command.

Is this a hardware problem?

thanks
Michael

---

### Post by akudewan on 2007-10-29
Well, the issue about ejecting may be a hardware problem. About the mounting, "dmesg | tail" on the commandline will give you an error message about any mounting issues. Try running this command after an unsuccessful mount and see what it shows.

Mplayer, I think, can play the dvd without mounting it. Try running "mplayer dvd://01" or "mplayer dvd://02" (01 and 02 are the track numbers).

---

### Post by sonicsmooth on 2007-10-29
mplayer automatically tries dvd://01 or dvd://1   It says this in its output when it fails.

When I tired it with xine --verbose=10 dvd:// it looks like it's trying to play /dev/hda1 which is weird because that's my main hard drive.

I didn't see any xine options to force it to use /dev/dvd or /dev/hdb.

The eject program says it tries an ide eject which fails, then tries a scsi-eject (or something like that; I'm not at my PC at this exact moment), which it claims succeeds.

When I press the eject button on the drive, the motor turns and it's as though it changes its mind in the middle.  Weird.

Also, when I try doing an hdparm on /dev/hdb I get some type of IO_CTL error.  This suggests to me it's either an unsupported DVD drive, maybe a non-compliant DVD drive, or a damaged DVD drive.

I don't have Windows to test it out.

---

### Post by sonicsmooth on 2007-10-29
Another question in general:

Does a DVD need to be "mounted" for a movie the same way as a cdrom does for data?  You mentioned that mplayer can read a dvd without mounting it.  Does it do something "lower level" than the OS normally does for adding a DVD to the file system? 

In my case, the drive will mount a cdrom just fine.  I'm not sure if I'm even supposed to be able to mount (using the normal fstab stuff) a normal video DVD.  I will observe dmesg when trying to mount a DVD and see what it says....

thanks
michael

---

### Post by mc4man on 2007-10-29
Typically when you insert removable media it auto mounts (shows up on desktop)
Possibly you've disabled that though I've noticed ubuntu is more sensitive to aging/dirty drives than windows. Does anything appear on desktop when you insert a dvd?
you could also ck. your sys.log after inserting to see if an event is logged

---

### Post by akudewan on 2007-10-30
> **sonicsmooth said:**
> Another question in general:

Does a DVD need to be "mounted" for a movie the same way as a cdrom does for data?  You mentioned that mplayer can read a dvd without mounting it.  Does it do something "lower level" than the OS normally does for adding a DVD to the file system? 

In my case, the drive will mount a cdrom just fine.  I'm not sure if I'm even supposed to be able to mount (using the normal fstab stuff) a normal video DVD.  I will observe dmesg when trying to mount a DVD and see what it says....

thanks
michael

I don't think it needs to be mounted like a data CD. I played a vcd using the *mplayer vcd://02* method, and checked /proc/mounts, and the drive wasn't mounted. You can mount is like a data cd, and then play the avseq01.dat or something.Vob file as well.

As for your mounting issue, maybe its just the dvd thats gone bad and not the whole drive. Try testing with another dvd if you have one....

---

### Post by sonicsmooth on 2007-10-30
(Not sure how to quote the last post)

I went out to Best Buy and bought a new dvd-rw+-/double/dual whatever drive, and it worked like a charm, no links or difficulty necessary.  It actually worked like I, a user, would expect it to work. Yay.  About time.  With the old drive VLC wouldn't mount a music CD, but Audio juicer would, nobody would mount a real DVD.  Now with the new drive they both work.

I wonder if this is why sometimes a few years ago when in this hardware lived the soul of XP, the DVD playback would often just freeze the machine?  I just assumed it was crappy windows drivers or something.  Now it looks like it may have been this stupid DVD drive all along.

However xine still complains there is no plugin for dvd://.  I think I've got every media package installed, so I'm not sure why it's doing this to me.  I wonder if for xine this is the same problem that is preventing me from reading channels.conf for dvb viewing.

Michael

---

### Post by akudewan on 2007-10-31
> **sonicsmooth said:**
> (Not sure how to quote the last post)

I went out to Best Buy and bought a new dvd-rw+-/double/dual whatever drive, and it worked like a charm, no links or difficulty necessary.  It actually worked like I, a user, would expect it to work. Yay.  About time.  With the old drive VLC wouldn't mount a music CD, but Audio juicer would, nobody would mount a real DVD.  Now with the new drive they both work.

I wonder if this is why sometimes a few years ago when in this hardware lived the soul of XP, the DVD playback would often just freeze the machine?  I just assumed it was crappy windows drivers or something.  Now it looks like it may have been this stupid DVD drive all along.

However xine still complains there is no plugin for dvd://.  I think I've got every media package installed, so I'm not sure why it's doing this to me.  I wonder if for xine this is the same problem that is preventing me from reading channels.conf for dvb viewing.

Michael

Glad you got that sorted out. And I'm also glad that you didn't get [bathroom tiles instead]("http://yro.slashdot.org/article.pl?sid=07/10/29/1833227") of a DVD-drive :lolflag:

As for the issue with Xine, I'm really not sure, maybe someone else can help you there...

---

