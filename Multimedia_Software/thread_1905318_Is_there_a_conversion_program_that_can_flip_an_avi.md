---
title: "Is there a conversion program that can flip an avi file 180 degrees?"
date: 2012-01-06
forum: Multimedia Software
---

### Post by rocksockdoc on 2012-01-06
I have an avi file that I can play on the default Totem Movie Player 2.30.2 on Ubuntu but the avi is literally upside down.

Is there a conversion program that can flip the avi file 180 degrees?

---

### Post by SeijiSensei on 2012-01-06
The **smplayer** video player can rotate the image by 90/180/270 degrees during playback.  No conversion required.

---

### Post by rocksockdoc on 2012-01-07
> **SeijiSensei said:**
> The **smplayer** video player can rotate the image by 90/180/270 degrees during playback.  No conversion required.

When I installed SMPlayer from the Ubuntu Software Center, it came up with the following error:
> The version of MPlayer (SVN r1) installed on your system is obsolete.
SMPlayer can't work well with it: some options won't work, subtitle selection may fail...
Please, update your MPlayer

Interestingly, there is no option for "MPlayer" in the Ubuntu Software Center.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210380&stc=1&d=1325922995[/IMG]

---

### Post by rocksockdoc on 2012-01-07
Interestingly, MPlayer appears to install 'with' smplayer - so - the Ubuntu archives must be installing 'old' versions.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210381&stc=1&d=1325923601[/IMG]

Nonetheless, smplayer resolved one of my problems which was how to play subtitles:

[LIST]
[*][ubuntu] [What 'magic' is needed to play a movie with subtitles (when srt files exist)?]("http://ubuntuforums.org/showthread.php?t=1905312")
[/LIST]

---

### Post by rocksockdoc on 2012-01-07
Despite the one-time error message, smplayer does seem to rotate files which solves the dilemma.

This rotation is persistent; but it's only honored (AFAIK) by smplayer itself.

Since this works, I'll mark this as solved. Thanks for the help.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210382&stc=1&d=1325924756[/IMG]

---

### Post by rocksockdoc on 2012-01-09
I found a very nice more permanent method of flipping a video file 180 degrees.

Googling for a better solution, I found DeVeDe, a video DVD creator:
$ sudo apt-get install devede

Among many other options, DeVeDe will rotate and create a new video file (whether AVI,  or MP4, or DVD ISO) from the original video file.

In DeVeDe, you simply load the original video file and select the rotation options, e.g.,
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210489&stc=1&d=1326104947[/IMG]


This rotation will be permanent, in the sense that any hardware dvd or video player will always play the file in the rotation you've selected.

Here is a good help file for using DeVeDe for rotation and other video conversions:
- [URL="http://files.majorsilence.com/devede/docs/file.html"]How to use DeVeDe on Ubuntu to permanently rotate video files
[/URL]

---

