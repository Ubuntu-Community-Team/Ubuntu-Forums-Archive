---
title: "[SOLVED] authored DVD plays back fine on xine, but not on standalone player"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by wrathkeg on 2007-12-13
Dear all,
I am creating a video DVD using a kino+mandvd (using files from a Sony DVD Handycam). The resulting DVD plays fine on Ubuntu with gxine, but on my standalone DVD player, the playback is very jerky.  Any ideas what the problem might be?  If you need any additional info, please let me know and I can try to supply it. TIA,
WK

---

### Post by timcredible on 2007-12-13
maybe try another dvd authoring tool, like devede or lives or qdvdauthor or dvdstyler.  i've done plenty of home movies on camcorder to dvd by using kino and dvdstyler.

---

### Post by wrathkeg on 2007-12-13
> **timcredible said:**
> maybe try another dvd authoring tool, like devede or lives or qdvdauthor or dvdstyler.  i've done plenty of home movies on camcorder to dvd by using kino and dvdstyler.

Thanks for that response (and so quick, too).  

I've just installed DVD styler but am having the same problem:  the resulting DVD is kind of flickery when played on a standalone player, but fine on xine.   

Here's a bit more on what I did in case it helps someone identify the cause: I converted the VOB file from the Handycam to a DV file.  I edited the DV file with Kino, then exported as a generic MPEG2 file.  I then started up dvdstyler, and used the MPEG2 file as my movie, and burned the DVD from right there in dvdstyler.  Like I say, it looks fine in dvdstyler's preview (xine), but bad on the DVD player.  Any ideas, anyone?  It might be something really obvious that I am doing wrong: I am new to video stuff of this kind.

TIA,
WK

---

### Post by wrathkeg on 2007-12-13
So, anyone got any experience of this? I've read one or two things which suggests that bitrate is an issue (suggesting that some DVD players don't cope with high bitrates).  I have tried to change this in various ways (with ffmpeg, in Kino), but without success.  To be honest, I am some way out of my depth in trying to solve this, and am really just stabbing in the dark. So, any ideas?
TIA
WK

---

### Post by yabbies on 2007-12-13
I live in the usa midwest and have been hit hard by an ice storm. I just had power restored to my house(finally) but have no communications. I'm at work but leaving in about 10 minutes.

First of all check out tovid and todisc- it's not in ubuntu repos 

If you have the dvd directory that you want to burn complete with Audio_TS and Video_TS
then you can just burn the directory from a command line with

makedvd -burn* dvd_directory*

If you let me know exactly what you have in full detail I can give you a step by step to make a complete dvd with interactive menus using tovid and todisc.

---

### Post by wrathkeg on 2007-12-14
Thanks for the offer of help.  On yabbies' suggestion, I have installed tovid, and tried to get it working.  Unfortunately, no joy: the DVD is still jerky when I play it back on a standalone DVD play. Here's what I did to try to edit a file from a Sony DVD handycam (editing with Kino, burning with Tovid), and then write it to a DVD.

1. Copied across the VOB file onto the hard drive.
 ```
  cp /media/cdrom0/VIDEO_TS/VTS_01_1.VOB test.vob
```
2. Opened Kino and imported the test.vob file.  Did a little bit of trimming to the start and end.

3. Exported from Kino, via the "Export" tab.  Used file-format "8 - DVD".  Resulting file, edited-test.mpeg, looks fine on gxine.

4. Tried to make a DVD menu with tools from tovid missing out the menu for now, just for simplicity:

```
   makexml edited-test.mpeg -out my_dvd
   makedvd -burn my_dvd.xml
```

Process seems to complete without error, and plays back with gxine without any obvious signs of trouble (though I do notice one glitch a little way into the recording -- I might worry about that later):

```
   gxine dvd:/dev/cdrw &
```

Although this method seems to generate something a bit better than before, on the standalone player, the video still goes really fuzzy when the camera is 'panning'.  So, any ideas as to what might be going wrong?  Or any suggested alterations to my process to try to improve things?

In case it's relevant, this is the info outputted from ffmpeg on the test.vob file:
```

Input #0, mpeg, from 'test.vob':
  Duration: 00:00:11.0, start: 0.226767, bitrate: 6744 kb/s
  Stream #0.0[0x20]: Subtitle: dvdsub
  Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
  Stream #0.2[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 9100 kb/s, 25.00 fps(r)
```

