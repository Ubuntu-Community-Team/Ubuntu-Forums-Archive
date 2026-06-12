---
title: "mplayer filled up my hard drive with junk and then crashed."
date: 2009-04-03
forum: Multimedia Software
---

### Post by u-slayer on 2009-04-03
So I'm writing a script to convert dvd iso's to mkv files. It works fine most of the time. But I got this one dvd: (Stargate SG1 Season 1 Disc1) - Mplayer will read it for awhile dumping the file correctly, but then it will encounter some error in the files and continuously dump the same broken frame of video to the hard drive filling it up before crashing. Any way to prevent this?

```
mplayer -quiet -dumpstream dvd://3 -dvd-device /media/disk/sg1/1/1-3 -dumpfile /media/disk/mkv/1-3.3/1-3.3.vob
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://3.
There are 4 titles on this DVD.
There are 9 chapters in this DVD title.
There are 1 angles in this DVD title.
audio stream: 0 format: ac3 (stereo) language: en aid: 128.
number of audio channels on disk: 1.
subtitle ( sid ): 0 language: es
subtitle ( sid ): 1 language: fr
number of subtitles on disk: 2
/media/disk/mkv/1-3.3/1-3.3.vob: Error writing file.

Exiting... (Fatal error)
```

---

### Post by andrew.46 on 2009-04-04
Hi u-slayer,

> **u-slayer said:**
> So I'm writing a script to convert dvd iso's to mkv files. It works fine most of the time. But I got this one dvd: (Stargate SG1 Season 1 Disc1) - Mplayer will read it for awhile dumping the file correctly, but then it will encounter some error in the files and continuously dump the same broken frame of video to the hard drive filling it up before crashing. Any way to prevent this?

It could be a problem with copy protection in which case I suspect there is nothing you can do. But I notice that your copy of MPlayer is quite old:

```
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
```

and it might be worth trying a more modern version, guides exist for this on these forums. Do you have the same error with other software? Perhaps also a quick shot with vobcopy might be well worthwhile.

All the best,

Andrew

---

### Post by u-slayer on 2009-04-04
> **andrew.46 said:**
> But I notice that your copy of MPlayer is quite old:

```
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
```

and it might be worth trying a more modern version, guides exist for this on these forums. Do you have the same error with other software? Perhaps also a quick shot with vobcopy might be well worthwhile.

All the best,

Andrew

1.0rc2 is the latest stable release (I just checked)

Also I tried vobcopy

```
vobcopy -I -i /media/disk/sg1/1/1-3
[Hint] You use -i. Normally this is not necessary, vobcopy finds the input dir by itself. This option is only there if vobcopy makes trouble.
[Hint] If vobcopy makes trouble, please mail me so that I can fix this (robos@muon.de). Thanks
Vobcopy 1.1.0 - GPL Copyright (c) 2001 - 2007 robos@muon.de
[Hint] All lines starting with "libdvdread:" are not from vobcopy but from the libdvdread-library
[Error] Could not find the provided path (/media/disk/sg1/1/1-3), typo?
[Error] Could not get the device which belongs to the given path!
```

It couldn't find the device which belongs to the path because there is none. The path is just a dvd folder with a VIDEO_TS folder and dvd files inside it. Mplayer has no trouble with this, but apparently vobcopy can't read from a folder which gives me serious doubts about it reading from an iso file, something that mplayer has no trouble with.

---

### Post by andrew.46 on 2009-04-04
Hi u-slayer,

> **u-slayer said:**
> 1.0rc2 is the latest stable release (I just checked)

The 'release' version that you have is unfortunately not supported by MPlayer at all as it is considered outdated. Have a look at the download page:

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

and you will see:

```
MPlayer v1.0rc2 source outdated
```

The latest version in fact shows as:

```
andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r29134-4.2.4 (C) 2000-2009 MPlayer Team
```

and thus has almost 2 years of development over the 'outdated' version and in my experience is *very* stable. Are you running Intrepid? Have a look at [this guide]("http://ubuntuforums.org/showthread.php?t=1024592") and consider if it might be worth the effort :-).

My apologies about vobcopy, I somehow had it in my head that you were ripping from dvd :-).

---

### Post by elektronaut on 2009-06-23
> **u-slayer said:**
> ...
Also I tried vobcopy
...
It couldn't find the device which belongs to the path because there is none. The path is just a dvd folder with a VIDEO_TS folder and dvd files inside it. Mplayer has no trouble with this, but apparently vobcopy can't read from a folder which gives me serious doubts about it reading from an iso file, something that mplayer has no trouble with.
Might be a bit late, but I'm also converting a couple of iso files into mkv's. I use Vobcopy because I ripped the whole DVD's (used DVDDecrypter to rip them - just read that you can also decide to only rip the main movie in the GUI), but only want to transcode the main movies. For transcoding I then run the magic script [**h264enc (click here)**](http://h264enc.sourceforge.net/) which also uses MEncoder. In order to use Vobcopy, you first have to mount your iso:
```
sudo mkdir /media/iso
sudo mount -o loop -t iso9660 file.iso /media/iso
```
Then
```
sudo vobcopy -l -i /dev/loop0 -n xx -o /path/to/output/
```
where "xx" is the number of the main movie, in case you have ripped the whole DVD. You should be able to know the number by looking into /media/iso/video_ts/ for the largest files. There should be a couple of files with the same start number, let's say "vts_10_1.vob", "vts_10_2.vob", ..., "vts_10_7.vob", which amount to a couple of GB's. So in this case you would use
```
sudo vobcopy -l -i /dev/loop0 -n 10 -o /path/to/output/
```
You will notice instantly if you pick the wrong number, because Vobcopy displays the complete file size at the start. If it's just a couple of hundred MB's, then you picked an extra and can hit CTRL-C.
The reason you got to run Vobcopy as sudo is because you were also root when you mounted the iso file. You won't be able to access the loop device as a normal user. I don't know if there is another way of mounting it. 
When you got the vob file, you change it's ownership:
```
sudo chown myUserName: /path/to/output/xy.VOB
```
Finally you run the wonderful [**h264enc**](http://h264enc.sourceforge.net/) on the vob file.

---

