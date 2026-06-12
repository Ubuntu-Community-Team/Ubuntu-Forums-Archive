---
title: "How do I concatenate videos, adding a gap between each, using ffmpeg?"
date: 2023-02-12
forum: Multimedia Software
---

### Post by Paddy Landau on 2023-02-12
I want something very simple. I want to concatenate a few videos, but leave a brief gap (about half a second) between each.

The videos all have the same format (video dimensions and codecs), and so I don't need any conversion.

To concatenate without a gap is straightforward ([FONT=courier new]video.list[/FONT] is a text file containing a list of the videos in the format [FONT=courier new]file 'video 1.mp4'[/FONT] etc.):
```
ffmpeg -f concat -i videos.list -codec copy output-video.mp4
```
Now, how can I do the same but leave a brief gap between each video? The gap doesn't have to be exactly half a second; an approximate value will do.

Thank you

---

### Post by TheFu on 2023-02-12
I'd create a silent/black clip of the same size and length as the others, then I'd use mkvmerge to concatenate the clips in whatever order I needed.  If the clips aren't truly  using the exact same settings for both audio and video, this won't work.  You'll need to transcode.

There's a GUI for mkvmerge in the mkvtools ... I seldom use it.  You can also use ffmpeg, but the concatenation with ffmpeg is cumbersome.  I have a script that will concatenate sequential files nicely ... er .... it will generate a bash script with mkvmerge commands to be run.  Filenames cannot have spaces since inputs are parsed looking for *-01* with either mkv or mp4 extensions.  Here's that script:
```

#!/bin/bash

if [ "X$1" = "X" ] ; then
  echo "Usage: $0 file-01.mkv"
  exit 1;
fi

for filename in "$@"; do

   ROOT=`echo "$filename" | sed -e 's/-01.m[pk][4v]//g'` 
   CNT=1
   if [[ $(echo "$filename" | grep -c 'mkv$') -eq 1 ]] ; then
      EXT="mkv"
   elif  [[ $(echo "$filename" | grep -c 'mp4$') -eq 1 ]] ; then
      EXT="mp4"
   fi
   OUT="ionice mkvmerge -o \"$ROOT.mkv\" \"$ROOT-0$CNT.$EXT\" "
   
   for CNT in {02..99} ; do
     if [ -f "$ROOT-$CNT.$EXT" ] ; then
       OUT="$OUT + \"$ROOT-$CNT.$EXT\""
     fi
   done
   
   echo $OUT 
  #  echo $OUT | sh -
done

```

If you swap the last 2 echo lines (comment 1, not the other), then you can run the script automatically.  I've been doing this for some time. It is safe.

---

### Post by Paddy Landau on 2023-02-12
> **TheFu said:**
> … mkvmerge
Thank you for this. I installed [FONT=courier new]mkvtoolnix[/FONT], and then experimented with [FONT=courier new]mkvmerge[/FONT], using your script as a template.

