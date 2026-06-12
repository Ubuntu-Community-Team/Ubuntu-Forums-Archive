---
title: "mencoder this is it for me"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by tbuss on 2007-05-07
I'm fairly new to linux, and I would like to convert videos that I capture with kino to a smaller file size and compatible type for all os's. I would like to place these video's on my website. I have tried to use mencoder for the past couple of weeks. I have yet to get a video on my site that plays correctly or at all.  If the video does play it's up-side-down, or if I test in IE it prompts about a missing codec, even if I converted to wmv, and avi, most likely the sound codec I used maybe? FF seems to have other issues, another thread. 
I have read:
[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-video-for-windows](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#menc-feat-video-for-windows)
[http://en.wikipedia.org/wiki/MEncoder](http://en.wikipedia.org/wiki/MEncoder)

I just can't figure this out. All I would like to do is simply take a file that is large and make it smaller. This is what I have tried, but nothing works.
```
mencoder ffmpeg -i brynleeBeaDancing.avi -vcodec wmv1 brynleeBeaDancing.wmv
mencoder brynleeBeaDancing.avi -o brynleeBeaDancing.wmv -ovc lavc -oac lavc
mencoder beaBrynleeDancing.dv -ovc lavc -oac lavc -ffourcc DX50 -o brynleeBeaDancing.avi
mencoder brynleeBeaDancing.wmv -o test.avi -ovc lavc -oac mp3lame
mencoder brynleeBeaDancing.wmv -ovc lavc -ffourcc DX50 -0 brynleeBeaDancing.avi
mencoder brynleeBeaDancing.wmv -ovc lavc -oac lavc -ffourcc DX50 -o brynleeBea.avi

```

---

### Post by tbuss on 2007-05-11
I figured out that Linux sux when it comes to anything with video. My solution to anyone that wants to do anything with video is to dual boot with windows and use that to do all your editing, capturing, compressing, converting, authoring etc. That way, instead of wasting your time fixing apps, looking for dependencies, reading useless man pages, searching for hours only to have someone try to give you an education on how video works, just use windows to do what you have to with the video and be done with it. Unless you are one of those people that does not have a life other than the one spent behind a computer for hours upon hours. Of course you might be called a slave to microsoft, but then again I guess I'm a slave to other companies as well, Electric, Water, Oil, you get my point.

---

### Post by Quicky on 2007-05-17
Cheer up son.

What's the problem with exporting your raw dv files from within kino? I use kino to capture video from my handycam (which creates enormous raw dv files), and then use the export function to convert them to mpegs or avis which are obviously a fraction of the size of the dv. There's no need to use mencoder.

---

### Post by tbuss on 2007-05-17
Quicky,

I finally figured out how use Kino to it's fullest; wish you would have posted earlier. I think I had a small mental breakdown :-&

What I really want to do (and why I was using mencoder) is to place video on my site. I need to compress the video and also convert it to a format than can be played in wmp. I have a small family web site and my parents use windows. Asking them to download a codec via a link provided on the site is not an option; only ends in tragedy :-s Having them install VLC on their windows box is equally tragic.

I haven't tried to export the raw dv files to avi in Kino yet, if this is done what options do you use. I'm trying to avoid the MPEG-4 Video or (FMP4) that was produced when using mencoder; this is not a true avi files and requires a codec to be played in wmp.

---

### Post by Quicky on 2007-05-18
No worries. To export your DV to an mpeg you can do the following once you've captured the DV from your camcorder (which I assume you've done before).

Open up one of your DV files in Kino and click the Export button on the right hand side. Kino presents you with five tabs to let you select which format you'd like to export to. Click the MPEG tab, and you should get some options below. Give the output file a name (in the text box – I believe the file will be created in the home folder by default), then choose the file format (0 – Generic MPEG1) is the one I use. The remaining settings can be left alone, then at the bottom of the screen, hit the Export button.

It will take some time to export, but once complete you should have a single .mpeg file. Occasionally I've noticed that when Kino is performing the export and it creates the two temporary files (audio and video) it fails to merge them into the final mpeg, but when this has happened I've just run it again and its been fine. To be honest, that's probably just an issue with my machine.

It might also be worth checking that you have mjpegtools and ffmpeg installed in synaptic. I remember that I had problems when I first tried this export function and it was because I was missing some program or other from the repositories, and am I'm relatively sure it was one of those two – don't quote me though. Let me know how you get on.

---

### Post by tbuss on 2007-05-19
I tried as you suggested. I captured the raw dv files from my camcorder; ended up being about 16 different clips. I then exported the files using 0 – Generic MPEG1. I chose frame from 0 to 108404; the full 60 mins. However, after the export was completed the mpeg file was only 166 MB and it only exported 11 minutes 48 seconds of the captured dv files (aprox frame 0-21000 of 108404)

Any suggestions? What was exported worked as advertised, I would like to export the full dv tape however.

---

### Post by Quicky on 2007-05-20
Yeah, I was hoping it would work okay for you because I had the same problem originally and I'm not entirely sure what I did to fix it. I can tell you some of the things that I did, and with any luck you'll have some success.

Firstly, the video being split into multiple DV clips won't be too much of an issue because you can join clips easily enough. You may have done this already, but just in case, once you've opened your first clip you can hit the 'insert a file after the current scene icon', 6th from the left on the toolbar, and add one of your other clips. You should end up with a number of thumbnails in the storyboard panel on the left. Do that with all the clips you need (putting them in the correct order), then hit the 'join' icon, 2nd from the right, to merge the clips and each of the scenes in each clip (if applicable). Once all your clips have been merged, you should only have one thumbnail in the storyboard.

In order to get around the the partial export problem, you might also want to try exporting to a different file format, perhaps 3 – Generic MPEG2. I hate to say 'try playing with settings' but unfortunately that's pretty much what I did – there is a bit of trial and error involved with Kino (especially when it comes to editing) but it will work for you eventually.

Bear in mind that I have only ever exported to 0 – Generic MPEG1 or  3 – Generic MPEG2 (most of the time it was MPEG2 actually), so I wouldn't worry about trying any other formats. Both of these will play in any standard media player.

Finally, I also played about with the duration part of the export function, where it says 'Every 1 frame of All', and changed the dropdown options to 'Every 1 frame of 0 to *the last frame number*'. Don't know if that made any difference, but its worth trying.

---

### Post by tbuss on 2007-05-20
Quicky,

I was in the process of exporting when I received a notice that you had replied. 

I did something similar to what you had suggested, the end results were a 1.8 GB 3 - Generic MPEG2 file for a 59 minutes 25 seconds long video.

*After using Kino to grab the raw dv files:*

Instead of placing each frame individually on the storyboard by using 'insert' I just drag and drop all the files (17 clips total) from my video folder onto the storyboard. The files were named 5-2007002.dv, 5-2007003.dv etc (so there is no need to rearrange). All files are now loaded on the storyboard. Then I clicked on 'timeline' and edited the start and end values and hit 'ok'. (for me it was start: 0 end: 108404.) Then I clicked on 'export'.  I also edited the Frame from/to values using 0-108404.

**Export options used: **
file format: 3 - Generic MPEG2
Deinterlace: Internal Deinterlacer (Very fast)
**Advanced Options (default)**
Video Pipe: mpeg2enc -v 0
Audio Encoding: mp2enc -v 0
Multiplexer: mplex -v 0

The timeline sequence I had left out in previous steps; I thought what the heck and it worked. It seems as though we have used the same steps except for one, you used 'join' and I used the 'timeline'. Perhaps adjusting the start and end values on the 'timeline' has the same effect?

Just want to say it was very cool of you to help. It's seems I have come a long way from my initial post ;)

---

