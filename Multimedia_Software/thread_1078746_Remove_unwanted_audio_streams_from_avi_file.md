---
title: "Remove unwanted audio streams from avi file"
date: 2009-02-23
forum: Multimedia Software
---

### Post by paulhurleyuk on 2009-02-23
I have several avi files that I want to use in mythvideo. The problem
is that they have two audio tracks (german and english), and I want the second one. 

The mythtv wiki suggests that it's possible to use ffmpeg and mpeg demux
to remove any unwanted audio streams, but it doesn't seem to work with
my avi files (I don't get the same output from ffmpeg, and mpegdemux
complained about the wrong streams)

Ideally, I'd love a command line tool I can feed avi files to to strip the first audio track off.  Any one else knows what to do ?

Thanks

Paul.

---

### Post by andrew.46 on 2009-02-24
Hi,

FFmpeg can copy the audio and video streams of your choice by using the -map option. Can you run:

```
ffmpeg -i myfile.avi
```

to demonstrate the existing structure of the file?

Andrew

Edit: A nice explanation of how mapping works in FFmpeg can be [seen here]("http://howto-pages.org/ffmpeg/#map").

---

### Post by paulhurleyuk on 2009-02-24
Here's the response.  I'll try the guide you linked.  Thanks.

```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.     
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from 'house_s01e02.avi':
  Duration: 00:43:12.3, start: 0.000000, bitrate: 1265 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tb(r)
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
    Stream #0.2: Audio: mp3, 48000 Hz, stereo, 96 kb/s
Must supply at least one output file
```

---

### Post by andrew.46 on 2009-02-25
Hi paulhurleyuk,

> **paulhurleyuk said:**
> 
```

Stream #0.0: Video: mpeg4, yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tb(r)
Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Stream #0.2: Audio: mp3, 48000 Hz, stereo, 96 kb/s

```

You could try:

```
ffmpeg -i input.avi -map 0:0 -vcodec copy -map 0:2 -acodec copy output.avi
```

with the obvious substitutions for inputfile.avi and outputfile.avi.

Andrew

---

### Post by scottro on 2010-03-04
I realize this is an ancient thread, but just wanted to give thanks to Andrew for his one liner.  Works perfectly for me.

---

### Post by Jofarmer on 2010-08-21
I have to disagree: I tried this approach and avidemux-gtk and both added little audio cracks to the sound. It seems as if they chopped the video into tiny parts and reattached it with one audio stream less, but the glueing didn't work so good. Also, ffmpeg changed the speeds, video is faster now than audio. From the output:```
Seems stream 0 codec frame rate differs from container frame rate: 
23.98 (65535/2733) -> 23.98 (2997003/125000)
```So there are two different kinds of 23.98fps? The input.avi is without any cracks in the audio and a/v perfectly in sync. Can anybody give me some advise on how to retain that quality and still delete the 1st audio stream?

---

### Post by JC Cheloven on 2010-12-13
Well, decimal numbers represented as quotient of integers often are inexact. Thus, none of your reported quotients is exactly 23,98:
65535/2733= 23,9791
2997003/125000= 23,9760
This small difference is enough to cause the out of sync you noticed, being more noticeable as time passes.

> It seems as if they chopped the video into tiny parts and reattached it with one audio stream 
It's in fact as it works. Is what the container is for: taking small portions of video (which may be encoded with any codec), and packaging it with its portion of audio. FFmpeg is reporting in your case that the frame rate specified in the container does not exactly match the frame rate specified in the encoding (ie, used by the codec).

So, in your case, you'll probably need to force the frame rate of the output file with the -r option (to some of the above values?). Or perhaps you'll need playing with codec specific parameters. Please type "man ffmpeg" at terminal for documentation. In any case, the "map" is the core feature for what you want to do.

Also, Andrew's one liner worked fine for me with the file below (output from ffmpeg -i myfile.avi). Perhaps some difference with yours may give you a clue:

```
  Duration: 01:28:51.72, start: 0.000000, bitrate: 1355 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x368 [PAR 1:1 DAR 40:23], 23.98 tbr, 25 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 192 kb/s
    Stream #0.2: Audio: mp3, 44100 Hz, stereo, s16, 192 kb/s