This is the output for the edited file (hence the shorter duration, though I notice that the bitrate is different too)

```
Input #0, mpeg, from 'edited-test.mpeg':
  Duration: 00:00:07.5, start: 0.184656, bitrate: 5694 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 7500 kb/s, 25.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 224 kb/s
```

And finally, this is the output for the file on the DVD itself

```
Input #0, mpeg, from 'VTS_01_1.VOB':
  Duration: 00:00:07.5, start: 0.184656, bitrate: 5694 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 7500 kb/s, 25.00 fps(r)
  Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 224 kb/s
```

Any help with sorting this out would be much appreciated.

WK

---

### Post by ron999 on 2007-12-14
Hi
I see in your code that the video is 720x576, 25 fps.
That is the setting for a PAL DVD.
The values for NTSC are 720x480, 30 fps.

So, where you live, is your TV system PAL or is it NTSC?

---

### Post by wrathkeg on 2007-12-14
thanks for the quick reply.  I'm in the UK, so it's PAL, as far as I know (I'm a bit green on video/DVD matters.....)
WK

---

### Post by ron999 on 2007-12-14
Yup, it's PAL system in UK.

It was just a thought.
:rolleyes::mrgreen:

---

### Post by wrathkeg on 2007-12-14
> **ron999 said:**
> Yup, it's PAL system in UK.

It was just a thought.
...and i appreciate it. I really feel like I am stabbing in the dark here, so I appreciate anyone helping me, um, stab. :)
WK

---

### Post by ron999 on 2007-12-14
Hi
I use tovid too.
The first stage is to convert the file to the correct format - which I think that your Kino "Export" will have done for you.

But it might be worth doing the check with tovid. If it's correct, it will tell you so. If it's not, it will convert it.

The command I would use is:-

**tovid -pal -dvd -in** < your file > **-out movie**

And the output would be movie.mpg 
Then 

**makexml movie.mpg -out my_dvd**

8-)

---

### Post by kelvin spratt on 2007-12-14
Are you using eye candy when authoring your films?. What media are you burning cheap media gives that sort of results, I personally use cinelerra and Devede and make wedding and such like videos for people and always use Verbatim at x16, Burn with Nero or brasero.Warning Devede might need Mencoder replacing with an older version as their is a bug in ubuntu 7.04/7.10 for some people.

---

### Post by yabbies on 2007-12-14
[check this out]("http://ubuntuforums.org/showthread.php?t=617994")

I had posted a detailed tovid/ todisc to get a working dvd

just switch all the avi mentions with your vob files.
as ron has mentioned

let us know how it goes- todisc is sure to impress your family and friends

---

### Post by wrathkeg on 2007-12-15
Okay, so I have run the commands Ron suggested: and here's the proof from my command line :)

```
tovid -pal -dvd -in test.mpeg -out tovid-test
makexml tovid-test.mpg -out my_dvd
makedvd -burn my_dvd.xml
```

and things are still blurry on the standalone player. 

In response to Kelvin: I don't think the media can be the problem as I am using the same TDK mini DVD+RW that I recorded to on the Handycam itself, which played back fine.

I will try Yabbies' directions and report back.

Thanks all.  Hopefully the pain will be over soon!

WK

---

### Post by wrathkeg on 2007-12-15
Back again. The problem appeared to be that the file produced by the handycam is interlaced. Below is what I have done with success. I'm no expert (as
you can see from the previous postings....) but these details might help someone, sometime.

1. copied the VOB file across from the mini DVD to the hard drive:

```
cp /media/cdrom0/VIDEO_TS/VTS_01_1.VOB .
```

2. converted the file to a deinterlaced DV file which Kino will edit, using ffmpeg:

```
ffmpeg -deinterlace -i VTS_01_1.VOB -target pal-dv movie.dv
```

3. edited the movie.DV file with Kino, splitting into three scenes, and exporting as a MPEG suitable for DVD (option 8 from the drop-down file-format menu).

4. made a menu using the Tovid suite

```
makemenu "Part 1" "Part 2" "Part 3" -out main_menu
```

5. get the DVD ready

```
makexml -menu main_menu.mpg test000.mpeg test001.mpeg test002.mpeg -out my_dvd
```

6. burn the DVD

```
makedvd -burn my_dvd.xml
```

7. Pop it into the DVD player and enjoy.

So, I got there in the end. Thanks, all, for the suggestions.

WK

---