Unfortunately, it created the same output as [FONT=courier new]ffmpeg[/FONT] did, i.e. without any gaps, but worse, the video was on its side :( (The videos were all filmed in portrait mode, if that's of any significance.)
> **TheFu said:**
> I'd create a silent/black clip as the others…
This gives me an idea. I'll create a silent, black clip a half-second long, and insert that between each clip in my [FONT=courier new]ffmpeg[/FONT] command. I'll try that tomorrow, as it's late here and I need to finish up.

First, I just need to figure out how to make that silent, black clip in the right dimensions and with the right encoding!

---

### Post by TheFu on 2023-02-12
> **Paddy Landau said:**
>  
First, I just need to figure out how to make that silent, black clip in the right dimensions and with the right encoding!

ffmpeg can take any image and convert it into a clip. So, you just need to take a black image use it 30 or 60 times to get 1 second (30pfs, right?) and have ffmpeg create the detailed resulting clip.  To learn the exact encoding parameters - this is very important - I be one of the ffmpeg tools or mplayer -I can dump that information.

Portrait?  Eeeew.  Nasty.  I've never understood why anyone would do that for video. Must be a phone thing.  Even in the old days using a Nokia N800, I'd transcode to 240p xvid and watch the videos sideways ... like a 16x9 TV.

---

### Post by Paddy Landau on 2023-02-13
> **TheFu said:**
> Portrait? Eeeew. Nasty. I've never understood why anyone would do that for video.
I agree! It's a pain, because there is so much extraneous pointless space above and below, while the left and right areas that would have been useful are just black bars. But, alas, this isn't under my control.

My son thinks that it's because people look at their phones in portrait, and instinctively film it that way. I suppose that might be the case.
> **TheFu said:**
> ffmpeg can take any image and convert it into a clip.
I completely forgot about that!

I did this, which worked, but…

… when playing the concatenated video in VLC, each time the spacer comes around, VLC re-displays the title of the video (as it does right at the start), but with the text distorted through stretching. It's horribly distracting, especially as this is an instruction video with a demonstration that needs to be followed.

The video properties, according to Nautilus, are:

[LIST]
[*]Dimensions 640×352
[*]Codec H.264
[*]Frame rate 30fps
[*]Bit rate 1838 kbps
[/LIST]
You'll notice that the dimensions are given in landscape. I think that the phone saved the videos in landscape, but included metadata to tell the player to rotate the video into portrait.

I created a file, [FONT=courier new]Spacer.png[/FONT], with the dimensions 352×640. To create the spacer clip of a half of a second, I used this command (I got the command from the internet, because I don't really know what I'm doing):
```
ffmpeg -loop 1 -i Spacer.png -c:v libx264 -t 0.5 -pix_fmt yuv420p -vf scale=352:640 Spacer.mp4
```
I created a file, [FONT=courier new]video.list[/FONT], which contains the list of files as follows:
```
file 'video 1.mp4'
file 'Spacer.mp4'
file 'video 2.mp4'
file 'Spacer.mp4'
file 'video 3.mp4'
file 'Spacer.mp4'
file 'video 4.mp4'
file 'Spacer.mp4'
file 'video 5.mp4'
```
This is my command to concatenate the videos:
```
ffmpeg -f concat -safe 0 -i video.list -codec copy 'Concatenated.mp4'
```
Do you notice what I did wrong?

---

### Post by TheFu on 2023-02-13
Used ffmpeg, not mkvmerge?
Filenames have spaces?
Not the exact same video encoding parameters as the phone videos in the spacer.

---

### Post by Paddy Landau on 2023-02-13
> **TheFu said:**
> Used ffmpeg, not mkvmerge?
Because of the problems that I previously mentioned.
> **TheFu said:**
> Filenames have spaces?
Sure. Why not? (The original names are different, but for privacy reasons, I just used "video 1" and so forth here.)
> **TheFu said:**
> Not the exact same video encoding parameters as the phone videos in the spacer.
Do you know how I correct that? I am a bit of a dummy when it comes to encoding.

---

### Post by TheFu on 2023-02-13
> **Paddy Landau said:**
> Because of the problems that I previously mentioned.

Sure. Why not? (The original names are different, but for privacy reasons, I just used "video 1" and so forth here.)

Do you know how I correct that? I am a bit of a dummy when it comes to encoding.

Spaces break everything all the time. Just avoid them or be prepared to run in to dumb issues.
If I didn't encode the files, then I don't have any 100% certain method to know all the settings.  It isn't being dumb, it just isn't made easy, since even the version of the encoder might add some unknown thing to the input files that isn't reported in any tool showing the parameters.  This is one reason why I think you'll need to re-encode ... so you know the exact parameters for all the videos involved.

---

### Post by Paddy Landau on 2023-02-13
Hmm, alright. Perhaps I'd better just give up trying to add spacers, because it seems like there's a lot of knowledge that I'm lacking.

Thank you for the time that you've spent trying to help!

It's been an interesting experiment, but I'm not much the wiser. I need a "Video encoding for Dummies" book, but I suspect that a dummy wouldn't be able to understand. It's a complex subject, isn't it?

---

### Post by qyot27 on 2023-02-18
I'd probably re-encode just to make sure the video is rotated correctly.  I'd be willing to bet the issue in VLC is because it may be picking up on some metadata in the segments that changes when it goes from segment into spacer, which throws everything off.  When re-encoding, the metadata would [usually] be stripped out, depending on what it is.

And if I did re-encode, it would be by using AviSynth+ to prepare the entire thing before handing it off to FFmpeg.

```
v1=FFmpegSource2("video1.mp4",atrack=-1).TurnRight()
v2=FFmpegSource2("video2.mp4",atrack=-1).TurnRight()
v3=FFmpegSource2("video3.mp4",atrack=-1).TurnRight()
# [other video files, following the same pattern]
spacer=BlankClip(v1,12)

v1 ++ spacer ++ v2 ++ spacer ++ v3 #[and so on...]
```
This would be saved as a file, e.g. test_concat.avs.  You can then give the script file to FFmpeg for encoding.

The only rub would be the need to build AviSynth+ (easy), either re-build the system FFmpeg with *--enable-avisynth* (tricky) or build a separate [and preferably static] FFmpeg to handle it (easier, but depends on how many other things you want enabled), and also build the FFMS2 source plugin (easy, if you point it at that other build of FFmpeg).  The deb-multimedia (dmo) repository is another option.

One advantage of this approach is that all filtering can be done in the script, and be changed basically on-the-fly so you don't waste time running re-encode after re-encode to get the video processing looking right.  If FFmpeg was built with *--enable-avisynth*, the corresponding FFplay binaries can play the scripts back as if they were normal video files - although the better option would be building mpv and linking against that AviSynth-aware version of FFmpeg, since mpv is actually meant as a normal media player.

---

### Post by Paddy Landau on 2023-02-19
> **qyot27 said:**
> I'd probably re-encode…
Thank you for that detailed response! Rebuilding apps is rather more than I feel capable of doing, so I shan't go down that route.

TheFu also mentioned re-encoding; I think that ffmpeg can do that anyway, can't it? That's something that I might look at when I have a some time, because I don't fully understand how to use ffmpeg (my skills level is novice).

Regarding the playback, the final product is intended to be played not only on a Linux system but also on a Windows system and an Android system, so it would have to work natively in them.

---

### Post by qyot27 on 2023-02-19
Yes, FFmpeg can do re-encodes.  The small primer there on AviSynth was mainly because that's one way you can ensure that everything looks correct before giving it to FFmpeg, because as far as FFmpeg knows, it's only getting one file, not several.

But either way, the way you would go about encoding afterward is the same, whether you use a concat list file or an AviSynth script:
```
ffmpeg -f concat -safe 0 -i video.list -vcodec libx264 -crf 18 -acodec aac -b:a 192k 'Concatenated.mp4'
```
or
```
ffmpeg -i video.avs -vcodec libx264 -crf 18 -acodec aac -b:a 192k 'Concatenated.mp4'
```

Encoding parameters get listed after the input.  *vcodec* (or *c:v*) selects the video codec (in this case, libx264, since H.264 is by far the most commonly supported video format these days), *crf* is the video quality control targeting a rough perceptual quality rather than a specific bitrate* (18 being a fairly middle of the road setting for anything ~720p or under), *acodec* (or *c:a*) selects the audio codec (aac, since that is typically what gets paired with H.264), and *b:a* sets the audio bitrate.

*if it has to be played back on dedicated hardware rather than a software player, you may need to switch to using a specific bitrate instead, but I would try with crf mode first.

---

### Post by Paddy Landau on 2023-02-19
> **qyot27 said:**
> Yes, FFmpeg can do re-encodes…
Thank you! I have made a note of all that, and I'll give it a try when I have some time.

---

