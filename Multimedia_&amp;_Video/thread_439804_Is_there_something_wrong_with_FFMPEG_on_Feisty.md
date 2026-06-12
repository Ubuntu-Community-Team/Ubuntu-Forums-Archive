---
title: "Is there something wrong with FFMPEG on Feisty?"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by michwill on 2007-05-11
Hi All,

I'm having severe trouble with ffmpeg on Feisty Fawn.  I've got MythTV installed, and, for whatever reason, I can't transcode to anything useful with ffmpeg.  I've tried using "nuvexport", "myth3gp", and general "transcode" all to no avail.  Also, whenever I try to burn to DVD using Mytharchive, I receive an error informing me that the process "failed while running ffmpeg to re-encode video". . .

Does anyone have any experience with this issue?  If so, please advise.


NOTE:  I've used the default ffmpeg from the repositories, as well as installing from source.  Nothing seems to work, but I'm still pretty sure the problem is with ffmpeg.


Thanks,
Michael

---

### Post by reclusivemonkey on 2007-05-11
I'm at work right now so I can't give you any useful details, but I believe the ffmpeg in the medibuntu repos is compiled with more formats supported. However, I know 3gp is not compiled in.

---

### Post by michwill on 2007-05-11
I tried adding the medibuntu repositories, but it made no difference.  I heard on the MythTV mailing lists that ffmpeg has changed the way it encodes sound so that might be the issue.

---

### Post by michwill on 2007-05-11
Ok, this is extremely frustrating.  I've tried editing every possible option to no avail.  There isn't sufficient output in the scripts to indicate what exactly is going wrong.  I edited the "mythburn.py" script so that it output the variable "result", but it simply indicates a failure and exit code of 256;  no more, no less.  Is there anyone out there that's actually getting this to work successfully?

---

### Post by zaziork on 2007-05-13
What are you trying to convert? I've been playing about with DSS, and have successfully used ffmpeg to transcode mpeg2/ac3 mpg (ripped from DVD) to mpeg4/acc with h264 (which I then put in an mp4 container and hinted with MP4Box..  all streamed fine with DSS). Also tried transcoding to mpeg4/acc which works fine. I'm on Fiesty, and compiled ffmpeg from source.

---

### Post by michwill on 2007-05-13
> **zaziork said:**
> What are you trying to convert? I've been playing about with DSS, and have successfully used ffmpeg to transcode mpeg2/ac3 mpg (ripped from DVD) to mpeg4/acc with h264 (which I then put in an mp4 container and hinted with MP4Box..  all streamed fine with DSS). Also tried transcoding to mpeg4/acc which works fine. I'm on Fiesty, and compiled ffmpeg from source.

Basically I'm trying to use MtyhArchive and/or NuvExport to work with ".nuv" files (from MythTV) and neither work.  MtyhArchive hiccups with an unintelligible ffmpeg error, and NuvExport creates video with no sound.  Any ideas?  Ultimately I'd like to have a version for DSS as well as a version for burning to DVD. Perhaps you could provide me with some examples of ffmpeg commands to do this?

Thanks

---

### Post by michwill on 2007-05-14
FYI, only DivX exporting (via nuvexport) produces audio.  The others either produce 100% buzzing or nothing.

---

### Post by michwill on 2007-05-14
Hrm, I'm getting the following from "mythburn.log" when trying to use mytharchive.:

```

mythburn.py (0.1.20061201-1) starting up...
Process priority 8
script path:/usr/share/mythtv/mytharchive/scripts
myth share path:/usr/share/mythtv
passed job file: /tmp/config/mydata.xml
passed progress log file: /tmp/logs/progress.log
mythburn.py (0.1.20061201-1) starting up...
Found 1 CPUs
Obtaining MythTV settings from MySQL database for hostname mythtv-desktop
Processing Mythburn job number 1.
Options - mediatype = 2, doburn = 1, createiso = 0, erasedvdrw = 1
          savefilename = ''
Looking for: /usr/share/mythtv/mytharchive/themes/G.A.N.T./theme.xml
Loading font 0, /usr/share/mythtv/FreeSans.ttf size 19
Loading font 1, /usr/share/mythtv/FreeSans.ttf size 15
Loading font 2, /usr/share/mythtv/FreeSans.ttf size 14
wantIntro: 1, wantMainMenu: 1, wantChapterMenu:1, wantDetailsPage: 1
Final DVD Video format will be ntsc
There are 1 files to process
Pre-processing file '1007_20070508233000.nuv' of type 'recording'
          Seinfeld
2007-05-14 12:00:20.320 Opening /var/lib/mythtv/recordings/1007_20070508233000.nuv
Input #0, nuv, from '/var/lib/mythtv/recordings/1007_20070508233000.nuv':
  Duration: 00:38:18.6, start: 0.000000, bitrate: 1411 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 480x480,  0.03 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 1411 kb/s
0: start_time: 0.000 duration: 2.299
1: start_time: 0.000 duration: 2.299
stream: start_time: 0.000 duration: 2298.694 bitrate=1411 kb/s
2007-05-14 12:00:20.346 duration = 2298
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file duration="2298" filename="/var/lib/mythtv/recordings/1007_20070508233000.nuv" type="nuv">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="0" codec="mpeg4" ffmpegindex="0" fps="0.0333667" height="480" id="0" streamindex="0" width="480"/>        
                <audio bitrate="1411200" channels="2" codec="mp3" ffmpegindex="1" id="1" language="N/A" samplerate="48000" streamindex="1"/>        
        </streams>    
</file>
Video resolution is 480 by 480
*************************************************************
Processing file 1007_20070508233000.nuv of type recording
*************************************************************
File type is 'nuv'
Video codec is 'mpeg4'
2007-05-14 12:00:20.680 Opening /var/lib/mythtv/recordings/1007_20070508233000.nuv
Input #0, nuv, from '/var/lib/mythtv/recordings/1007_20070508233000.nuv':
  Duration: 00:38:18.6, start: 0.000000, bitrate: 1411 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 480x480,  0.03 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 1411 kb/s
0: start_time: 0.000 duration: 2.299
1: start_time: 0.000 duration: 2.299
stream: start_time: 0.000 duration: 2298.694 bitrate=1411 kb/s
2007-05-14 12:00:20.686 duration = 2298
streaminfo.xml :-
<?xml version="1.0" ?>
<!DOCTYPE FILEINFO>
<file duration="2298" filename="/var/lib/mythtv/recordings/1007_20070508233000.nuv" type="nuv">    
        <streams count="2">        
                <video aspectratio="1.33333" bitrate="0" codec="mpeg4" ffmpegindex="0" fps="0.0333667" height="480" id="0" streamindex="0" width="480"/>        
                <audio bitrate="1411200" channels="2" codec="mp3" ffmpegindex="1" id="1" language="N/A" samplerate="48000" streamindex="1"/>        
        </streams>    
</file>
Preferred audio languages eng and eng
Video id: 0x0, Audio1: [1] 0x1 (MP3, N/A), Audio2: [-1] - 0x-1 (N/A, N/A)
Aspect ratio is 4:3
Re-encoding audio and video from nuv file
Encoding profile (SP) found
mythtranscode started PID = 8759
Waiting for mythtranscode to create the fifos
2007-05-14 12:00:21.052 Using runtime prefix = /usr
2007-05-14 12:00:21.103 New DB connection, total: 1
2007-05-14 12:00:21.110 Enabled verbose msgs: important
2007-05-14 12:00:21.115 New DB connection, total: 2
2007-05-14 12:00:21.178 Using protocol version 31
2007-05-14 12:00:21.385 mythtranscode: 0% Completed @ 28.5714 fps.
Running ffmpeg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-xvid --enable-libdts --enable-amr_nb --enable-amr_wb --enable-pp --enable-libogg --enable-libgsm --enable-x264 --enable-liba52 --enable-libtheora --extra-cflags=-Wall -g -fPIC -DPIC --cc=ccache cc --enable-swscaler
  libavutil version: 49.4.0
  libavcodec version: 51.40.2
  libavformat version: 51.11.0
  built on Mar 29 2007 11:08:52, gcc: 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)
Input #0, s16le, from '/tmp/work/1/audout':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Input #1, rawvideo, from '/tmp/work/1/vidout':
  Duration: N/A, bitrate: N/A
  Stream #1.0: Video: rawvideo, yuv420p, 480x480,  0.03 fps(r)
Output #0, dvd, to '/tmp/work/1/newfile2.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=5-31, 4771 kb/s,  5.00 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #1.0 -> #0.0
  Stream #0.0 -> #0.1
[mpeg2video @ 0xb7d83808]MPEG1/2 does not support 5/1 fps
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
************************************************************
ERROR: Failed while running ffmpeg to re-encode video.
Command was /usr/bin/ffmpeg -y -f s16le -ar 48000 -ac 2 -i /tmp/work/1/audout -f rawvideo -pix_fmt yuv420p -s 480x480 -aspect 1.33333 -r 0.0333667 -i /tmp/work/1/vidout -aspect 1.33333 -r 0.0333667 -s 720x480 -b 4771k -vcodec mpeg2video -qmin 5 -ab 192 -ar 48000 -acodec ac3 -f dvd "/tmp/work/1/newfile2.mpg"
************************************************************

chmod: changing permissions of `/tmp': Operation not permitted
chmod: changing permissions of `/tmp/.ICE-unix': Operation not permitted
chmod: changing permissions of `/tmp/gconfd-root': Operation not permitted
chmod: `/tmp/gconfd-root': Permission denied
chmod: changing permissions of `/tmp/.X0-lock': Operation not permitted
chmod: changing permissions of `/tmp/orbit-root': Operation not permitted
chmod: `/tmp/orbit-root': Permission denied
chmod: changing permissions of `/tmp/gedit.root.1740485529': Operation not permitted
chmod: changing permissions of `/tmp/.X11-unix': Operation not permitted
chmod: changing permissions of `/tmp/.X11-unix/X0': Operation not permitted
Terminated
```


