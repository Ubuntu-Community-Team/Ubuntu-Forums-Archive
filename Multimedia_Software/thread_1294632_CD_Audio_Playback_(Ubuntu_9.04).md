---
title: "CD Audio Playback (Ubuntu 9.04)"
date: 2009-10-18
forum: Multimedia Software
---

### Post by bobwyajnr on 2009-10-18
Hi all,

Just wanting some help troubleshooting CD audio playback (i.e. direct playback from a physical CD). I recently installed Ubuntu 9.04 for a guy called Paul at my work. I installed all the extras and CD Audio playback worked fine initially. I used "Ubuntu Tweak" to set playback default to Rythmbox as this appeared to work the best (full tracks listing with "real names" - not CDDA1, etc.).

Paul's PC plays back web flash content, iplayer content, DVD discs (compiled latest versions of SMplayer/Mplayer), etc. However (for some unknown reason) CD Audio playback has now broken again. CD Audio discs are just mounted (on the desktop) - no playback application is autostarted anymore. I checked in "Ubuntu Tweak" and Rythmbox is still the default CD Audio playback app. I can't find any way to playback audio CD content either via the Rythmbox menus...

What application/codec actually decodes Audio CDs?? How can I troubleshoot this problem?? Is there any apps like "Gspot", etc. for Windows, that can help with this kind of issue?

Bob

---

### Post by ajgreeny on 2009-10-18
Try opening nautilus and go to Edit->Preferences->Media tab and there you can set what you want to happen when all sorts of different media are used.  I don't know if ubuntu tweak changes or over-rides any of that as I have never used it, but try it and see.

---

### Post by bobwyajnr on 2009-10-19
OK

An update to this thread. I have checked at the file associations are correct in the suggested Nautilus menus.

Today I checked out the machine and it would mount the audio CD and start Rhythmbox. However again Rythmbox is not loading the CD track info at all. Also I get the CD folder opening with all the tracks listed as "Track %%" with a padlock beside them... I have read about this elsewhere - some kind of permissions issue perhaps?

The problem is definately something to do with the processing of audio CDs. Perhaps someone could check out the settings for Paul's CD device (in **/dev** and **/etc/fstab**) before I move to identify other possible causes.

fstab:
```

# /etc/fstab: static file system information.
...
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

/dev:
```

...
lrwxrwxrwx  1 root   root           3 2009-10-19 12:12 cdrom -> sr0
lrwxrwxrwx  1 root   root           3 2009-10-19 12:12 cdrw -> sr0
...
lrwxrwxrwx  1 root   root           3 2009-10-19 12:12 dvd -> sr0
lrwxrwxrwx  1 root   root           3 2009-10-19 12:12 dvdrw -> sr0
...
lrwxrwxrwx  1 root   root           3 2009-10-19 12:12 scd0 -> sr0
...
brw-rw----+ 1 root   cdrom    11,   0 2009-10-19 12:12 sr0

```

Any further thoughts on how to trouble shoot this problem? Again what app actually decodes the Audio CD track/data information?

Thanks for any help...

Bob

---

