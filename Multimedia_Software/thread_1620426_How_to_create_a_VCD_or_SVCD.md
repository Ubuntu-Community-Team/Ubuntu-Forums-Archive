---
title: "How to create a VCD or SVCD?"
date: 2010-11-13
forum: Multimedia Software
---

### Post by amsterdamharu on 2010-11-13
SOLUTION:
Should encode the sound as mp2 224kb 48000
So the ffmpeg command to encode the video should be:
```
ffmpeg -i in.dat -f dvd -target pal-dvd -vcodec mpeg2video -b 1200kb -r 25 -s 352x288 -aspect 4:3 -acodec mp2 -ar 48000 -ab 224kb  out.mpg"
```For other aspects you can use 16:9 there is one more but it's not DVD standard I've read somewhere.).
For NTSC you should use -target ntsc-dvd and -r 29.97

Then you can edit the out.mpg in avidemux. After that I used ffmpeg again to encode the lot just to make sure it's the right format.
Some tips when using avidemux:
1. Check the bottom of the window for something like "Frame:I(03)" You can only set your start marker on an I frame or you'll get an error trying to save the file. Use alt+left or right arrow to go through the frames.
2. When saving on the left of the window choose copy for both Video and Audio and MPEG+PS (A+V) as the format because it defaults to AVI.

Now use k3b directly to create and burn (to CD or image) the VCD. 
Or use devede but make sure when adding the files you check "This is already a DVD/xCD suitable MPEG-PS file" under the file properties "advanced options" -> misc tab

/SOLUTION:


Questions:
1. Can I use brasero to burn (image or cd) a vcd without it re-converting my video?
2. Is there a way to make k3b burn the VCD image file without an error and without deleting it after it's created?
3. Is there any software I overlooked that would allow me to create a SVCD?

I have a VCD that my school needs to use sometimes, the chapters need to be re-created because there are only 8 chapters on the VCD. One chapter consist of a story, word practise and a song. I would like the store, word practise and song to be 3 separate chapters so I can start the song directly without fast forwarding through the story and word practise. (I am using Mint 8 and have some extra stuff installed for ffmpeg to work)

Here is what I got so far: 
1. Got the video files off the CD and tried to open with avidemux (cannot open)
2. Converted the files with ffmpeg:
```
ffmpeg -i in.dat -f dvd -target pal-dvd -vcodec mpeg2video -b 1200kb -r 25 -s 352x288 -ar 48000 -ab 128kb out.mpg
```3. Now I can edit it with avidemux
4. Broke up the video's into chapters that I want
5. Start brasero and click video project
6. In the main menu choose view -> uncheck preview so it won't crash
7. Add the video files
8. In the bottom part I choose image file instead of writing to cd (think I had to install vcdimager for that option to appear)
9. Click burn
10. Select location and name of the cue file

Now I get a dialogue saying "converting video file to mpeg2". This takes forever and will eventually shut down my computer because the cpu overheats.
When I have only a 10 second video file it takes a long time and then creates the cue and bin file.
Now I play the bin file with:
```
mplayer mybin.bin
```mplayer start the video and I can see the video is in the following format:
VIDEO:  MPEG2  480x480  (aspect 2)  25.000 fps  1125.2 kbps (140.7 kbyte/s)
Now I wonder why brasero converted my mpeg-2 pal Low level standard to something that according to wikipedia is not even a standard.
[http://en.wikipedia.org/wiki/MPEG-2#DVD-Video](http://en.wikipedia.org/wiki/MPEG-2#DVD-Video)
When mplayer plays the video it looks crap, a lot worse than the original mpeg file after ffmpeg and avidemux were done with it.

Ok time to try k3b

1. Converted the video files with ffmpeg and avidemux and now have the files in the chapters I want.
2. Start k3b and choose new project -> new video cd project
3. Add one of the mpeg files and it will give me a dialogue saying:
```
K3b will create a SVCD image from the given MPEG files, but these files must already be in SVCD format. K3b does not yet resample MPEG files.
 
 Note: Forcing MPEG2 as VCD is not supported by some standalone DVD players.

```4. I choose do not force VCD
5. I click "burn" and tick "only create image file" in the "writing" tab and then "start"
6. There are the following errors:
invalid mpeg packet found at packet# 2 -- please fix this mpeg file!
[FONT=DejaVu Sans Mono]vcdxbuild returned an unknown error (code 1)[/FONT]
[FONT=DejaVu Sans Mono]7. It then proceeds to remove the binary and cue file although "remove image file" is not checked so I have no idea what the output would be.[/FONT]


[FONT=DejaVu Sans Mono]If in step 4 I choose "force VCD" and then proceed I get the same error.[/FONT]
[FONT=DejaVu Sans Mono]
[/FONT]

---