. . .notice the param errors.  What is different/new in FFMPEG that mytharchive isn't taking into account?

---

### Post by zaziork on 2007-05-14
I'm not really familiar with mythtv or .nuv files per se, so can't really be much help here... however, some general observations: seems not to like encoding for mpeg2 @ 5fps.. That's low in any case, unless I'm misunderstanding the attribute; PAL DVD is usually 25fps. Have you tried changing the codec/format? Encoding to mpeg4 with h264 in mp4 container would be the way to go for streaming via DSS.. are you also trying to burn the files to DVD so they can be played in a stand-alone dvd player (ie. mpeg 2/ac3 in VOB)?

---

### Post by michwill on 2007-05-15
> **zaziork said:**
> I'm not really familiar with mythtv or .nuv files per se, so can't really be much help here... however, some general observations: seems not to like encoding for mpeg2 @ 5fps.. That's low in any case, unless I'm misunderstanding the attribute; PAL DVD is usually 25fps. Have you tried changing the codec/format? Encoding to mpeg4 with h264 in mp4 container would be the way to go for streaming via DSS.. are you also trying to burn the files to DVD so they can be played in a stand-alone dvd player (ie. mpeg 2/ac3 in VOB)?

Well, as I said, it's all occurring through mytharchive or nuvexport.  Nuvexport worked on previous systems (6.06), and it doesn't now.  I'm guessing something changed with FFMpeg or one of the transcoding systems.  I'm really not sure, and there isn't an intuitive chain-of-output to follow.

---

### Post by joereith on 2007-05-20
i would say that you just try using tovid. It works the best for me and you can modify all of the settings

---

### Post by ebs16 on 2007-06-14
I ran into this same problem. A quick repo update pulled a new version of ffmpeg and fixed the problem.

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by tagra123 on 2007-09-18
_HOW TO GET GOOD VIDEO FOR DVD USING FFMPEG AND NUVEXPORT_

My system is not using a pvr-150 250, etc..

Using the plain ole WinTVGo Card bt chipset
Upgraded from myth .18 to mythtv .20.2 because of zaptoit stopping its free service -- converted to schedules direct.

We create dvd's with our files.

Small little glitch 

Myth archive cannot seem to keep audio and video in sync -- most of what Iv'e read says that mytharvhive works best with the pvr150 or better because it record directly to mpeg.

Let's try the reliable nuvexport

Installed nuvexport-0.4-0.20070804.svn.tar.bz2

NuvExport version 0.4  was also creating very poor pixeled video.

Here's a small little modification to the nuvexport dvd module to get the video  that nuvexport creates looking good again.
```

sudo gedit /usr/local/share/nuvexport/export/ffmpeg/DVD.pm
```

Find this line near the bottom of the opened file:

```
$self->{'ffmpeg_xtra'} = $self->param('bit_rate', $self->{'v_bitrate'})
```

comment out that line by placing a # and add this line
```
$self->{'ffmpeg_xtra'} = ' -b ' . $self->{'v_bitrate'} . 'k'
```

The two lines should look like this when finished
```
# $self->{'ffmpeg_xtra'} = $self->param('bit_rate', $self->{'v_bitrate'})
$self->{'ffmpeg_xtra'} = ' -b ' . $self->{'v_bitrate'} . 'k'
```


works like a charm now.

More about this here:
[http://www.mythtv.org/pipermail/mythtv-commits/2006-December/024023.html](http://www.mythtv.org/pipermail/mythtv-commits/2006-December/024023.html)

---

