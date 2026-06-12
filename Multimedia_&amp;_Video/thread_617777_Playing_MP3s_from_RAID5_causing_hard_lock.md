---
title: "Playing MP3s from RAID5 causing hard lock"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by dutch_gecko on 2007-11-19
(p.s. feel free to move this to hardware if it belongs there, I'm just assuming it's a media problem for now)

Well here's a weird one. Whenever I attempt to play an MP3 file located on my 3 disk RAID 5 (created in mdadm), the entire system locks up. I've tried playing a selection of files in mpd, Rhythmbox and Totem. I can copy the files to my home directory and play them without issues at all.

The same problem also occured when playing a FLAC file.

Here's the relevant line in fstab:
```
/dev/md0        /media/raid     ext3    defaults    0   2
```

And the permissions of the raid itself:
```
gecko@tokaygecko:/media$ ls -l
drwxrwxrwx 5 root root    12288 2007-11-18 19:44 raid/
```

And of the music directory within the raid:
```
gecko@tokaygecko:/media/raid$ ls -l
drwxr-xr-x 212 gecko gecko 12288 2007-11-13 20:18 music/
```

This is pretty much a fresh install of Ubuntu Gutsy. Initially I had some troubles building the raid, since the build process crashed half way through. Letting it rebuild afterwards though sorted things out (or so I thought).

I can access the raid in other ways without difficulty. I can navigate through using either the terminal or nautilus, I can create files and read and write to them, and I can copy files off and onto the raid.

I'm about to test one last thing related to symbolic links, and after that I may test a video file to see what kind of result I get out of that, but the constant restarts are getting tiring.

edit1: I just played the usual way and got a good thirty seconds of guitar riffs before the system locked with some beeping noise coming out of the speakers.

edit2: just got weirder: an episode of mythbusters (containing an MP3 audio stream) just played fine in Totem from the raid disk. What's going on?!

---

