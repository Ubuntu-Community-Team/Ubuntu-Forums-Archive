---
title: "Trying to convert wma to ogg/flac soundconverter"
date: 2009-05-04
forum: Multimedia Software
---

### Post by cptrohn on 2009-05-04
Hi I am trying to convert my old wma's to either ogg or FLAC with Soundconverter...

I seem to be having a problem with this though,  when I go to convert a sample wma to ogg it seems that soundconverter freezes during the conversion process...  It places an ogg file in my music directory, but there is nothing in the file to play...
It does say that MP3 encoding isn't enabled, could this be the reason why?

I have never tried to convert anything from wma to ogg before.... am I doing something wrong?

---

### Post by cptrohn on 2009-05-04
OK, is this a DRM issue since I ripped all of my CD's with Vista... (when I still used Window$)?

Because I have my downloaded MP3's converting successfully as I type this right now.

---

### Post by logos34 on 2009-05-04
Soundconverter uses gstreamer engine--stear clear of anything that relies on gstreamer, which tends to make a [mess of vbr mp3 output]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding").

At least one person has had [your problem with wma to ogg]("https://answers.launchpad.net/ubuntu/+source/soundconverter/+question/47748") (likely many others)

Try dir2ogg:

> sudo apt-get install dir2ogg cdparanoia icedax faad python-cddb python-musicbrainz2 alac-decoder mplayer-nogui mplayer

(make sure **universe **repo is enabled)

dir2ogg -h

man dir2ogg

pkg description:

apt-cache show dir2ogg

example:
[COLOR="Red"]
dir2ogg -W -q5 -d ~/audio[/COLOR]

(--> converts all .wma file in 'audio' dir to ogg vorbis @ quality 5 (~160kbps)

hope that helps

---

### Post by teledyn on 2011-03-10
(sigh)

ERROR: wma was enabled, but no decoder has been found.

I did an aptitude search for wma and nothing obvious came up; this is using 10.10

---

### Post by omatoots on 2011-04-02
> **logos34 said:**
> Soundconverter uses gstreamer engine--stear clear of anything that relies on gstreamer, which tends to make a [mess of vbr mp3 output]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding").

At least one person has had [your problem with wma to ogg]("https://answers.launchpad.net/ubuntu/+source/soundconverter/+question/47748") (likely many others)

Try dir2ogg:



Your directions are clear and easy to follow. I am now getting .wma files out of my music folder.
Well done. Thank you.

---