```

---

### Post by cbanakis on 2011-02-07
OK, I know this thread is very old, but I figured out a great solution, and its not every day that I have a chance to contribute.

What is needed...

MKV files creator
openoffice spreadsheet
any text editor
terminal

How to do it... 

1. Open the first of the series of files you want to remove a track from in MKV files creator.  (I had avi files, the only consequence is that they are mkv now)
2. Select all options I wanted.  (Deselected the track I did not want) (Audio Track 1)
3. Hit "Copy to clipboard"

This is what I got...
("mkvmerge" -o "/Path To Output File/Output File Name.mkv"  "--forced-track" "0:no" "--forced-track" "2:no" "-a" "2" "-d" "0" "-S" "-T" "--no-global-tags" "--no-chapters" "/Path To Input File/Input File Name.avi" "--track-order" "0:0,0:2")

4. Brake this up, and paste into openoffice spreadsheet.  (File names excluding extension in separate fields)

example  ("|||" = new cell)

("mkvmerge" -o "/Path To Output File/|||Output File Name|||.mkv"   "--forced-track" "0:no" "--forced-track" "2:no" "-a" "2" "-d" "0" "-S"  "-T" "--no-global-tags" "--no-chapters" "/Path To Input File/|||Input  File Name|||.avi" "--track-order" "0:0,0:2")

5. Duplicate that line in openoffice for however many files you have (Assuming the path is the same for all files)
6. Copy and paste file names into new spreadsheet.  (find and replace .avi with nothing)
7. Copy and past file list over the duplicated file names in command spreadsheet.
8. Select All, Copy and paste into text edit
9. Select and copy a tab, then find and replace tab with nothing
10. Copy all, and paste in terminal.

11. Find something to keep you occupied for a while

12. Done :)

Please let me know if this helps anyone

It looks much more complicated then it is.

Its basically just a lot of copy and paste

I hope I help someone

Mine error-ed out a couple times, but I was running to and from a network drive, and had it delete an audio track from about 100 files.

So others probably wont have that issue.

Even with the errors, it saved me SEVERAL hours.

To recover, I just reopened the spreadsheet, and deleted the lines for all the completed files, then ran it again.  (No Biggy)

---

### Post by cbanakis on 2011-02-07
Solved?

---

### Post by ortermagic on 2011-03-31
Hi cbanakis,

Thanks for your help....I am finally able to post, having finally navigated the getting into Ubuntu forums maze, for the first time.
I wanted to make a comment because of the timely nature of your post, I have just started to use KDenlive as a video editor  and got very fed up with the audio on one of my AVI's which i could not delete within KDenlive.
 So i googled around till I found your helpful solution...The thing is, I was able to get the desired effect simply by pasting the clipboard results directly into a terminal, rather than doing all that spread sheet stuff.  I wonder why?
 Thanks for your helpfulness nonetheless   =D>

---

### Post by ortermagic on 2011-03-31
I'm back....With a problem, I knew it was too good to be true...
After stripping out the audio from my AVI clip, then ripping a music track to put with the video, I found that after rendering the re-edited video using KDenlive the resultant audio quality was nothing like smooth. 
The sounds I ended up with were the audio equivalent of *blocky*!
Which means to me that there's something within that I didn't get right.
I'm a bit nervous about doing all that cut and paste into a spreadsheet ** cbanakis**, because I am unfamiliar with spreadsheet functionality.
   I'm not asking for help but if there's anyone out there who knows what's happening I would appreciate any (simple) advice :(

---

### Post by ortermagic on 2011-04-01
Back so soon ....to inform anyone interested that after rendering my video I found that it worked just fine...ie: I was successful in stripping audio out of my avi and the end product was just fine. So thanks again ** cbanakis** for your valuable help. My video is now on youtube[B] :P

[/B]

---

### Post by Mariane on 2011-05-19
mkv does not work for me, when I try to add the avi file it does not appear in the list of supported files... 

Mariane

---

### Post by ortermagic on 2011-05-23
Hi there sorry about the delay. My solution (I tend to stumble around rather blindly, without much inside know how) My solution was to drag the MKV file created directly onto the Kdenlive dropspot,  it worked! 
Then, all I needed to do was put the resultant MKV on the Kdenlive time line, go to CLIP, select split audio, drag the audio on to an audio path (No3) then delete it. Doing this enabled me to create a silent video on to which I was able to impose my own soundtrack. 
I had a similar non recognition flag when I tried to import via the add function.
Hope that helps.

---

