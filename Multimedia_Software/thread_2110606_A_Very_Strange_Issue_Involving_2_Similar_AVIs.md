---
title: "A Very Strange Issue Involving 2 Similar AVIs"
date: 2013-01-30
forum: Multimedia Software
---

### Post by cawilliams1983 on 2013-01-30
I am having a very rough go at something here.  Please bear with me while I try to frame the problem accurately.

I have two files (avi) of the same video.  One is in Italian, the other English.  Data-wise, the only difference I can spot between them besides the file size is that the english version's MP3 sound is encoded at 44000 instead of 48000.  I want to play the English version on my XBox 360 so upload it to a thumb-drive.  After it's loaded, I open the file in Ubuntu before ejecting the drive and everything seems fine (it in English) however, when I run it from the Xbox, it's in Italian.  After this, I loaded both files to the same thumb drive.  I checked them both in Ubuntu first and they are different but, when loaded from the XBox, they are the same..  ergo, Italian.

I am sorry if I'm not giving enough information.  If you need any just let me know.

Thanks for any help.

Once this is resolved, I will change the title (if I can) to something less vague in case anyone else has this trouble.

---

### Post by SeijiSensei on 2013-01-30
Does the video player software on the client allow you to select an audio track if more than one exists?  Perhaps that is all you need.

If you install mplayer from the repositories and run it from the command line with "mplayer /path/to/your/video.avi" it will tell you how many audio tracks are in the file, and the order in which they appear.  That might give you some clues.

---

### Post by cawilliams1983 on 2013-01-30
DLing mplayer but I checked Sound in Totem Movie Player and there are indeed two different audio tracks.  The first one is Italian..  So, now how would I go about deleting the first audio track (Xbox doesn't let you choose between multiples) before uploading the avi to a thumbdrive?

Edit:  Any idea how the two different tracks from two different files got mingled?

---

### Post by cawilliams1983 on 2013-01-30
Thank you for pointing me in the right direction, SeijiSensei!  After a google search, I found the answer to the (first) question in the last post.  andrew.46 showed how to strip unwanted audio tracks with ffmpeg in [http://ubuntuforums.org/showthread.php?t=1078746]("http://ubuntuforums.org/showthread.php?t=1078746").  Thanks again!

If you have any insight as to why they were merged, I would be much obliged to here it :)

---

### Post by evilsoup on 2013-01-30
You can use avconv (or ffmpeg, same syntax):

```

avconv -i input.avi -map 0:v -map 0:a:0 -c copy output1.avi -map 0:v -map 0:a:1 -c copy output2.avi

```'-map 0:v -map 0:a:0' tells avconv to take the video and the first audio streams, while '-c copy output1.avi' tells avconv to copy the streams (so no re-encoding) to a new file called 'output.avi'. '-map 0:v -map 0:a:1 -c copy output2.avi' tells avconv to take the video and second audio streams, and copy them to output2.avi.

it's in the repositories.

PS you may find ps3mediaserver interesting - it allows you to stream over the local network from your computer to a client device. Despite its name, it works perfectly well with the XBOX 360 too. Unfortunately it's not in the repos, you'd have to use [this PPA]("https://launchpad.net/~happy-neko/+archive/ps3mediaserver").
EDIT: ps3mediaserver will even allow you to select which audio stream you would want to use, on top of the advantage that you don't need to bother with memory sticks - I use it all the times, it's a really good program.

---

### Post by andrew.46 on 2013-02-04
> **cawilliams1983 said:**
> andrew.46 showed how to strip unwanted audio tracks with ffmpeg in [http://ubuntuforums.org/showthread.php?t=1078746]("http://ubuntuforums.org/showthread.php?t=1078746").  Thanks again!

That was certainly a few years ago, unusual to see the same FFmpeg syntax still holding, the developers can make ruthless changes with such things :)

---

