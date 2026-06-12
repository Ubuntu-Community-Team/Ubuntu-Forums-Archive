---
title: "mp4 converted to mpeg 1 or mpeg 2 - how to ?"
date: 2015-01-20
forum: Multimedia Software
---

### Post by michael-piziak on 2015-01-20
How can I convert an mp4 file to mpeg1 or mpeg2 so I can put it on a flash drive and view on a flatscreen tv (that requires it be mpeg1 or mpeg2)

---

### Post by vinnywright on 2015-01-20
I would try "winff"

```
vinny@vinny-Bonobo-Extreme:~$ apt show winff
Package: winff
Priority: extra
Section: universe/graphics
Installed-Size: 1,529 kB
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Paul Gevers <elbrus@debian.org>
Version: 1.5.3-3
Depends: winff-gtk2 | winff-qt
Breaks: shared-mime-info (<< 0.40)
Download-Size: 116 kB
Homepage: http://www.winff.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
APT-Sources: http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
Description: graphical video and audio batch converter using ffmpeg or avconv
 WinFF is a graphical user interface for FFmpeg or avconv. It will convert
 almost any video file that FFmpeg or avconv will convert. WinFF does multiple
 files in multiple formats at one time. You can, for example, convert
 mpeg's, flv's, and mov's into avi's (or DVD/VCD format or MPEG or 3gp
 etc.) all at once.
 .
 This package provides a variety of preset conversion settings for
 common formats and devices. These presets are intended to hit the
 "sweet spot" for each individual codec. They have been written with a
 tip of the balance to quality.
 .
 For most presets to work, it is necessary to have the unstripped version
 of the libavcodec package, which can be obtained by installing
 [COLOR=#ff0000]libavcodec-extra [/COLOR]as suggested by this package. It might be necessary
 to enable additional repositories to find that package.

```

or search for command line arguments for avconv or ffmpeg that do this .

the avconv is part of the libav-tools package.

VINNY

---

### Post by mc4man on 2015-01-20
If you're being limited to mpeg1/2 then without any specifics (source mat., target display, dvd player support specs, ect), what Andrew suggested is best way to start. It will give you a DVD_VIDEO compliant mpeg2video file.
[http://ubuntuforums.org/showthread.php?t=2150361&p=12674818&viewfull=1#post12674818](http://ubuntuforums.org/showthread.php?t=2150361&p=12674818&viewfull=1#post12674818)

You may not want pal, so for ntsc, same command, example with ffmpeg, avconv can be used - 
```
ffmpeg -i *input*.mp4 -target ntsc-dvd -aspect 16:9 -ac 2 *output*.mpg
```

that would give you ac3 as audio if it matters
You could use mp2 if desired, it's allowed if you later author & burn to disk, ex. (you may need to check -ar spec if burning to disk.
```
ffmpeg -i *input*.mp4 -target ntsc-dvd  -aspect 16:9 -c:a mp2 -ac 2 -ab 192k -ar 44100 *output*.mpg
```

If you don't need to be DVD_VIDEO compliant then you could do other things.

---

### Post by michael-piziak on 2015-01-21
WinFF works good; however, I attempted to convert a 90 minute file and after working for an hour it gave the error "buffer overflow error."

Now I'm trying Transmageddon.

---

### Post by michael-piziak on 2015-01-21
Update:  Even when WinFF shows the overflow error, the end resulting mpg file can still be used.
I did a test and used WinFF and Transmageddon to convert the same 1.5 hour movie to mpg.
End result:  both programs converted and can play both on the computer; however, the Transmageddon file had a noticeable audio delay when plugged into the t.v. and the WinFF had a very slight audio delay.
hmmmm

---

### Post by michael-piziak on 2015-01-24
Update: winff works good after many runs.  Thanks allyally

---

