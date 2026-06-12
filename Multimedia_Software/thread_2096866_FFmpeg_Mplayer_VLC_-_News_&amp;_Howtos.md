---
title: "FFmpeg Mplayer VLC - News &amp; Howtos"
date: 2012-12-21
forum: Multimedia Software
---

### Post by Merrattic on 2012-12-21
This thread has been started to provide those in the know, and those wanting to know, a place to discuss developments, changes, tips, tricks, one liners, scripts in ffmpeg, mplayer, vlc and similar associated programs. Submissions and questions alike. If posting something different / new in this thread, on replying go advanced and edit the title accordingly, also use the tag facility to assist with searches :)

I'll kick things off with a few links:

**FFMpeg**
[http://ffmpeg.org](http://ffmpeg.org) & [http://ffmpeg.org/trac/ffmpeg/wiki](http://ffmpeg.org/trac/ffmpeg/wiki)

**Mplayer**
[http://www.mplayerhq.hu](http://www.mplayerhq.hu)

**VLC**
[http://www.videolan.org/vlc/index.html](http://www.videolan.org/vlc/index.html)

---

### Post by andrew.46 on 2012-12-21
Thanks for starting this thread Merratic! I would like to kick off with a great link:

Welcome to the FFmpeg Bug Tracker and Wiki
[https://ffmpeg.org/trac/ffmpeg/wiki](https://ffmpeg.org/trac/ffmpeg/wiki)

Some great info specific to Ubuntu and FFmpeg, some of it based on information formerly hosted on these Forums. Of great interest *currently* is the new ability of FFmpeg to burn subtitles into video streams:

How to burn subtitles into the video
[https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20burn%20subtitles%20into%20the%20video](https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20burn%20subtitles%20into%20the%20video)

I have given this filter a run and for my simple needs it works very, very well.

---

### Post by nothingspecial on 2012-12-21
This is great. Discussion of new developments is always welcome. 

If anyone asks a support question within this thread I hope they will be encouraged to start a thread of their own in which we can link back to the information in this thread or the other fantastic documentation available.

---

### Post by Merrattic on 2012-12-21
@ Andrew.46 re subtitles

How to setup the subtitle file in the first place? Is there an associated program for this? I would use this for example in screen recordings to add text to a tutorial.....

EDIT: found myself, use either **subtitleeditor** or **gaupol** both in the main repos

---

### Post by ron999 on 2012-12-21
> **Merrattic said:**
> ... one liners

OK
Here is a one-liner. :p
A way howto use neroAacEnc with FFmpeg.
  
```
ffmpeg -i "input" -c:v libx264 -crf 23 -preset medium -an output.mp4 -f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of soundtrack.aac && MP4Box output.mp4 -add soundtrack.aac
```

And the deluxe version:-

```
tempname=$(date +"%s"); \
ffmpeg -i "input" \
-c:v libx264 -crf 23 -preset medium -an output.mp4 \
-f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of $tempname.aac && \
MP4Box output.mp4 -add $tempname.aac && \
rm -f $tempname.aac
```

Also for mkv:-
     
```
tempname=$(date +"%s"); \
ffmpeg -i "input" \
-c:v libx264 -crf 23 -preset medium -an $tempname.mkv \
-f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of $tempname.aac && \
mkvmerge -o output.mkv $tempname.mkv $tempname.aac && \
rm -f $tempname.mkv $tempname.aac
```

---

### Post by nothingspecial on 2012-12-21
> **Merrattic said:**
> @ Andrew.46 re subtitles

How to setup the subtitle file in the first place? Is there an associated program for this? I would use this for example in screen recordings to add text to a tutorial.....

EDIT: found myself, use either **subtitleeditor** or **gaupol** both in the main repos

Please do not use this thread to ask specific questions.

If someone is searching the forums for an answer about subtitle files, how are they expected to find it in a thread titled "FFmpeg Mplayer VLC - News & Howtos" ?

---

### Post by nothingspecial on 2012-12-21
> **ron999 said:**
> OK
Here is a one-liner. :p
A way howto use neroAacEnc with FFmpeg.
  
```
ffmpeg -i "input" -c:v libx264 -crf 23 -preset medium -an output.mp4 -f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of soundtrack.aac && MP4Box output.mp4 -add soundtrack.aac
```

And the deluxe version:-

```
tempname=$(date +"%s"); \
ffmpeg -i "input" \
-c:v libx264 -crf 23 -preset medium -an output.mp4 \
-f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of $tempname.aac && \
MP4Box output.mp4 -add $tempname.aac && \
rm -f $tempname.aac
```

Also for mkv:-
     
```
tempname=$(date +"%s"); \
ffmpeg -i "input" \
-c:v libx264 -crf 23 -preset medium -an $tempname.mkv \
-f wav - | neroAacEnc -if - -q 0.5 -ignorelength -of $tempname.aac && \
mkvmerge -o output.mkv $tempname.mkv $tempname.aac && \
rm -f $tempname.mkv $tempname.aac
```


awesome, thanks.

---

### Post by evilsoup on 2012-12-21
HOW TO: concatenate MP4 files with h264 video & AAC audio without re-encoding.

Note that this will only work on files with the same parameters - same frame rate, etc. This should be adaptable to other MPEG files (MPEG4/divx, MPEG2, MP3 or MP2 audio), though you'd have to change the bitstream filters.

First, create some named pipes:

```
mkfifo temp1 temp2
```Then, you're going to need to transfer the videos to MPEG Transport Streams, which makes it possible to concatenate, and then do the actual concatenation using ffmpeg's concat protocol.

```

ffmpeg -i input1.mp4 -c copy -bsf h264_mp4toannexb -f mpegts -y temp1 2> /dev/null & \
ffmpeg -i input2.mp4 -c copy -bsf h264_mp4toannexb -f mpegts -y temp2 2> /dev/null & \
ffmpeg -f mpegts -i "concat:temp1|temp2" -c copy -absf aac_adtstoacs output.mp4 

```As far as I know, you can use this to concatenate an arbitrary number of MP4 files, though I've not had a reason to try it on more than three files myself. I might whip up a bash script to reduce the typing needed.

EDIT: also, it should be noted that you only need to use a transport stream because of the video. If you only have MP3 or AAC audio (even in an MP4 container) you should be able to feed them to the concat protocol as-is, withoutv  mucking around with pipes.

---

### Post by ron999 on 2012-12-22
> **evilsoup said:**
> HOW TO: concatenate MP4 files with h264 video & AAC audio without re-encoding.
Hi
For this type of file, doesn't **MP4Box** do the same thing?
```
MP4Box input1.mp4 -cat input2.mp4 -out output.mp4
```

---

### Post by evilsoup on 2012-12-22
Yes. But I've found the ffmpeg way to work on some files that MP4Box doesn't.

And besides, this is the ffmpeg, Mplayer & VLC thread :P

---

### Post by Merrattic on 2012-12-22
> **nothingspecial said:**
> Please do not use this thread to ask specific questions.

If someone is searching the forums for an answer about subtitle files, how are they expected to find it in a thread titled "FFmpeg Mplayer VLC - News & Howtos" ?

Hence why my starting post indicated that posters of new material should go advanced and then edit the title for their post.

A search (especially if you pick "Beans" instead of "Threads") will return the post. (although in this case it was beaten to the top by your post :lol:)

So please all new info posters, change the title of your post :)

---

### Post by andrew.46 on 2012-12-23
I have upgraded the version of FFmpeg used for my guide:

Howto: Build the development version of vlc under Ubuntu
[http://www.andrews-corner.org/vlc.html](http://www.andrews-corner.org/vlc.html)

and it all builds and runs well on Quantal as of:

```

andrew@corinth:~$ **[COLOR="Red"]cvlc --version | head -n 3[/COLOR]**
VLC media player 2.1.0-git Rincewind (revision 7f4f09b)
VLC version 2.1.0-git Rincewind (7f4f09b)
Compiled by andrew on corinth (Dec 21 2012 15:34:31)
Compiler: gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1)

```

Still a lot of fun building this version :)

---

### Post by Merrattic on 2012-12-23
Moving on from this thread: 

[http://ubuntuforums.org/showthread.php?t=1502537](http://ubuntuforums.org/showthread.php?t=1502537)

which is now closed, *loop_input* is now deprecated in favour of *loop 1*. So to create a film from one image file, to the length of one audio file, like the ones you see on youtube, do something like this:
```
ffmpeg -loop 1 -shortest -i input.jpg -i input.mp3 \
-acodec copy -c:v mjpeg-aspect 16:9 output.mp4
``` You may wish to play around with bitrates and scale too.

---

### Post by shantiq on 2012-12-24
not seen this thread yet so a few for your perusal


**audio bulk convert** 

keeps tags!




**flac to 320 mp3**

> for f in *flac; do ffmpeg -i "$f" -b:a 320k -c:a libmp3lame "${f%.*}.mp3"; done 


**alac to flac**

> for f in *.m4a; do ffmpeg -i "$f" "${f%.m4a}.flac"; done

**flac to alac**

> for f in *.flac; do ffmpeg -i "$f" -c:a alac "${f%.flac}.m4a"; done


use from and to any audio format simply modifying codec/bitrate/channels etc...


**ac3 to aac [with or without 5.1]** requires this [**version**]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") of ffmpeg

>  for f in *.ac3; do ffmpeg -i "$f" -c:a  libfdk_aac  -b:a 448k "${f%.*ac3}.aac"; done

---

### Post by Merrattic on 2012-12-24
I do something similar :
[B]
This one strips the audio from an mp4 video and converts to mp3:[/B]
```
#!/bin/bash

#convert mp4 to mp3

FILES="*.mp4"

for F in $FILES

do
newname=`basename "$F" .mp4`
ffmpeg -i "$F" -vn -c:a libmp3lame -ac 2 -ab 192k -ar 44100 "$newname.mp3"

done
```Again, just change the extensions/bitrates/codecs for different formats, and if doing audio to audio remove the "-vn" part.

---

### Post by FakeOutdoorsman on 2012-12-25
"ffmpeg -h" used to include all options. You can now control how much help you want to be displayed:
```
ffmpeg -h      -- print basic options
ffmpeg -h long -- print more options
ffmpeg -h full -- print all options (including all format and codec specific options, very long)
```

"man ffmpeg" has also seen some changes and has been broken up into specific sections:
```
SEE ALSO
       ffplay(1), ffprobe(1), ffserver(1), ffmpeg-utils(1),
       ffmpeg-scaler(1), ffmpeg-resampler(1), ffmpeg-codecs(1),
       ffmpeg-bitstream-filters(1), ffmpeg-formats(1), ffmpeg-devices(1),
       ffmpeg-protocols(1), ffmpeg-filters(1)
```

Also see Andrew's example at [ffmpeg new syntax](http://ubuntuforums.org/showpost.php?p=12419575&postcount=4).

---

### Post by andrew.46 on 2012-12-25
Looks good, those FFmpeg guys never stop :)

---

### Post by andrew.46 on 2013-01-03
Many questions on these Forums concerning stitching together videos, this nice script might be the answer to many posts:

[http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join,%20merge%29%20media%20files](http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join,%20merge%29%20media%20files)

Down the bottom of the page. I changed the EXTRA_OPTIONS and changed all the -vcodec -acodec stuff (although I believe it still works with git FFmpeg) and off I went. Interested to know how others find this script?

---

### Post by evilsoup on 2013-01-03
That script should work, but anyone using the repo version should change all instances of 'ffmpeg' to 'avconv' within the script, to be on the safe side.

There is a [concat filter]("http://ffmpeg.org/ffmpeg-filters.html#concat") included with recent versions of ffmpeg that should enable people to do the same without the need for an external script, but I haven't tried it out yet, so I don't know how well it works (I may play around with it some time today or tomorrow, if I do I'll post usage etc in this thread). EDIT: if someone with the repo version of avconv could post up the output of

```

avconv -filters | grep concat

```

that would tell me if the filter method is available to Ubuntu avconv users.

---

### Post by andrew.46 on 2013-01-03
I keep a relatively clean Quantal VM and it is not there :(

---

### Post by evilsoup on 2013-01-03
After a small amount of tinkering with the examples given in the (typically newbie-unfriendly :/ ) ffmpeg filter documentation, I've found that this command will concatenate two videos:

```

ffmpeg -i input1.mp4 -i input2.mp4 \
-filter_complex '[0:0] [0:1] [1:0] [1:1] concat=n=2:v=1:a=1 [v] [a]' \
-map '[v]' -map '[a]' <encoding options> output.mp4

```I'll break apart the -filter_complex section, to make it easier to follow

```

'[0:0] [0:1] [1:0] [1:1] 

```This fragment tells ffmpeg what streams to send to the concat filter; in this case, streams 0 and 1 from input 0 (ffmpeg starts counting from 0, so that's the first and second streams from the first input file, input1.mp4 in this example), and streams 0 and 1 from input 1 (input2.mp4).

```

concat=n=2:v=1:a=1 [v] [a]'

```This is the concat filter itself. n=2 is telling the filter that there are two input files; v=1 is telling it that there will be one video stream; a=1 is telling it that there will be one audio stream (I know I said that ffmpeg starts counting from 0, but apparently the writer of this filter decided to do this instead).

[v] and [a] are names for the output streams, to allow the rest of the ffmpeg line to use the output of the concat filter. I *think* they can have arbitrary names; which one is video and which one is audio is probably determined by their relative positions, but I haven't tested that out.

Note that the single quotes ' ' around the whole filter section are required.

```

-map '[v]' -map '[a]'

```This tells ffmpeg to use the results of the concat filter rather than the streams directly from the input files. 

Note that filters are incompatible with stream copying; you can't use -c copy with this method. I also think that it can't handle soft subtitles, though I haven't tested that: there's no hint about it in the documentation, but ffmpeg documentation is often incomplete or obfuscated, so that's not a sure sign either way.

This can concatenate files encoded in different formats (I've tested with a h264/aac MP4 and a vpx/vorbis WEBM, worked perfectly), though they need to be the same video frame size and audio sample rate and etc. So the concat filter can be used instead of that script. Here are some examples that should come in useful.

To concatenate two files into a decent-quality h264 video/AAC audio MP4:

```

ffmpeg -i input1.mp4 -i input2.webm \
-filter_complex '[0:0] [0:1] [1:0] [1:1] concat=n=2:v=1:a=1 [v] [a]' \
-map '[v]' -map '[a]' -c:v libx264 -crf 25 -preset veryfast -c:a libfdk_aac -vbr 3 output.mp4

```Three files, same output settings:

```

ffmpeg -i input1.mp4 -i input2.webm -i input3.ogg \
-filter_complex '[0:0] [0:1] [1:0] [1:1] [2:0] [2:1] concat=n=3:v=1:a=1 [v] [a]' \
-map '[v]' -map '[a]' -c:v libx264 -crf 25 -preset veryfast -c:a libfdk_aac -vbr 3 output.mp4

```Three files, but with two audio streams (e.g. different languages) rather than one:

```

ffmpeg -i input1.mp4 -i input2.webm -i input3.ogg \
-filter_complex '[0:0] [0:1] [0:2] [1:0] [1:1] [1:2] [2:0] [2:1] [2:2] concat=n=3:v=1:a=2 [v] [a1] [a2]' \
-map '[v]' -map '[a1]' -map '[a2]' -c:v libx264 -crf 25 -preset veryfast -c:a libfdk_aac -vbr 3 output.mp4

```THE FOLLOWING IS UNTESTED, AND I'M 90% SURE IT WON'T WORK, but if anyone wants to test it out, feel free - if it is possible, this should concatenate a subtitle stream as well:

```

ffmpeg -i input1.mp4 -i input2.mp4 \
-filter_complex '[0:0] [0:1] [0:2] [1:0] [1:1] [1:2] concat=n=2:v=1:a=1:s=1 [v] [a] [s]' \
-map '[v]' -map '[a]' -map '[s]' -c:v libx264 -crf 25 -preset veryfast -c:a libfdk_aac -vbr 3 -c:s *** output.mp4

```

---

### Post by evilsoup on 2013-01-03
> **andrew.46 said:**
> I keep a relatively clean Quantal VM and it is not there :(

Well, that's annoying. One more reason for people to upgrade to ffmpeg, I suppose.

Would it be possible for you to do the same thing with the ffmpeg from Jon Severinsson's PPA?

---

### Post by evilsoup on 2013-01-03
To recursively convert files (so do every *flac in a directory, and in directory within that directory), you can use find. This will convert all FLACs to MP3 with a quality setting of 2 (indiscernible from CD quality for most people):

```

find . -type f -name *.flac -exec bash -c 'ffmpeg -i "$0" -c:a libmp3lame -q:a 2 "${0/%flac/mp3}"' {} \;

```

---

### Post by Merrattic on 2013-01-05
Nice work on the concat stuff **evilsoup** - without you explaining it all I'd have given up after the first line of explanation in the examples ;)

---

### Post by FakeOutdoorsman on 2013-01-05
> **evilsoup said:**
> Would it be possible for you to do the same thing with the ffmpeg from Jon Severinsson's PPA?

The concat filter is also not available in ffmpeg from Jon Severinsson's PPA.

---

### Post by evilsoup on 2013-01-05
What about the subtitles filter?

---

### Post by FakeOutdoorsman on 2013-01-06
No, unfortunately. It's too new for the current PPA build and I don't know if it has been backported to any releases. See the [filter list]("http://ubuntuforums.org/showpost.php?p=12414705&postcount=6") for the PPA ffmpeg for more info.

---

### Post by evilsoup on 2013-01-09
Note: these filters may or may not be available in the repo or Jon-Severinsson version, I'm not sure how new they are.

You can **speed up video** with the setpts video filter:

```

ffmpeg -i input.mkv -an -filter:v 'setpts=0.5*PTS' [output options] output.mkv

```Generally, use it like this: 'setpts=*x**PTS', where *x* is 1/the speed you want. So if you want to double the speed, then 1/2 gets you 'setpts=0.5*PTS'; if you want to halve the speed, then 1/0.5 gets you 'setpts=2*PTS'.

You can **speed up audio** with the atempo audio filter:

```

ffmpeg -i input.mkv -vn -filter:a 'atempo=2.0' [output options] output.mkv

```The value here works in the exact opposite way to the setpts example; if you want to double the speed, put in 2.0, and if you want to halve it use 0.5. This filter is limited to the range 0.5-2.0; if you need to work outside that range, you have to chain multiple atempo filters together. To quadruple the speed of some audio:

```

ffmpeg -i input.mkv -vn -filter:a 'atempo=2.0,atempo=2.0' [output options] output.mkv

```Note that this can be tricky: the two atempo filters effectively multiply their values, rather than adding them together. Some arithmatic would be needed.

You can **combine these two** filters together in a complex filtergraph. To double the speed of both video and audio at the same time:

```

ffmpeg -i input.mkv -filter_complex '[0:v]setpts=0.5*PTS[v];[0:a]atempo=2.0[a]' \
-map '[v]' -map '[a]' [output options] output.mkv

```If you have two audio streams, and you want to speed up both of them, you can use:

```

ffmpeg -i input.mkv \
-filter_complex '[0:v]setpts=0.5*PTS[v];[0:a:0]atempo=2.0[a0];[0:a:1]atempo=2.0[a1]' \
-map '[v]' -map '[a0]' -map '[a1]' [output options] output.mkv

```I've also put this information (well, the atempo stuff; the setpts stuff was there already) up on the [ffmpeg community wiki]("http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20speed%20up%20/%20slow%20down%20a%20video")

---

### Post by FakeOutdoorsman on 2013-01-11
x264 minimum Yasm version now appears to be 1.2.0 as of the latest push. I updated [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) to include Yasm compilation since repository versions are old.

---

### Post by evilsoup on 2013-01-15
If you have a decrypted ISO of a DVD movie, you can use ffmpeg's [concat protocol]("https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20concatenate%20%28join%2C%20merge%29%20media%20files#protocol") (the demuxer will also work, but I've found the protocol to be more reliable for these things).

```

sudo mkdir /media/fakedvd
sudo mount -o loop movie.iso /media/fakedvd
cd /media/fakedvd
ffmpeg -i "concat:VTS_02_1.VOB|VTS_02_2.VOB|VTS_02_3.VOB|VTS_02_4.VOB|VTS_02_5.VOB" \
-c:a copy -c:v libx264 -crf:v 22 -preset:v veryfast ~/Videos/output.mp4

```Normally, the VTS_xx_n.VOB with the most entries is the main feature of the DVD (the rest are [anti-piracy warnings]("http://www.youtube.com/watch?v=ALZZx1xmAzg"), trailers, deleted scenes, etc). VTS_xx_0.VOB is normally the DVD menu, so you can ignore it.

Obviously, the above method involves creating a huge intermediate ISO file. FFmpeg has no way of reading encrypted DVDs. Fortunately, there's another command-line program that can use the libdvdcss stuff, *and* avoid having to use ffmpeg's concat protocol: vobcopy.

```

vobcopy -l -o - | ffmpeg -i - -c:a copy -c:v libx264 -crf:v 22 -preset:v veryfast output.mp4

```Vobcopy should automatically detect where your DVD is mounted, and it can normally detect which VOB files to use automatically. The `-l` option tells vobcopy to output a single, large file (normally it outputs to 2GB files, to be safe on older systems that don't support large files); `-o -` tells vobcopy to output to STDOUT, which this command pipes into ffmpeg. For more information on vobcopy, look at its man page.

---

### Post by SeijiSensei on 2013-01-15
I recently came across this [informative summary]("http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html") of the libav/ffmpeg divorce.  For those of you who, like me, wondered why you get the "deprecated" message whenever you run the version of ffmpeg in the repos, it provides some helpful insights.

---

### Post by FakeOutdoorsman on 2013-01-15
The choice to use the phrase "THIS PROGRAM IS DEPRECATED" was a very poor one resulting from a combination of politics and lack of understanding of the users point-of-view by the Ubuntu developers and maintainers (this was an Ubuntu addition, not upstream). That being said, the previous message was even worse...

I provided a patch to use a more descriptive phrase but it was not accepted.

---

### Post by mc4man on 2013-01-15
While the current 'message' is Ubuntu created it was done in such a manner to placate Reinhard Tartler from Debian who is the maintainer for Ubuntu/Debian
(another reason why the bug title/descrip was changed.

Anyway in 13.04 libav-tools has removed 'ffmpeg' from the install though they still keep & re-direct ffplay, ffsever & ffprobe

(generally libav seems behind the curve on some decoders, see they just added wmal to 'plain9' & maybe opus, not that it will do users of apps depending on libav* shared libs much good in Ubuntu atm.

Also this nonsense sometimes leads to breaks in some app's support, currently audacious in 13.04 is again [without ffaudio plugin]("https://bugs.launchpad.net/ubuntu/+source/audacious-plugins/+bug/1080059"), the Debian maintainer doesn't seem to care much..

---

### Post by FakeOutdoorsman on 2013-01-15
> **mc4man said:**
> Anyway in 13.04 libav-tools has removed 'ffmpeg' from the install though they still keep & re-direct ffplay, ffsever & ffprobe

Also see [Merge branch 'experimental' into ubuntu](http://anonscm.debian.org/gitweb/?p=pkg-multimedia/libav.git;a=blobdiff;f=debian/control;h=ba2760abac7efa6e4e8d3d4619a07e01b0bd10c3;hp=3ab1b81d2ebce43cb520300a3029de185b8f137d;hb=a7398cdc19fb2ea2a7716fb15b4b02f9ecf7c3ce;hpb=8cf50e974ef00b5cd050b139c7d9c00c09130f1e).

Reinhard is hopeful that ffmpeg will be removed for Raring. He says:
> I don't have the time to fix all packages in the archive, which needs to be done by feature freeze for that. my hope is that other packagers can jump in

Assuming this does occur it probably makes it more likely that a ffmpeg from FFmpeg package could be a possibility in 13.10 perhaps...I'm just guessing here. A static ffmpeg binary might be a good and simple-ish start.

---

### Post by mc4man on 2013-01-18
> **FakeOutdoorsman said:**
> 
Reinhard is hopeful that ffmpeg will be removed for Raring. He says:
Assuming this does occur it probably makes it more likely that a ffmpeg from FFmpeg package could be a possibility in 13.10 perhaps...I'm just guessing here. A static ffmpeg binary might be a good and simple-ish start.

Not sure whether that would be allowed (static FFmpeg
Certainly is possible, went ahead & made a static ffmpeg .deb with no issue (screens
To save some time took a ffmpeg-1.0 debian-multimedia source, removed alot (the ./configure is extensive, could of removed some more), & built up 
Used current shared libs in 13.04 for dep's, installing to /usr

What did come up conflicting libav-tools other than the 3 remaining bin files (symlinks), was that libav uses many if not all the same doc & man names. To bad they don't use their own.. 
(doc's & man's could be installed elsewhere but not sure whether that would matter.

edit: on the other hand it could all be installed to /opt with no issues with libav-tools, I've several install there now, shared & static

---

### Post by FakeOutdoorsman on 2013-01-18
I guess we could always try and submit something and see what they say (or don't say). Debian package management isn't something I'm very familiar with... [DebianMultimedia](http://wiki.debian.org/DebianMultimedia) and the related [FAQ](http://wiki.debian.org/DebianMultimedia/FAQ) and [packaging](http://wiki.debian.org/DebianMultimedia/DevelopPackaging) are worth a look.

I should ask him about the symlinked bin files ffplay, ffserver, and ffprobe.
**Update:** I don't see any symlinks in the [libav-tools](http://packages.debian.org/experimental/amd64/libav-tools/filelist) package in Debian experimental.

Do you know what DMO means (7:1.1-dmo3)? I never figured that out.

---

### Post by mc4man on 2013-01-18
> **FakeOutdoorsman said:**
> 

I should ask him about the symlinked bin files ffplay, ffserver, and ffprobe.

Do you know what DMO means (7:1.1-dmo3)? I never figured that out.
dmo = deb-multimedia.org 
as in I think Not [DFSG free]("http://www.debian.org/social_contract")

---

### Post by andrew.46 on 2013-01-23
Those who follow the svn version of MPlayer will now have the ability to play [evrc files]("http://en.wikipedia.org/wiki/Evrc"). A sample here:

```

wget http://samples.mplayerhq.hu/A-codecs/suite/EVRC/02_Lord_Of_The_Flies_evrc.qcp

```

Playback as follows:

```

andrew@skamandros~$ mplayer 02_Lord_Of_The_Flies_evrc.qcp 
MPlayer SVN-r35839-4.7.2 (C) 2000-2013 MPlayer Team

Playing 02_Lord_Of_The_Flies_evrc.qcp.
libavformat version 54.61.104 (internal)
libavformat file format detected.
[qcp @ 0xef0300]max_analyze_duration 5000000 reached at 5000000 microseconds
[qcp @ 0xef0300]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (evrc), -aid 0
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.90.100 (internal)
AUDIO: 8000 Hz, 1 ch, floatle, 4.8 kbit/1.88% (ratio: 600->32000)
Selected audio codec: [ffevrc] afm: ffmpeg (FFmpeg EVRC decoder)
==========================================================================
AO: [oss] 8000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 296.7 (04:56.7) of 250.3 (04:10.2)  0.2% 


Exiting... (End of file)

```

Playback a little patchy on this sample btw. More of a curiosity for me rather than a positive 'need-to-have' but good to see MPlayer/[libavcodec]("http://git.videolan.org/?p=ffmpeg.git;a=commit;h=098d3891be08ca119e20ad7989668ddef83b31ea") catering for all needs :).

---

### Post by FakeOutdoorsman on 2013-02-09
A [tee psuedo-muxer](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=f43d09cd60a17a139b3aeb94434dbbbac1a28dab) has been added to ffmpeg by Nicolas George:

> The tee muxer can be used to write the same data to several files or any other kind of muxer. It can be used, for example, to both stream a video to the network and save it to disk at the same time.

I haven't been able to try it yet, but it looks interesting.

---

### Post by evilsoup on 2013-02-09
That looks pretty snappy, I'll have to re-compile soon to get that. And you posted that 40 minutes after the commit, that's crazy quick :P

An example of its usage, from [here](http://git.videolan.org/?p=ffmpeg.git;a=commitdiff;h=f43d09cd60a17a139b3aeb94434dbbbac1a28dab):

```

ffmpeg -i input.file -c:v libx264 -c:a mp2 \
-f tee "archive-20121107.mkv|[f=mpegts]udp://10.0.1.255:1234/"

```

...this will create both an MKV and an MPEG Transport Stream.

---

### Post by andrew.46 on 2013-02-12
Is everybody keeping up with SMPlayer releases? 0.8.3 came out at the end of 2012 and with UMPlayer fading out SMPlayer is still the best choice for an MPlayer gui...

---

### Post by FakeOutdoorsman on 2013-02-12
> **andrew.46 said:**
> ...with UMPlayer fading out...

What's the story behind that? (I've never actually used UMPlayer).

---

### Post by andrew.46 on 2013-02-12
> **FakeOutdoorsman said:**
> What's the story behind that? (I've never actually used UMPlayer).

UMPlayer was a nice fork of SMPlayer that appeared when SMPlayer development was quiescent. It added a nice feature of a youtube browser and a few other improvements. When SMPlayer roared back to life rvm imcoporated and improved some of the UMPlayer changes and it looks like UMPlayer is now sleeping. Details here:

[http://smplayer.sourceforge.net/blog/umplayer-is-a-smplayer-fork/](http://smplayer.sourceforge.net/blog/umplayer-is-a-smplayer-fork/)

A much more civilised fork than others that have occurred recently :).

---

### Post by andrew.46 on 2013-03-02
Not such recent news perhaps but there has been substantial work done on the native MPlayer gui known as GMPlayer in recent times. I have started building it again, just need to find the best possible skin, the default skin is a little old looking :). My screenshot shows GMPlyer with 'Blue', and yes that is the Bee Gees with 'Stayin' Alive', the song at the centre of several Basic Life Support advertisements recently!!!

Edit: Added 'Clearlooks' with Bruce Lee sizzling across the screen!! Clearlooks was created by the man doing all of the gui work on MPlayer.

---

### Post by Merrattic on 2013-03-02
I am strictly cli, config file and scripts with mplayer, just a window and keyboard commands for me. Never got on with any of the mplayer guis. Starting playing with cvlc as well, but might need to remap keyboard commands, small and fading brain can't cope with two sets of kbd shortcuts :)

---

### Post by Merrattic on 2013-03-10
Just spotted a new commit: afade, which allows for fading in and out of audio (to go along with fade for video)

Seems this works at the beginning and the end of a video clip, but can be more tricky to implement in the middle of a clip? Not had a chance to recompile to try it out yet.

syntax:

[http://ffmpeg.org/ffmpeg-filters.html#afade](http://ffmpeg.org/ffmpeg-filters.html#afade)

---

### Post by mc4man on 2013-03-17
Really minor little 'info' deal I find handy
While one can open the individual man pages in a terminal, ect. I always found that to be a hassle
Unity has a help lens with a man page scope, makes it easy to open & search any man

Also there are bookmark, find, & print options, screen shows some

---

### Post by andrew.46 on 2013-03-27
To put my money where my mouth is I have written up the installation of skins with GMPlayer:

[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

The 'Noskin' skin is an interesting move :). Anybody have some favourite skins that I should add in there?

---

### Post by FakeOutdoorsman on 2013-03-27
Newish filter: [curves](http://ffmpeg.org/ffmpeg-filters.html#curves). Presets have been added a few days ago.
```
ffplay input.mkv -vf curves=preset=color_negative
ffmpeg -i input.mkv -vf curves=preset=strong_contrast output.mkv
```

Also, if you're a student you should consider participating in [Google Summer of Code](https://developers.google.com/open-source/soc/) with FFmpeg. You can get paid for coding and get to interact with an open-source project. See [FFmpeg Summer of Code 2013](http://wiki.multimedia.cx/index.php?title=FFmpeg_Summer_of_Code_2013) for more info.

---

### Post by FakeOutdoorsman on 2013-04-05
FFmpeg documentation update: now you can use "man ffmpeg-all" and get a very long, monolithic output as an alternative to the separated-by-component style such as "man ffmpeg-filters".

---

### Post by FakeOutdoorsman on 2013-04-05
Some other ways of getting info and help:

List any AVOptions ("private" encoder options) and supported stuff for an encoder:
```
$ ffmpeg -h encoder=aac
Encoder aac [AAC (Advanced Audio Coding)]:
    Supported sample rates: 96000 88200 64000 48000 44100 32000 24000 22050 16000 12000 11025 8000 7350
    Supported sample formats: fltp
AAC encoder AVOptions:
  -stereo_mode       <int>        E...A. Stereo coding method (from -1 to 1)
     auto                         E...A. Selected by the Encoder
     ms_off                       E...A. Disable Mid/Side coding
     ms_force                     E...A. Force Mid/Side for the whole frame if possible
  -aac_coder         <int>        E...A.  (from 0 to 3)
```

List any AVOptions and supported stuff for a decoder:
```
$ ffmpeg -h decoder=vorbis
Decoder vorbis [Vorbis]:
    Supported sample formats: fltp
    Supported channel layouts: mono stereo 3.0 quad 5.0 5.1 6.1 7.1
```

List AVOptions for a filter:
```
$ ffmpeg -h filter=curves
Filter curves
  Adjust components curves.
curves AVOptions:
  red               <string>     ..FV.. set red points coordinates
  r                 <string>     ..FV.. set red points coordinates
  green             <string>     ..FV.. set green points coordinates
  g                 <string>     ..FV.. set green points coordinates
  blue              <string>     ..FV.. set blue points coordinates
  b                 <string>     ..FV.. set blue points coordinates
  preset            <int>        ..FV.. select a color curves preset (from 0 to 10)
     color_negative               ..FV..
     cross_process                ..FV..
     darker                       ..FV..
     increase_contrast              ..FV..
     lighter                      ..FV..
     linear_contrast              ..FV..
     medium_contrast              ..FV..
     negative                     ..FV..
     strong_contrast              ..FV..
     vintage                      ..FV..
```

---

### Post by andrew.46 on 2013-04-07
I have only just realised that changes and tips for the commandline ripper audio cd abcde could really fit into this thread as a *'similar program'* to the great media player and converters previously mentioned. I am fortunate enough to be one of the newest abcde developers and I would dearly love involvement by the knowledgeable people in this thread and on these Forums to make abcde a better application. Plenty of issues to have a look at here if bug squashing is your strength:

[http://code.google.com/p/abcde/issues/list](http://code.google.com/p/abcde/issues/list)

and I will be more than happy to facilitate any suggested corrections and enhancements to the abcde code, always with correct attribution of work to the appropriate person. Have a look here for recent development:

[http://code.google.com/p/abcde/source/list](http://code.google.com/p/abcde/source/list)

Encoding with NeroAacEnc and opusenc a couple of really great recent additions to abcde!!
[B]
Edit:[/B] I forget my own patch which upgraded the Musepack requirement from SV7 to SV8 :)

---

### Post by FakeOutdoorsman on 2013-04-08
> **FakeOutdoorsman said:**
> Also, if you're a student you should consider participating in [Google Summer of Code](https://developers.google.com/open-source/soc/) with FFmpeg. You can get paid for coding and get to interact with an open-source project. See [FFmpeg Summer of Code 2013](http://wiki.multimedia.cx/index.php?title=FFmpeg_Summer_of_Code_2013) for more info.

Unfortunately FFmpeg was again not accepted for GSoC.

---

### Post by shantiq on 2013-04-09
If you have a 24-bit flac and you want to retain the 24-bit there is a way [converting it to wv]   about 390k here



KEEP 24-BIT   [flac to lossy]


```
ffmpeg -i file.flac -acodec pcm_s24le -ar 48000 file.wav \
&& wavpack -b4x file.wav  && rm file.wav

```

---

### Post by evilsoup on 2013-04-09
What does the wavpack line do?

---

### Post by shantiq on 2013-04-09
hi esoup    it turns the wav into a 390k lossy wavpack or thereabouts retaining the 24-bit  [b2 instead of b4 about 260k]

---

### Post by evilsoup on 2013-04-10
Ah, OK.

---

### Post by telperion on 2013-04-12
FFmpeg: DRC (Dynamic Range Compression) audio with Sox

```
ffmpeg -i 'FILE_INPUT.mkv' -vn -f sox - | sox -t sox - -c 2 -b 16 -t wav - compand 0.0,1 6:-70,-43,-20 -5 -90 0.1 | ffmpeg -y -i - -c:a libfaac -b:a 112k -f mp4 out.m4a
```

the file out.m4a can be muxed with mkvmerge gui (or other).


Or auto muxing the drc audio in new mkv

```
ffmpeg -i originalvideo.mkv -vn -f sox - | sox -t sox - -c 2 -b 16 -t wav - compand 0.0,1 6:-70,-43,-20 -5 -90 0.1 | ffmpeg -y -i originalvideo.mkv -i - -map 0:0 -map 1:0 -f matroska -c:v copy -c:a libfaac -b:a 112k out_drc.mkv
```

or auto muxing the drc audio as second audio in new mkv:

```
ffmpeg -i originalvideo.mp4 -vn -f sox - | sox -t sox - -c 2 -b 16 -t wav - compand 0.0,1 6:-70,-43,-20 -5 -90 0.1 | ffmpeg -y -i originalvideo.mp4 -i - -map 0:0 -map 0:1 -map 1:0 -f matroska -c:v copy -c:a:0 copy -c:a:1 libfaac -b:a:1 112k -metadata:s:1 language=eng -metadata:s:2 language=eng_drc out_2audio_drc.mkv
```

Some compand preset [here]("http://forum.doom9.org/showthread.php?t=165807")

ffmpeg 1.2
sox 14.4.1

---

### Post by monkeybrain2012 on 2013-04-13
Hi,

I am wondering if there is any good instruction to compile mplayer with VAAPI support? There is a ppa but apparently it doesn't get updated [https://launchpad.net/~sander-vangrieken/+archive/vaapi](https://launchpad.net/~sander-vangrieken/+archive/vaapi)

Thanks.

---

### Post by andrew.46 on 2013-04-13
None that I am aware of I'm afraid :(

---

### Post by monkeybrain2012 on 2013-04-14
> **andrew.46 said:**
> None that I am aware of I'm afraid :(

Ok, I guess I will have to ask the guy who created the ppa. :)

---

### Post by monkeybrain2012 on 2013-04-14
Hi, I have compiled ffmpeg from source using FakeOutdoorsman's excellent tutorial. Now how I do I make the packaging system (apt-get) to use it instead of the system version? What I mean is that suppose I install vlc from apt-get it will want to install libavcodec or something as dependencies, but instead of installing redundant versions of these dependencies is there a way (sumlink?) to make the system know to use the libraries from the compiled version of ffmpeg instead ( I don't want to have to compile every application that may depend on some parts of ffmpeg)

---

### Post by andrew.46 on 2013-04-14
> **monkeybrain2012 said:**
> Ok, I guess I will have to ask the guy who created the ppa. :)

There has been talk for some time about incorporating the mplayer-vaapi code into the mainstream MPlayer code but I have heard nothing concrete for quite some time :(.

---

### Post by mc4man on 2013-04-14
> **monkeybrain2012 said:**
> Hi, I have compiled ffmpeg from source using FakeOutdoorsman's excellent tutorial. Now how I do I make the packaging system (apt-get) to use it instead of the system version? What I mean is that suppose I install vlc from apt-get it will want to install libavcodec or something as dependencies, but instead of installing redundant versions of these dependencies is there a way (sumlink?) to make the system know to use the libraries from the compiled version of ffmpeg instead ( I don't want to have to compile every application that may depend on some parts of ffmpeg)

Well if you followed the guide exactly then you built a static ffmpeg so no shared libraries & that's that.

If you built ffmpeg as shared then after an ldconfig apps would use those or some of those shared libs for better, worse, or no difference. Personally can't see the point of doing that. 
The repo packages were built off of libav, not much to be gained by having those apps use ffmpeg shared libs. Plus at times the major versions of those libs are different, libav is always behind ffmpeg so the apps won't use anyway (if vlc is expecting a .53 & you've built a .54, ect.

Far better to rebuild some sources using the static ffmpeg build or in some cases a shared ffmpeg build (out of path is better for shared

(- as far as package deps ect., last I checked checkinstall is limited to 2 "provides" so again you wouldn't be able to replace in cases where a app deps on more than 1 ffmpeg/libav libs

---

### Post by monkeybrain2012 on 2013-04-14
> **mc4man said:**
> Well if you followed the guide exactly then you built a static ffmpeg so no shared libraries & that's that.

If you built ffmpeg as shared then after an ldconfig apps would use those or some of those shared libs for better, worse, or no difference. Personally can't see the point of doing that. 
The repo packages were built off of libav, not much to be gained by having those apps use ffmpeg shared libs. Plus at times the major versions of those libs are different, libav is always behind ffmpeg so the apps won't use anyway (if vlc is expecting a .53 & you've built a .54, ect.

Far better to rebuild some sources using the static ffmpeg build or in some cases a shared ffmpeg build (out of path is better for shared

(- as far as package deps ect., last I checked checkinstall is limited to 2 "provides" so again you wouldn't be able to replace in cases where a app deps on more than 1 ffmpeg/libav libs

Hi, I actually did build ffmpeg with shared enabled. There may not be much to gain in Ubuntu, but I actually was doing this in Debian Sid. In Sid I for some reasons couldn't install the libav -extras files (from debian multimedia) without removing almost all my multimedia apps but I couldn't do some conversions with the repo version of ffmpeg (self build works fine). I know this is not really a debian forum but I figure my question is generic enough that the answer should work in Debian as well,.

---

### Post by mc4man on 2013-04-14
> **monkeybrain2012 said:**
> Hi, I actually did build ffmpeg with shared enabled. There may not be much to gain in Ubuntu, but I actually was doing this in Debian Sid. In Sid I for some reasons couldn't install the libav -extras files (from debian multimedia) without removing almost all my multimedia apps but I couldn't do some conversions with the repo version of ffmpeg(self build works fine). I know this is not really a debian forum but I figure my question is generic enough that the answer should work in Debian as well,.
Well not using Debian can only take a quick look. It appears debian-multimedia (sid) uses FFmpeg as a source, (a relatively outdated version) & doesn't provide extra packages.
Sources that build off of D-M's ffmpeg & available from D-M like vlc could be removed if you install the extra packages from Debian sid that are based on libav.
Anyway, if you were using the ffmpeg binary for your 'conversions' then there is no need to build as shared. 

Otherwise, in regards to your generic question, 
Your self built ffmpeg using checkinstall isn't going to satisfy the install deps of already built packages.
You can either take the ffmpeg source, add a debian folder, adjust as needed & package build or in the past i've used equivs to produce dummy dep packages. ( in this case the former is likely less trouble.

Again I wouldn't bother, I'd leave the provided packages as is & create your own as needed.
For Ex. I've a current ffmpeg-static in /usr/local for use of the binary(s) & an FFmpeg release source as shared in /opt for use with sources that can benefit from like audacious (also built to /opt

---

### Post by monkeybrain2012 on 2013-04-17
Hi, Mc4man,

You are probably right that it can be problematic to do this in SID as there seems to be some really crazy packaging going on like removing libavcodec or libvpx would remove Gnome along with a bunch of other things. I am not sure how that can be.

---

### Post by evilsoup on 2013-04-17
Unless you need fdk_aac (which can't be distributed with the ffmpeg binary for licensing reasons), I'd say just grab a static build from the [ffmpeg download page](https://ffmpeg.org/download.html) and add it into your $PATH, and use the libraries from the repos.

---

### Post by andrew.46 on 2013-04-19
Latest update for abcde fixes support for newer versions of eyeD3:

[http://code.google.com/p/abcde/source/detail?r=379](http://code.google.com/p/abcde/source/detail?r=379)

Could perhaps do with some cleverness to cover older versions of eyeD3, looks like the eyeD3 developer drew a line in the sand with the latest changes from 0.7.0 onwards:

[http://eyed3.nicfit.net/changelog.html](http://eyed3.nicfit.net/changelog.html)

---

### Post by andrew.46 on 2013-04-22
A new cd ripper is about to be commited to abcde:

[http://code.google.com/p/abcde/issues/detail?id=92](http://code.google.com/p/abcde/issues/detail?id=92)

The patch at the bottom is working well on my system, I would be interested to hear how others go...

---

### Post by monkeybrain2012 on 2013-04-27
Hi,

I am trying to compile ffmpeg as a shared library in raring (--enable-shared), it seems to compile ok, but when I type ffmpeg in the terminal I get 
```

ffmpeg: symbol lookup error: /usr/local/lib/libavcodec.so.55: undefined symbol: vpx_codec_vp9_dx_algo
```


I had the same problem in Precise as well. Please advise.

Thanks.

---

### Post by evilsoup on 2013-04-27
You'd probably be better off starting your own thread for that.

Did you follow a guide for compiling?

---

### Post by monkeybrain2012 on 2013-04-27
I did follow the guide, with the exception that I compiled it as a shared library because I want to use it for compiling other things, I don't want to have multiple static libraries of the same software lying around.

---

### Post by andrew.46 on 2013-04-27
An interesting development for x264 users:

OpenCL lookahead
[http://git.videolan.org/?p=x264.git;a=commit;h=3a5f6c0aeacfcb21e7853ab4879f23ec8ae5e042](http://git.videolan.org/?p=x264.git;a=commit;h=3a5f6c0aeacfcb21e7853ab4879f23ec8ae5e042)

I have to admit that I cannot get this working onmy system despite having the appropriate headers in place :(.

---

### Post by monkeybrain2012 on 2013-04-29
I managed to compile ffmpeg as a shared library and it works but only with libvpx disabled. Instead of compiling from git I just grab a tarball of ffmeg-1.2, but since I got the same error in both cases I think disabling libvpx would work for the git version too.


```
$ ffmpeg -version
ffmpeg version 1.2
built on Apr 29 2013 16:09:13 with gcc 4.7 (Ubuntu/Linaro 4.7.3-1ubuntu1)
configuration: --enable-shared --enable-ffplay --enable-libopus --enable-libpulse --disable-libvpx --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
libavutil      52. 18.100 / 52. 18.100
libavcodec     54. 92.100 / 54. 92.100
libavformat    54. 63.104 / 54. 63.104
libavdevice    54.  3.103 / 54.  3.103
libavfilter     3. 42.103 /  3. 42.103
libswscale      2.  2.100 /  2.  1.  0
libswresample   0. 17.102 /  0. 17.102
libpostproc    52.  2.100 / 52.  0.  0
```

---

### Post by evilsoup on 2013-04-30
Please [file a bug report](http://ffmpeg.org/bugreports.html) about that.

---

### Post by mc4man on 2013-04-30
> **monkeybrain2012 said:**
> I managed to compile ffmpeg as a shared library and it works but only with libvpx disabled. Instead of compiling from git I just grab a tarball of ffmeg-1.2, but since I got the same error in both cases I think disabling libvpx would work for the git version too.


It *could* be informative to know - 
Are you on 32 or 64 bit?
Did you use a static libvpx build (the guide does) or a shared libvpx build or the 13.04 libvpx1 & libvpx-dev?

Slightly off topic - 
While possibly a moot point to you I'm wondering if you realize that when building a source against a static FFmpeg that after the build you can remove that static FFmpeg build if no further use (referencing your comment about having multiple static FFmpeg builds lying around

---

### Post by monkeybrain2012 on 2013-04-30
Hi,

It is 32 bit and I build libvpx as a shared library. Seems that I can't remove libvpx1 without removing a lot of other stuffs.

---

### Post by mc4man on 2013-04-30
> **monkeybrain2012 said:**
> Hi,

It is 32 bit and I build libvpx as a shared library. Seems that I can't remove libvpx1 without removing a lot of other stuffs.
When I get home tonight will give that a try, let you know if seeing same issue 
(just to note - may not be too much difference between git vpx & the one available in raring

---

### Post by telperion on 2013-05-02
> **andrew.46 said:**
> An interesting development for x264 users:

OpenCL lookahead
[http://git.videolan.org/?p=x264.git;a=commit;h=3a5f6c0aeacfcb21e7853ab4879f23ec8ae5e042](http://git.videolan.org/?p=x264.git;a=commit;h=3a5f6c0aeacfcb21e7853ab4879f23ec8ae5e042)

I have to admit that I cannot get this working onmy system despite having the appropriate headers in place :(.


build last git for a test, 
patch for building x264 with opencl on linux

```
--- a/configure   2013-04-29 21:29:38.000000000 +0200
+++ b/configure      2013-05-02 16:11:24.000000000 +0200
@@ -1115,8 +1115,8 @@
     # OpenCL support is only well tested on Windows/MinGW.  If you
     # wish to try it on an unsupported platform, swap the lines
     # below.  If OpenCL breaks, you get to keep both halves
-    #opencl="yes"
-    opencl="no"
+    opencl="yes"
+    #opencl="no"
 fi
 if [ "$opencl" = "yes" ]; then
     log_check "looking for perl"
@@ -1125,7 +1125,7 @@
         echo 'OpenCL support requires perl to compile.'
         echo 'use --disable-opencl to compile without OpenCL.'
         exit 1
-    elif [[ $cross_prefix != ""  &&  $host_os == mingw* ]] ; then
+    elif [[ $host_os != mingw* ]] ; then
         if cc_check "CL/cl.h" "-lOpenCL"; then
             echo 'HAVE_OPENCL=yes' >> config.mak
             echo 'OPENCL_LIB=OpenCL' >> config.mak
```

test with opencl

```
mc@debian64:~/develop-deb/x264_10/opencl$ ./x264 --threads 0 --opencl  --bitrate 800 --preset faster --tune film -o video.mkv test.mkv 
lavf [info]: 720x404p 0:1 @ 24000/1001 fps (vfr)
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.1 Cache64
x264 [info]: OpenCL acceleration enabled with NVIDIA Corporation GeForce GT 440 
x264 [info]: profile High, level 3.0
x264 [info]: frame I:181   Avg QP:16.60  size: 23111                           
x264 [info]: frame P:3454  Avg QP:20.32  size:  6237
x264 [info]: frame B:4999  Avg QP:21.46  size:  1901
x264 [info]: consecutive B-frames: 11.7% 29.1% 12.4% 46.7%
x264 [info]: mb I  I16..4: 22.3% 42.6% 35.1%
x264 [info]: mb P  I16..4: 11.4% 17.3%  2.8%  P16..4: 32.8% 12.4%  4.5%  0.0%  0.0%    skip:18.8%
x264 [info]: mb B  I16..4:  1.3%  1.5%  0.2%  B16..8: 34.8%  5.9%  0.4%  direct:12.0%  skip:44.0%  L0:42.8% L1:48.8% BI: 8.4%
x264 [info]: final ratefactor: 20.01
x264 [info]: 8x8 transform intra:52.9% inter:48.2%
x264 [info]: coded y,uvDC,uvAC intra: 49.1% 65.0% 17.6% inter: 11.0% 24.5% 0.3%
x264 [info]: i16 v,h,dc,p: 53% 20% 16% 12%
x264 [info]: i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 31% 15% 25%  4%  5%  6%  5%  5%  4%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 30% 15% 13%  6%  8%  9%  6%  8%  5%
x264 [info]: i8c dc,h,v,p: 50% 18% 26%  5%
x264 [info]: Weighted P-Frames: Y:4.8% UV:3.9%
x264 [info]: ref P L0: 73.6% 26.4%
x264 [info]: ref B L0: 81.7% 18.3%
x264 [info]: ref B L1: 94.9%  5.1%
x264 [info]: kb/s:782.51

encoded 8634 frames, 121.62 fps, 782.52 kb/s
```

without opencl
```
mc@debian64:~/develop-deb/x264_10/opencl$ ./x264 --threads 0  --bitrate 800 --preset faster --tune film -o video2.mkv test.mkv 
lavf [info]: 720x404p 0:1 @ 24000/1001 fps (vfr)
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.1 Cache64
x264 [info]: profile High, level 3.0
x264 [info]: frame I:184   Avg QP:16.66  size: 23148                           
x264 [info]: frame P:3387  Avg QP:20.29  size:  6307
x264 [info]: frame B:5063  Avg QP:21.40  size:  1900
x264 [info]: consecutive B-frames: 11.8% 26.1% 12.1% 50.0%
x264 [info]: mb I  I16..4: 22.4% 42.4% 35.3%
x264 [info]: mb P  I16..4: 11.4% 17.3%  2.9%  P16..4: 32.7% 12.4%  4.5%  0.0%  0.0%    skip:18.8%
x264 [info]: mb B  I16..4:  1.2%  1.5%  0.2%  B16..8: 34.9%  5.8%  0.4%  direct:11.9%  skip:44.1%  L0:42.5% L1:49.0% BI: 8.4%
x264 [info]: final ratefactor: 19.95
x264 [info]: 8x8 transform intra:52.9% inter:48.4%
x264 [info]: coded y,uvDC,uvAC intra: 49.4% 65.3% 17.7% inter: 10.9% 24.4% 0.3%
x264 [info]: i16 v,h,dc,p: 52% 20% 16% 12%
x264 [info]: i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 31% 15% 25%  4%  5%  6%  5%  5%  4%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 30% 16% 13%  6%  8%  9%  7%  8%  5%
x264 [info]: i8c dc,h,v,p: 50% 18% 26%  5%
x264 [info]: Weighted P-Frames: Y:4.6% UV:3.8%
x264 [info]: ref P L0: 74.2% 25.8%
x264 [info]: ref B L0: 82.2% 17.8%
x264 [info]: ref B L1: 94.8%  5.2%
x264 [info]: kb/s:782.64

encoded 8634 frames, 121.98 fps, 782.66 kb/s
```

no particular difference, can it be that my video card (nvidia GT 440) is not very powerful

---

### Post by andrew.46 on 2013-05-02
Thanks telperion, x264 now builds fine with opencl. Now to test it out :)

---

### Post by andrew.46 on 2013-05-02
I have a cutting edge CPU but a reasonably ordinary GPU:

With *--opencl*:

```

andrew@skamandros~/media/videos$ time \
> x264 --threads 0 --opencl \
>      --bitrate 800 --preset faster \
>      --tune film -o test_1.mkv Decay_2012_1080p_HQ.avi
lavf [info]: 1920x960p 1:1 @ 24000/1001 fps (vfr)
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX XOP FMA4 FMA3 SSEMisalign LZCNT BMI1
x264 [info]: OpenCL acceleration enabled with NVIDIA Corporation GeForce GTS 450 
x264 [info]: Compiling OpenCL kernels...
x264 [info]: profile High, level 4.0
x264 [info]: frame I:1306  Avg QP:26.55  size: 24994                           
x264 [info]: frame P:63991 Avg QP:31.17  size:  5491
x264 [info]: frame B:44200 Avg QP:33.48  size:  1514
x264 [info]: consecutive B-frames: 44.8%  3.0%  3.8% 48.5%
x264 [info]: mb I  I16..4: 33.6% 63.1%  3.2%
x264 [info]: mb P  I16..4:  8.1% 12.3%  0.0%  P16..4: 12.3%  1.5%  0.2%  0.0%  0.0%    skip:65.6%
x264 [info]: mb B  I16..4:  0.7%  1.0%  0.0%  B16..8:  8.1%  0.4%  0.0%  direct: 1.7%  skip:88.0%  L0:46.5% L1:52.2% BI: 1.3%
x264 [info]: final ratefactor: 33.17
x264 [info]: 8x8 transform intra:60.3% inter:84.7%
x264 [info]: coded y,uvDC,uvAC intra: 20.4% 15.4% 0.2% inter: 1.2% 0.6% 0.0%
x264 [info]: i16 v,h,dc,p: 53% 25% 12%  9%
x264 [info]: i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 22% 18% 50%  2%  1%  2%  1%  2%  2%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 26% 27% 13%  5%  6%  5%  7%  6%  5%
x264 [info]: i8c dc,h,v,p: 78% 10% 11%  0%
x264 [info]: Weighted P-Frames: Y:2.2% UV:1.3%
x264 [info]: ref P L0: 73.0% 27.0%
x264 [info]: ref B L0: 80.4% 19.6%
x264 [info]: ref B L1: 94.0%  6.0%
x264 [info]: kb/s:789.90

encoded 109497 frames, 79.11 fps, 789.90 kb/s

real	23m4.248s
user	107m11.544s
sys	8m34.957s
andrew@skamandros~/media/videos$ 

```

and without* --opencl*:

```

andrew@skamandros~/media/videos$ time \
> x264 --threads 0 \
>      --bitrate 800 --preset faster \
>      --tune film -o test_2.mkv Decay_2012_1080p_HQ.avi
lavf [info]: 1920x960p 1:1 @ 24000/1001 fps (vfr)
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX XOP FMA4 FMA3 SSEMisalign LZCNT BMI1
x264 [info]: profile High, level 4.0
x264 [info]: frame I:1342  Avg QP:27.09  size: 24026                           
x264 [info]: frame P:82588 Avg QP:31.67  size:  4766
x264 [info]: frame B:25567 Avg QP:32.14  size:   990
x264 [info]: consecutive B-frames: 68.0%  2.3%  1.2% 28.5%
x264 [info]: mb I  I16..4: 35.1% 61.8%  3.0%
x264 [info]: mb P  I16..4:  6.8%  9.9%  0.0%  P16..4: 12.1%  1.4%  0.2%  0.0%  0.0%    skip:69.5%
x264 [info]: mb B  I16..4:  0.5%  0.7%  0.0%  B16..8:  5.0%  0.2%  0.0%  direct: 0.9%  skip:92.7%  L0:46.3% L1:52.1% BI: 1.5%
x264 [info]: final ratefactor: 33.15
x264 [info]: 8x8 transform intra:59.6% inter:82.0%
x264 [info]: coded y,uvDC,uvAC intra: 19.9% 15.2% 0.2% inter: 1.2% 0.6% 0.0%
x264 [info]: i16 v,h,dc,p: 53% 26% 12%  9%
x264 [info]: i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 22% 18% 51%  2%  1%  2%  1%  2%  2%
x264 [info]: i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 26% 28% 13%  5%  6%  6%  7%  5%  6%
x264 [info]: i8c dc,h,v,p: 79% 10% 11%  0%
x264 [info]: Weighted P-Frames: Y:1.7% UV:1.0%
x264 [info]: ref P L0: 74.5% 25.5%
x264 [info]: ref B L0: 77.6% 22.4%
x264 [info]: ref B L1: 93.8%  6.2%
x264 [info]: kb/s:790.38

encoded 109497 frames, 102.35 fps, 790.38 kb/s

real	17m49.945s
user	119m35.897s
sys	0m25.827s
andrew@skamandros~/media/videos$ 

```

Now to interpret these results.....

---

### Post by telperion on 2013-05-03
> **andrew.46 said:**
> I have a cutting edge CPU but a reasonably ordinary GPU:

With *--opencl*:

```

andrew@skamandros~/media/videos$ time \
> x264 --threads 0 --opencl \
>      --bitrate 800 --preset faster \
>      --tune film -o test_1.mkv Decay_2012_1080p_HQ.avi
lavf [info]: 1920x960p 1:1 @ 24000/1001 fps (vfr)
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX XOP FMA4 FMA3 SSEMisalign LZCNT BMI1
x264 [info]: OpenCL acceleration enabled with NVIDIA Corporation GeForce GTS 450 
x264 [info]: Compiling OpenCL kernels...
x264 [info]: profile High, level 4.0

encoded 109497 frames, 79.11 fps, 789.90 kb/s

real	23m4.248s
user	107m11.544s
sys	8m34.957s
andrew@skamandros~/media/videos$ 

```

and without* --opencl*:

```

andrew@skamandros~/media/videos$ time \
> x264 --threads 0 \
>      --bitrate 800 --preset faster \
>      --tune film -o test_2.mkv Decay_2012_1080p_HQ.avi
lavf [info]: 1920x960p 1:1 @ 24000/1001 fps (vfr)
x264 [info]: using SAR=1/1
x264 [info]: using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2 AVX XOP FMA4 FMA3 SSEMisalign LZCNT BMI1
x264 [info]: profile High, level 4.0


encoded 109497 frames, 102.35 fps, 790.38 kb/s

real	17m49.945s
user	119m35.897s
sys	0m25.827s
andrew@skamandros~/media/videos$ 

```

Now to interpret these results.....


it seems that with a multicore cpu (I have a Q8300) there is no advantage to using OpenCL, and even disadvantages ...

---

### Post by scottro on 2013-05-03
I'm going to post my own howto, which covers doing various things with ffmpeg (and mencoder), in the hope it helps someone.  

[http://home.roadrunner.com/~computertaijutsu/dvds.html](http://home.roadrunner.com/~computertaijutsu/dvds.html)

Even though it's more RH and offshoots oriented, most of it will work out of the box on Ubuntu.

---

### Post by andrew.46 on 2013-05-03
> **scottro said:**
> I'm going to post my own howto, which covers doing various things with ffmpeg (and mencoder), in the hope it helps someone.

A lot of work in there :). A small quibble though: is this completely true:

> 
Most current distributions actually use the more modern genisoimage. 


I have personally used mkisofs for many years with absolutely zero issues at all, mind you I am loathe to reignite the war between Debian and Jörg Schilling...

---

### Post by andrew.46 on 2013-05-04
With the reopening of the Tutorials section on these Forums I have updated my vlc guide for Raring Ringtail and here it is:

Howto: Compile the development version of vlc under the latest Ubuntu release 
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

It feels good to be 'back in the saddle' :)

---

### Post by scottro on 2013-05-04
@andrew.46, I don't want to reignite that fire either.  As I said it is mostly based on RH based distros, but it seems to be the case with Fedora and Ubuntu, as well as #!Crunchbang.  

If you are using mkisofs on Ubuntu, please try running mkisofs -version and see what you get.  

However, that particular issue that I had, with files over 4 GB, was on CentOS, which is based on RHEL, therefore, uses older packages.  It might just be that the CentOS version (and this was CentOS 5.x) was the one with the problem, and if Mr. Schilling has made newer versions of mkisofs, it's no longer a problem. 

EDIT

I've changed the wording, to indicate that my issue was with CentOS 5.x, and that I've heard, but untested by me, that current mkisofs also gives no problem, however, most RH and Debian based distros use genisoimage.  As I said, I too, have no wish to reignate fires, so I left out all reasons behind the changes, and also reworded it to indicate that the only problem I had was with a CentOS 5.x mkisoimage.

Thanks for the information, I actually, to my chagrin, hadn't realized that this was part of the cdrtools controversy, and of course, I should have realized that.

---

### Post by andrew.46 on 2013-05-04
Well to tell the truth I do my burning on Slackware :). So my version of mkisofs is:

```

andrew@skamandros~$ mkisofs --version
mkisofs 3.01a13 (x86_64-unknown-linux-gnu) Copyright (C) 1993-1997 Eric Youngdale (C) 1997-2013 Joerg Schilling

```

I believe at the moment the current limitation for ISO-9660 is 8TB. The man pages for mkisofs state:

```

       ISO-9660/JOLIET/UDF filesystems are limited to a maximum size of 8 TB.  The maxi-
       mum size of a single file is 8 TB (single files in UDF are currently  limited  to
       aprox.  200 GB).   If yo like to have files larger than 2 GB, you need to specify
       -iso-level 3 or above.  If a HFS hybrid is created, the  maximum  file  size  for
       files in the HFS hybrid is 2 GB in any case.

```

But certainly it is difficult to get mkisofs running under Ubuntu and it looks like [the PPA that was a decent way of doing this]("https://launchpad.net/~brandonsnider/+archive/cdrtools") has been neglected of late :(.

---

### Post by scottro on 2013-05-04
A quick google indicates that the version used in CentOS 5.x was mkisofs 2.x.  Also, to be clear, the problem wasn't consistent, and not a problem with video files, only some data files.  At any rate, I learned something today, so many thanks.  (And the article has been edited a bit, which is good, as otherwise, it might have--completely unintentionally--reignited the old fight.)

---

### Post by FakeOutdoorsman on 2013-05-14
ffplay trick of the day:
```
ffplay input.txt
```

Text file to video:
```
ffmpeg -chars_per_frame 200 -i input.txt output.mkv
```

Random junk to video:
```

ffplay -f tty -chars_per_frame 200 /dev/urandom
ffmpeg -f tty -chars_per_frame 200 -i /dev/urandom -t 10 output.mkv
```

Show FFmpeg Changelog via http (stolen from ubitux in #ffmpeg-devel)
```
ffplay -chars_per_frame 200 -f tty 'http://git.videolan.org/?p=ffmpeg.git;a=blob_plain;f=Changelog;hb=HEAD'
```

---

### Post by andrew.46 on 2013-05-18
For those who do not follow the svn MPlayer there is an MPlayer release earlier this month: 1.1.1. A few details here:

[http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

BTW I am considering adding a guide for MPlayer to the 'Tutorials' section, still watching to make sure there are no further changes to this subforum before I undertake this not small amount of effort...

---

### Post by shantiq on 2013-05-19
found this ```
ffmpeg -chars_per_frame 200 -i input.txt output.mkv 
```

posted earlier by [FakeOutdoorsman  ]("http://ubuntuforums.org/showthread.php?t=2096866&p=12647881#post12647881")
to turn text [.txt file]to video

and thought how nice! but how to use it so that it can be used to post the resulting video on a video-sharing site (seriously) or that thoughtful ransom note [aargh!] **in a way that is readable**
so here:


```
ffmpeg -chars_per_frame 200  -s hd720 -i NAME.txt -b:v 4000k  output.mkv && \
ffmpeg  -i output.mkv -filter:v 'setpts=[COLOR=#800000]**6**[/COLOR][COLOR=#800000]**.5**[/COLOR]*PTS' -b:v 4000k  outputslow.mkv \
&& rm output.mkv
```


if you want slower try 7.0 or 7.5 or even slower 12.0 is a really comfortable reading speed

---

### Post by scottro on 2013-05-19
That's actually pretty neat.  Thank you.

---

### Post by andrew.46 on 2013-05-29
As a trial I have placed an MPlayer compile guide back on these Forums:

 Howto: Build the svn MPlayer under the latest release version of Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2149564](http://ubuntuforums.org/showthread.php?t=2149564)

Interesting to see if it sinks or swims :)

---

### Post by FakeOutdoorsman on 2013-06-12
New filter: rotate. Now you can rotate your videos using any arbitrary angle. Note that the angle is expressed in radians, although you can have it [convert radians to degrees](http://en.wikipedia.org/wiki/Radians#Conversion_between_radians_and_degrees) for you.

Rotate 33 degrees clockwise:
```
$ ffplay input.mkv -vf rotate="33*(PI/180)"
```
[ATTACH=CONFIG]243809[/ATTACH]
(That is a hop plant if you're wondering).

Examples from the [docs](http://ffmpeg.org/ffmpeg-filters.html#rotate):

Apply a constant rotation with period T, starting from an angle of PI/3:
```
rotate=PI/3+2*PI*t/T
```

Rotate the video, output size is chosen so that the whole rotating input video is always completely contained in the output:
```
rotate='2*PI*t:ow=hypot(iw,ih):oh=ow'
```

Rotate the video, reduce the output size so that no background is ever shown:
```
rotate=2*PI*t:ow='min(iw,ih)/sqrt(2)':oh=ow:c=none
```

---

### Post by andrew.46 on 2013-06-13
My brain hurts a little after reading those commandlines :(

---

### Post by shantiq on 2013-06-14
> **andrew.46 said:**
> My brain hurts a little after reading those commandlines :(    Maybe time for Windows or a Big Mac:KS:KS:KS:KS     Just joking....

Soon gonna be a time ffmpeg can walk on water or at least has a line of code that allows you to do that

say    ```
ffmpeg -i Jesus Copy [and for good measure]  -f///¹²³-457--0 --Galilee --feet--on--water //0
```

or at the very least makes you breakfast  ....   it is amazing software

---

### Post by andrew.46 on 2013-06-14
> **shantiq said:**
> Maybe time for Windows or a Big Mac:KS:KS:KS:KS     Just joking....

I run Windows at work and I have downloaded a nice static version of FFmpeg that runs *very* nicely with [Console 2]("http://sourceforge.net/projects/console-devel/files/console-releases/"). Not the same as Linux of course but the FFmpeg magic still produces great media files even on the limited platform of Windows :). But as for a Big Mac I am a pretty dedicated vegan so that will not happen any time soon!

---

### Post by shantiq on 2013-06-14
well Andrew me too no meat [i meant the machine not the food];   the animals were never guilty and do not deserve murder is my creed

i am sure here we can get help again from the mighty F

```
ffmpeg  -i me  --nomeat --no dairy copy /0¹²v-y+x
```


and seriously all interlude jokes apart ffmpeg is more and more mighty by the month and thanx to all guys here who keep showing us the tricks

---

### Post by FakeOutdoorsman on 2013-06-26
ffplay can play itself:
```
$ ffplay /usr/bin/ffplay
```
It might be loud, and your ffplay binary location will probably vary.

---

### Post by andrew.46 on 2013-06-28
Just to extend this thread a little further some may be interested to know that a new version of mkvtoolnix has been released:

```

andrew@skamandros~$ mkvmerge --version
mkvmerge v6.3.0 ('You can't stop me!') built on Jun 28 2013 21:16:37

```

Mosu never stops :)

---

### Post by andrew.46 on 2014-03-23
Hey, when did this thread go to sleep!! New version of mkvtoolnix has been released:

```

andrew@ilium~$ **[COLOR="#FF0000"]mkvmerge --version[/COLOR]**
mkvmerge v6.8.0 ('Theme for Great Cities') 64bit built on Mar 15 2014 16:47:31

```

with the beginning of support for h.265 encoded files. Upcoming news is that Mosu is rewriting the gui to support QT rather than wxWidgets. Interesting times ahead :).

---

### Post by andrew.46 on 2014-06-26
And in a great bit of news for abcde users development, which has slumbered for a while, will be moving along soon with a move to git and many other new developments...

---

### Post by mc4man on 2014-06-27
> **andrew.46 said:**
> And in a great bit of news for abcde users development, which has slumbered for a while, will be moving along soon with a move to git and many other new developments...
A git link would be great (when it's up if not already, only saw an old one & fedora's

Are there any plans to add fdkaac?

---

### Post by andrew.46 on 2014-06-27
Steve (abcde main developer) is keen to get a release out and announce the new git site in one go, so a little time yet. Definitely time for fdkaac after that though. I have commit access and would be more than happy to push a patch through if you are interested in producing one?

Mind you looks like I have to get a working knowledge of git first :)

---

### Post by SeijiSensei on 2014-06-28
Out of curiosity, what is the status of the mplayer/mplayer2 fork these days?  Ubuntu still uses the latter, which works well for me, but is there any chance of a reconciliation some time soon?  Are we missing anything of importance by Debian's continuing to rely on the mplayer2 code?

---

### Post by andrew.46 on 2014-06-28
MPlayer 2 has been a little quiet since [October last year]("http://git.mplayer2.org/mplayer2/") while latest MPlayer patch was yesterday:

```

------------------------------------------------------------------------
r37230 | reimar | **[COLOR="#FF0000"]2014-06-29 05:57:15 +1000 (Sun, 29 Jun 2014)[/COLOR]** | 5 lines

ad_spdif: do not call internal write_packet function directly.

Use av_write_frame instead.

Patch by Jan Andres [jandres gmx net].
------------------------------------------------------------------------

```

I suspect that Debian has jumped on the wrong media boat, not for the first time either :)

---

### Post by andrew.46 on 2014-06-30
> **mc4man said:**
> Are there any plans to add fdkaac?

BTW a quick and dirty test suggests that fdkaac actually works *out of the box* with a current abcde. I used AtomicParsley for the tagging (did not investigate fdkaac's tagging ability as this might need some adjustment) and added the following to ~/.abcde.conf:

```

AACENC=fdkaac
AACTAG=AtomicParsley
OUTPUTTYPE="m4a"
AACENCOPTS="-b 128"

```

plus the usual options and this certainly worked for me for a test cd. Hopefully you have time to see if same works for you?

---

