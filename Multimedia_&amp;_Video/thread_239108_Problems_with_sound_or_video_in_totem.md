---
title: "Problems with sound or video in totem"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by glennric on 2006-08-18
I did a fresh install of Dapper on my wife's computer and am having trouble getting avi files to play properly in Totem.  This is not a codec issue.  All of the possible codecs are installed.  If I install totem-xine then the video works, but the sound is horrid.  If I install totem-gstreamer the sound is fine, but the video won't play.  MPlayer plays all files fine, but no dice in Totem.  This seems to be a common problem.  I have searched the forums and found several posts about these issues and there are working solutions.  There are lots of suggestions about going to the Restricted Formats page and installing codecs and blah blah blah.  Obviously there is a more serious problem with Totem and its codecs in Dapper.  On my own computer I dist-upgraded from Breezy and for some reason these problems are not occurring.

Some attempts at solving the problem:

I noticed that there was no file /etc/asound.conf and so I copied this file over from my computer.  After doing this I was able to select ALSA in gstreamer-properties and the test worked.  That didn't work before.

I attempted to play the avi file with totem from the command line to look for errors.  I get the same output on both computers.  Namely a list of dll's that are being loaded.  No errors.

I also tried the suggestion at [http://ubuntuforums.org/showpost.php?p=136306&postcount=2]("http://ubuntuforums.org/showpost.php?p=136306&postcount=2").
This did nothing.

Any ideas?  This is too common of a problem.  Someone needs to figure this out and add it too the Restricted Formats.

---

### Post by glennric on 2006-08-19
Now I am having the same problems on both computers with avi files played in totem.  I killed esd (I had both esd and alsa running) and now totem sucks on both computers.  I tried rebooting and putting alsa and esd back the way they were, but to no avail.  Sound for avi files in totem sucks.  I don't know why sound was working right with avi's on my computer before, but I can't get it back the way it was.

---

