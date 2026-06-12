---
title: "Unable To Encode MP3"
date: 2009-10-09
forum: Multimedia Software
---

### Post by derklempner on 2009-10-09
I've checked all my installed packages; I've got the newest versions of lame and gstreamer.  Yet every time I type the following command:
```
ffmpeg -formats
```
the line for mp3 codecs displays:
```
D A    mp3             MP3 (MPEG audio layer 3)
```
and I'm unable to encode anything in MP3 format.

I've been having some problems with WinFF and mencoder to convert various old MOV files to AVI format.  Every indication points to the absence of a valid MP3 encoder that is causing the conversion to fail.  Yet when I use programs like Rhythmbox to encode CDs into MP3 format, it magically happens.

Anybody have any suggestions/ideas?

---

### Post by FakeOutdoorsman on 2009-10-09
This is a very common question here at the forums and is explained here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by derklempner on 2009-10-10
> **FakeOutdoorsman said:**
> This is a very common question here at the forums and is explained here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)
I've already got ffmpeg and ubuntu-restricted-extras installed.  I even double-checked them again with an apt-get, and they're the current versions.

I'm still stuck, sorry to say.

---

### Post by cotcot on 2009-10-10
What is the application that fails to encode mp3 ? Maybe it uses its own ffmpeg (or something else) instead of the ffmpeg you have installed by default.

---

### Post by FakeOutdoorsman on 2009-10-10
> **derklempner said:**
> I've already got ffmpeg and ubuntu-restricted-extras installed.  I even double-checked them again with an apt-get, and they're the current versions.

I'm still stuck, sorry to say.

For Jaunty and newer, FFmpeg uses libmp3lame as the mp3 encoder:
```
$ ffmpeg -formats | grep lame
...
  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
```
If you have this line you're set to encode with FFmpeg directly.  With WinFF you may have to update your presets.  Maybe paul.gevers can show up and give you instructions for that if that is the case.

---

### Post by paul.gevers on 2009-10-11
> **FakeOutdoorsman said:**
> With WinFF you may have to update your presets.  Maybe paul.gevers can show up and give you instructions for that if that is the case.

If indeed your winff presets are using mp3 as the codec you are using old an old preset file. If you started using winff a long time ago, you will have old presets in ~/.winff/presets.xml (which were copied on first use) which do not get updated when you update winff. You can use the latest presets by removing this file. If you created presets yourself you will have to manually merge the new and old presets. (Export your own presets, remove the file and import your exported presets again).

See also the [winff wiki]("http://code.google.com/p/winff/wiki/InstallPresetsxml")

---

