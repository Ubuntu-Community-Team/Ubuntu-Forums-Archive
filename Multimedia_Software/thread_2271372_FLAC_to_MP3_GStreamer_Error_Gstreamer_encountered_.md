---
title: "FLAC to MP3: GStreamer Error: Gstreamer encountered a general stream error"
date: 2015-03-29
forum: Multimedia Software
---

### Post by Roy_Bettle on 2015-03-29
Long story much shorter, I have a beautiful FLAC copy of Beethoven's 5th Symphony and my lovely wife has asked me to burn a CD for her truck.  Fired up SoundConverter, loaded the files, "General stream error".  The CLI read out is below.  I've confirmed that I'm running every package/plugin that I can find (good, bad, ugly), tried running it with gksudo ... nothing.  Source is a ZFS partition, destination is a folder in my home directory so permissions never should have been an issue.  What am I doing wrong?  Does it have something to do with the AAC GStreamer element missing?  If so, how do I find that as I can't seem to locate any plugin packages that I don't already have yet that error keeps showing up.  Maybe reinstall something?  Thanks!

```
roy@UbuntuMedia:~$ gksudo soundconverter
SoundConverter 2.0.4
  using Gstreamer version: 0.10.36
  using 8 thread(s)
  using gio
  "faac" gstreamer element not found, disabling AAC output.
Queue start: 1 tasks, 8 thread(s).
Queue done in 0.023s (1 tasks)
Queue start: 1 tasks, 8 thread(s).
Queue done in 4.337s (1 tasks)
/usr/lib/i386-linux-gnu/soundconverter/python/soundconverter/ui.py:1509: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  gnome.init(name, version)
/usr/lib/i386-linux-gnu/soundconverter/python/soundconverter/ui.py:1509: Warning: Attempt to add property GnomeProgram::display after class was initialised
  gnome.init(name, version)
/usr/lib/i386-linux-gnu/soundconverter/python/soundconverter/ui.py:1509: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  gnome.init(name, version)


Error: <b>GStreamer Error:</b>
GStreamer encountered a general stream error.
<i>(01 - Symphony No.2 in D, Op.36 1. Adagio molto - Allegro con brio.flac)</i>



```

---

### Post by Roy_Bettle on 2015-03-29
Never mind.  Problem found, fix applied, converting just fine now.  Turns out the approved SoundConverter (2.0.4) is a few years out of date, and buggy as hell, and the current version (2.1.5) works flawlessly.

---

### Post by Yellow Pasque on 2015-03-29
Why are you trying to convert to mp3 for burning a CD? You don't need to do that (unless you're talking about some special CD player that can play mp3's from a data disc). FLAC -> mp3 just loses audio quality.

---

### Post by Roy_Bettle on 2015-03-29
12-year old CD player in the truck won't work with the newer formats.  Or at least that's my working theory after trying to burn FLAC -> CD and not having it work in the truck's CD player.

---

### Post by Yellow Pasque on 2015-03-30
What are you using to burn? Brasero?
I use xfburn and haven't had any issues with FLAC (at least not any more than normal since old school CD players can be kind of finicky in my experience). You could even do a quick conversion to wav before burning if brasero is having issues with FLAC.
```
sudo apt-get install libav-tools
avconv -i file.flac file.wav
```

---

### Post by Roy_Bettle on 2015-03-31
Actually, I don't have a burner in my media server (where I was doing the conversions) so as much as it pains me to admit it, I was using my Winblows laptop to burn the CDs.

---

### Post by mc4man on 2015-03-31
If burning on windows then you'd need to account for that windows doesn't support flac. So either - 
convert flac to wav in Ubuntu, then use those wav file(s) to burn to audio cd, or
enable flac support in windows, installing madFlac codec will do that (ver. 1.10 should be fine

---

### Post by Yellow Pasque on 2015-03-31
^Yeah, that.
If it's something you're going to use often, I think you can add FLAC support in Windows: [http://www.howtogeek.com/howto/13843/how-to-play-flac-files-in-windows-7-media-center-player/](http://www.howtogeek.com/howto/13843/how-to-play-flac-files-in-windows-7-media-center-player/)
At least Windows 10 will finally have FLAC support out of the box...

---

### Post by Roy_Bettle on 2015-03-31
Yeah ... Winblows 10 ... because that will finally solve all those problems we've been dealing with since Winblows 95.  =)

---

### Post by Keith_Helms on 2015-04-01
> **Temüjin said:**
> Why are you trying to convert to mp3 for burning a CD? You don't need to do that (unless you're talking about some special CD player that can play mp3's from a data disc). FLAC -> mp3 just loses audio quality.

> 12-year old CD player in the truck won't work with the newer formats.   Or at least that's my working theory after trying to burn FLAC -> CD  and not having it work in the truck's CD player.

I think you missed the point.   The idea was not to use some newer format, like Ogg Vorbis or whatever.   If you're just burning a single album from FLAC to CD why not convert back to Wav and burn it as a standard audio CD?

```
ffmpeg -i inputfile.flac output.wav
```

---

### Post by mc4man on 2015-04-01
for  a simple flac to wav I'd just use flac as it doesn't use an output filename parameter, just copies the .flac name exactly. So cd to folder holding the .flac's >
```
flac -d *.flac
```
If you wanted to quickly separate out, at same prompt after above finishes - 
```
mkdir wav && mv *.wav ./wav
```

---

