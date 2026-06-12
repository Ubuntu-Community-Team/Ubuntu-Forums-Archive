---
title: "convert command not working in ubuntu"
date: 2010-01-19
forum: Multimedia Software
---

### Post by tvkpz on 2010-01-19
Hi

I am trying to use 'convert' in command prompt to convert image file format.

I get the following error. Any advice what is wrong?

convert: UnableToOpenConfigureFile `delegates.xml' @ configure.c/GetConfigureOptions/589.
convert: NoDecodeDelegateForThisImageFormat `airplane.jpg' @ constitute.c/ReadImage/530.
convert: MissingAnImageFilename `airplane.ppm' @ convert.c/ConvertImageCommand/2838.

Thanks in advance for any replies.

---

### Post by ron999 on 2010-01-19
But what is the command that you're using?

---

### Post by blackened on 2010-01-19
I'm with ron, it sure seems like you're issuing the command incorrectly or you're trying to work on an unsupported image format.

---

### Post by tvkpz on 2010-01-19
Hi

The command I issue is

$convert image1.jpg image1.ppm

I think it cannot be simpler than that.

I tried reinstalling image magick. But I do not know why this problem.

Is it that I installed some other software that may have caused some problems. I have installed FFMPEG (compiled from source) and OpenCV and they are working fine.

---

### Post by marsanyi on 2012-09-12
I had the same problem with Ubuntu 12.04, after upgrading.  I think it's a packaging issue.  The files that ImageMagick is looking for were in a directory, /usr/share/lib/ImageMagick-6.5.6/config...  I uninstalled and re-installed ImageMagick from the current ppas (packages imagemagick-common first, then imagemagick, then imagemagick-doc), but no go: still getting 6.5.6 for the version, even though the package manager reports 6.6.9 as the version installed.

which convert

showed /usr/local/bin/convert.  So I renamed that to something else, and reinstalled.  Now

which convert

showed /usr/bin/convert, and

/usr/bin/convert -version

showed 6.6.9.  I can now run /usr/bin/convert and everything works as expected.

Short answer:
[LIST]
[*]uninstall imagemagick and imagemagick-common in Synaptic
[*]remove or rename /usr/local/bin/convert
[*] install imagemagick-common and imagemagick
[*] use /usr/bin/convert to run it
[/LIST]

I'm adding a symlink to mine so I can omit the path.

---

