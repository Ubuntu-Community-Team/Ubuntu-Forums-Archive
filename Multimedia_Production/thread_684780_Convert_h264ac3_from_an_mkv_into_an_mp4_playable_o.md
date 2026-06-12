---
title: "Convert h264/ac3 from an mkv into an mp4 playable on an Xbox 360"
date: 2008-02-01
forum: Multimedia Production
---

### Post by jexxie on 2008-02-01
Hi all,

I've got a series of hidef TV episodes in an mkv format, I've extracted the video and audio streams, transcoded the audio into aac (was 5.1 ac3), and wrapped it into an mp4, but the file still doesn't play on the 360 -- does anyone know a 'good' set of x264 encoder options that will play on the 360? (I'm assuming that the video is the problem, as it shouldn't be the audio.)  (Avidemux fails to transcode this file, it crashes.)

(Later I'll post a guide on this.)

Here's some info on the video file:
```
me@myDesktop:~/videos$ midentify test.mkv
ID_AUDIO_ID=0
ID_AID_0_LANG=und
ID_VIDEO_ID=0
ID_FILENAME=test.mkv
ID_DEMUXER=mkv
ID_VIDEO_FORMAT=avc1
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=1280
ID_VIDEO_HEIGHT=720
ID_VIDEO_FPS=23.976
ID_VIDEO_ASPECT=1.7778
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=0
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=6
ID_LENGTH=2595.97
ID_VIDEO_CODEC=ffh264
ID_AUDIO_BITRATE=448000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_AUDIO_CODEC=a52
```

```
me@myDesktop:~/videos$ mkvinfo test.mkv 
+ EBML head
|+ Doc type: matroska
|+ Doc type version: 1
|+ Doc type read version: 1
+ Segment, size 1153738746
|+ Seek head (subentries will be skipped)
|+ EbmlVoid (size: 4027)
|+ Segment information
| + Timecode scale: 1000000
| + Muxing application: libebml v0.7.7 + libmatroska v0.8.1
| + Writing application: mkvmerge v2.0.2 ('You're My Flame') built on Sep 20 2007 09:25:45
| + Duration: 2595.968s (00:43:15.968000000)
| + Date: Tue Jan 15 03:43:23 2008 UTC
| + Segment UID: 0x6d 0xc5 0xa7 0x4c 0xba 0x32 0xd1 0x8f 0x03 0xe3 0xe2 0x69 0x35 0xf4 0x37 0xd1
|+ Segment tracks
| + A track
|  + Track number: 1
|  + Track UID: 1851004858
|  + Track type: audio
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 1
|  + MinCache: 0
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: A_AC3
|  + Codec decode all: 1
|  + Default duration: 32.000ms (31.250 fps for a video track)
|  + Language: und
|  + Audio track
|   + Sampling frequency: 48000.000000
|   + Channels: 6
| + A track
|  + Track number: 2
|  + Track UID: 1
|  + Track type: video
|  + Enabled: 1
|  + Default flag: 1
|  + Forced flag: 0
|  + Lacing flag: 0
|  + MinCache: 1
|  + Timecode scale: 1.000000
|  + Max BlockAddition ID: 0
|  + Codec ID: V_MPEG4/ISO/AVC
|  + Codec decode all: 1
|  + CodecPrivate, length 39
|  + Default duration: 41.708ms (23.976 fps for a video track)
|  + Language: eng
|  + Video track
|   + Pixel width: 1280
|   + Pixel height: 720
|   + Interlaced: 0
|   + Display width: 16
|   + Display height: 9
|+ EbmlVoid (size: 1024)
|+ Cluster
```

Any help is appreciated, TIA!

---

### Post by rootkit on 2008-02-01
If you know what settings does the Xbod360 accepts you can tweak my tool: [http://ubuntuforums.org/showthread.php?t=684571](http://ubuntuforums.org/showthread.php?t=684571)

---

### Post by jexxie on 2008-02-01
Xbox 360 supports the following for H.264:
·         File Extensions: .mp4, .m4v, mp4v, .mov
·         Containers: MPEG-4, QuickTime
·         Video Profiles: Baseline, main, and high (up to Level 4.1) profiles.
·         Video Bitrate: 10 Mbps with resolutions of 1920 x 1080 at 30fps.
·         Audio Profiles: 2 channel AAC low complexity (LC)
·         Audio Max Bitrate: No restrictions

Source: [http://blogs.msdn.com/xboxteam/archive/2007/11/30/december-2007-video-playback-faq.aspx](http://blogs.msdn.com/xboxteam/archive/2007/11/30/december-2007-video-playback-faq.aspx)

---

### Post by rootkit on 2008-02-02
Try this script and let me know

---

### Post by jexxie on 2008-02-04
The script is runing now, appears to be working, I'll update here if it works or not.
Thanks!

(Note: your script should do some better detection on what applications are accessible, (mine failed since I didn't have faac installed. ) )

---

### Post by rootkit on 2008-02-04
> **jexxie said:**
> The script is runing now, appears to be working, I'll update here if it works or not.
Thanks!

(Note: your script should do some better detection on what applications are accessible, (mine failed since I didn't have faac installed. ) )
I'll add it as dependency, tnx

---

### Post by jexxie on 2008-02-04
I cancelled the script's execution, it wanted to take 5-6 hours to encode the video file, which I felt was...long (also was processing at 2fps, on my amd 4800+)

I'll keep this thread updated as I solve this, I should have used mencoder in the beginning anyways (I'll try with that now)

Thanks for your scripts rootkit

---

### Post by rootkit on 2008-02-05
speed depends on resolution, fps and settings.
I use insane settings, but 2 FPS is too low.
What is your resolution?

---

### Post by jexxie on 2008-02-06
The video it was encoding was at 1280x720 -- I tried the script on some other avi's, works great for Xbox playback.

Thanks for your help =)

---

### Post by rootkit on 2008-02-06
Good.
I can give you more parameters that gives you both speed and quality.
Want to help me?

---

### Post by jexxie on 2008-02-08
Sure, let me know what I can do to help.

Also, with the script, is there a way to autodetect video bitrates instead of having a hard cap?

---

### Post by rootkit on 2008-02-08
> **jexxie said:**
> Sure, let me know what I can do to help.

Also, with the script, is there a way to autodetect video bitrates instead of having a hard cap?
yes, in the next version ;)

---

### Post by m3_del on 2008-02-08
So is this script just remuxing the files to an mp4? or converting? Just curious as converting takes forever.

---

### Post by jexxie on 2008-02-08
The script takes the video file you provide, scales it to the resolution you set, and rips the audio, trancodes the audio to low complexity aac, rencodes the video with x264 and muxes it into an mp4 container.

You ran a script without reading what it does?  I hope you never 'learn better', but you should read what things do before running them.

---

### Post by m3_del on 2008-02-08
I have not run the script, hence the questions. But my question to you is why re-encode the video? You can just change the 67 64 00 33 byte to 67 64 00 29 at the beginning of the file. saving the time of re-encoding...I suppose if you want to change the resolution...

---

### Post by jexxie on 2008-02-08
Sure, let me know what options you recommend -- I'm pretty good with bash scripting as well, so I can help out there.

---

### Post by rootkit on 2008-02-09
```

bframes=6
b-pyramid
weightb
bime
b-rdo
direct_pred=auto
partitions=p8x8,b8x8,i8x8,i4x4
8x8dct
threads=auto

```
please let me know.
If they don't works enable them one at time please.
I await your reply :)

---

### Post by shelbydz on 2008-02-09
I am also looking for help with this. I found a set of commands here to re-mux MKV into MP4, they play on my computer, but not my Xbox. 

Let me know what I can help with here.

---

### Post by rootkit on 2008-02-09
> **shelbydz said:**
> I am also looking for help with this. I found a set of commands here to re-mux MKV into MP4, they play on my computer, but not my Xbox. 

Let me know what I can help with here.
Why remux? encode directly to mp4

---

### Post by m3_del on 2008-02-10
> **rootkit said:**
> Why remux? encode directly to mp4

Encoding takes longer. No matter what you encode the ac3 audio to aac but you do not need to convert the video....

Shelbydz you can check this thread out [http://ubuntuforums.org/showthread.php?t=689757](http://ubuntuforums.org/showthread.php?t=689757)

---

### Post by jexxie on 2008-02-12
rootkit, I'm running a video encode on the video now -- I'll report back later tonight or tomorrow with the results.

---

### Post by jexxie on 2008-02-19
I'm working on a bash script to do this for me -- the basic script is done -- I'm adding a few more intelligent things like codec detection, so that if the mkv source file is h264, it'll just copy the video without re-encoding it over again. One step I haven't figured out yet for it is a way to script the hexediting bit, anyone have some ideas?

---

### Post by m3_del on 2008-02-20
Things I have seen people use is awk or sed, but so far all my attempts using them are failures.

---

### Post by jexxie on 2008-02-22
Well, here's my work thusfar -- works great for me, needs a bit more improvement on the h264 remuxing side. Feel free to make modifications, or update things -- or even post here with suggestions to improve on it.

Here's a an AVI rip of my Zoolander movie, and I'll convert it to the h264 video stream, with LC-AAC audio, muxed in an MP4 container:
me@myDesktop:~/videos$ reMuxToMP4 Zoolander.avi
 [x] Source filename: Zoolander.avi
 [x] Destination filename: Zoolander.mp4
 [x] Video stream found, 640 x 272 @ 25.000, using ffodivx
 [x] Audio stream found, 2 audio channels, using mad
 [x] Dumping the audio for normalizing...success
 [x] Normalizing the audio...success
 [x] Encoding the audio to low-complexity AAC...success
 [x] Extracting audio from MP4 container (silly neroAacEnc)...success
 [x] Encoding video to h264, first pass...success
 [x] Encoding video to h264, second pass...success
 [x] Muxing video at 25.000...success
 [x] Deleting audio and video tempfiles...success
 [o] All done!

---

### Post by m3_del on 2008-02-22
Nice work. Question. WHen you say "if video is already h264, don't encode, just copy.
#   this appears to be buggy, research -- the terminator video streams fail to import with MP4Box"

What do you mean by the video streams fail to import? Are you talking about large video streams? If so, that is fixed by an MP4Box patch....I have it listed in my post...

---

### Post by jexxie on 2008-02-22
Here's the error that I get:
```
me@myDesktop:~/videos$ reMuxToMP4 test.mkv
 [x] Source filename: test.mkv
 [x] Destination filename: test.mp4
 [x] Video stream found, 1280 x 720 @ 23.976, using ffh264
 [x] Audio stream found, 6 audio channels, using a52
 [x] Dumping the video...success
 [x] Muxing video at 23.976...failed
 [i] Showing the last 5 lines from the logfile (log.19:34:44-2008-02-22.txt)...
 [x] Muxing video at 23.976...   (BitStream Not Compliant)Cannot find H264 start code
Error importing test.mp4.264: BitStream Not Compliant
14382's retcode: 1
failed

```

---

### Post by jexxie on 2008-02-27
Here's an update to the script, added application detection so it dies gracefully if certain apps aren't installed, and a few other bugfixes.

---

### Post by rootkit on 2008-02-27
It seems a stripped version of my mkmp4 script, apart that is uses bad arguments (eg. spp, scale, -vc null)

---

### Post by jexxie on 2008-02-27
Feel free to post additions or improvements =)

---

### Post by m3_del on 2008-02-28
why is -vc null a bad argument?

mplayer recomends that to improve performance

---

### Post by rootkit on 2008-02-29
I'ts replaced by -novideo now

---

### Post by webjames on 2008-03-08
> **jexxie said:**
> Here's the error that I get:
```
me@myDesktop:~/videos$ reMuxToMP4 test.mkv
 [x] Source filename: test.mkv
 [x] Destination filename: test.mp4
 [x] Video stream found, 1280 x 720 @ 23.976, using ffh264
 [x] Audio stream found, 6 audio channels, using a52
 [x] Dumping the video...success
 [x] Muxing video at 23.976...failed
 [i] Showing the last 5 lines from the logfile (log.19:34:44-2008-02-22.txt)...
 [x] Muxing video at 23.976...   (BitStream Not Compliant)Cannot find H264 start code
Error importing test.mp4.264: BitStream Not Compliant
14382's retcode: 1
failed

```

i get this same error, anyone know a fix?

---

### Post by jexxie on 2008-03-10
Here's a version bump, added a version/auther line at the top so I can figure out what version of the script people are using.

Sadly, I don't yet know how to fix the failed to import h264 stream errors, anybody else know?

---

### Post by vik.vaughn on 2008-03-10
now that I got the normalize audio issue resolved, I'm also getting the Bitstream Not Compliant error:

```
 [x] Source filename:1080-sample.mkv
 [x] Destination filename: COMtest.mov
 [x] Video stream found, 1920 x 1040 @ 23.976, using ffh264
 [x] Audio stream found, 6 audio channels, using a52
 [x] Dumping the audio for normalizing...success
 [x] Normalizing the audio...success
 [x] Encoding the audio to low-complexity AAC...success
 [x] Extracting audio from MP4 container (silly neroAacEnc)...success
 [x] Dumping the video...success
 [x] Muxing video at 23.976...failed
 [i] Showing the last 5 lines from the logfile (log.19:35:18-2008-03-10.txt)...
 [x] Muxing video at 23.976...Cannot find H264 start code
Error importing COMtest.mov.264: BitStream Not Compliant
9680's retcode: 1
failed
 [i] Showing the last 5 lines from the logfile (log.19:35:18-2008-03-10.txt)...
```

You have no idea how awesome it will be if you can actually make this work without having to re-encode these videos at a painful 1 fps. I'm sure there are thousands of linux guys out there trying to watch HD movies on their 360's.

---

### Post by jexxie on 2008-03-10
I believe I've found a fix for this, something in how I'm extracting the video is corrupting it.

I'll post the script tomorrow after I've tested a bit.

---

### Post by jexxie on 2008-03-11
```
me@myDesktop:~/videos$ time reMuxToMP4 test.mkv
 [x] reMuxToMP4 script, v0.5.0, written by jexxie
 [x] Contact at: [http://ubuntuforums.org/member.php?u=207388](http://ubuntuforums.org/member.php?u=207388)
 [x] Source filename: test.mkv
 [x] Destination filename: test.mp4
 [x] Video stream found, 1280 x 720 @ 23.976 fps, using ffh264
 [x] Audio stream found, 6 audio channels, using a52
 [x] Muxed in mkv format
 [x] Dumping the audio...success           
 [x] Normalizing the audio...success
 [x] Encoding the audio to low-complexity AAC...success
 [x] Extracting audio from MP4 container (silly neroAacEnc)...success
 [x] Extracting the video from the mkv...success
 [x] Muxing video at 23.976 fps...success
 [x] Deleting audio and video tempfiles...success
 [o] All done!

real    8m21.845s
user    3m58.467s
sys     0m39.446s
```

Looks like it works, I haven't played this on my 360 yet, so I can't give a definitive answer yet, but it should work.

I've posted the script up on my blog:
[http://www.dufault.info/blog/2008/03/11/script-to-remux-a-mkv-h264-video-to-mp4-playable-on-an-xbox-360/](http://www.dufault.info/blog/2008/03/11/script-to-remux-a-mkv-h264-video-to-mp4-playable-on-an-xbox-360/)

---

### Post by jexxie on 2008-03-13
Checked on my xbox -- didn't work -- I need to find a way to drop the h264 profile to 4.1 instead of 5.1.  Anybody know how to edit a binary file with sed?

---

### Post by vik.vaughn on 2008-03-19
Has anyone been able to make this work?

---

### Post by jexxie on 2008-03-19
Apparently the program bbe can edit binary files, it's like sed -- I haven't figured out the syntax yet, as I've been busy with some other stuff.

I'm still workin' on this :)

---

### Post by jexxie on 2008-03-24
I'm still working on this minorly -- my 360 just died for the second time on Thursday, so I need to get it replaced via Microsoft. :(

---

### Post by vik.vaughn on 2008-03-24
Haha, how apropos. Billy must have known you were trying to use it with linux.

---

### Post by mammuth on 2008-03-25
> **jexxie said:**
> Apparently the program bbe can edit binary files, it's like sed -- I haven't figured out the syntax yet, as I've been busy with some other stuff.

I'm still workin' on this :)

All h264 videos I have checked have the level information at byte 7.

With bbe:

Replace one byte starting at byte 7 with decimal 41, input-file=vid.h264 output-file=vid.h264.new:
bbe -e "r 7 \41" --output=vid.h264.new vid.h264


To check the current 1 byte long decimal value starting at byte 7
bbe -s -b 7:1 -e "p D" vid.h264

Maybe you could use a check if the current value is larger than 41 and in that case replace it with 41.


//Mammuth

---

### Post by m3_del on 2008-03-31
That seems to work great mamuth. Thanks! It must parse through the entire stream as it does take some time. Still nice work.

---

### Post by jexxie on 2008-04-01
I'll add this into the script soon -- finally, an end all solution hopefully.

---

### Post by m3_del on 2008-04-01
We can only pray. Nice work btw

---

### Post by m3_del on 2008-04-05
Give this a go..... I am still testing this with a few files..... This should change the 33 bit to 29 instead of re-encoding.... I am sure jexxie will come out with an official release soon.
```

#!/bin/bash

# TODO:
# Need to add:
#  if video is already h264, don't encode, just copy.
#   this works now by extracting from mkv files, doesn't work if we're extractking h264 video from an avi.
#   more research needed into mencoder to copy the video stream out.

#  maybe add getopts-style script arguments? ./test inputfile -o outputfile --debug ?
#  also add debug mode where it doesn't autodelete the logfile when successful execution has completed.

VERSION="0.5.0"

X264OPTS="threads=auto"
VF="-vf harddup,spp"

log="$PWD/log.$(date +%T-%F).txt"

if [ -f "$log" ];
then
    echo " [i] Logfile already exists!\n [i] Exiting!";
    exit 1;
else
	touch "$log";
fi

cecho() {
	echo -e "${1}"
	echo -e "$1" >>"$log"
	tput sgr0;
}

ncecho () {
	echo -ne "${1}"
	echo -ne "$1" >>"$log"
	tput sgr0
}

sp="/-\|"
spinny () {
	echo -ne "\b${sp:i++%${#sp}:1}"
}

progress () {
	ncecho "  ";
	while [ /bin/true ];
	do
		kill -0 "${pid}" 2>/dev/null;
		if [ "$?" = "0" ];
		then
			spinny
			sleep 0.1
		else
			ncecho "\b\b";
			wait ${pid}
			retcode=$?
			echo ${pid}\'s retcode: ${retcode} >> "$log"
			if [ "${retcode}" = "0" ];
			then
				cecho success
			else
				cecho failed
				echo -e " [i] Showing the last 5 lines from the logfile (${log})...";
				tail -n5 "$log"
				exit 1;
			fi
			break 2;
		fi
	done
} 

cecho " [x] reMuxToMP4 script, v${VERSION}, written by jexxie\n [x] Contact at: http://ubuntuforums.org/member.php?u=207388"

if [ $# -lt 1	  ];
then
	cecho ' [i] Please supply a filename to remux to MP4, and the target filename optionally';
	exit 1;
fi

for i in mplayer normalize-audio mencoder MP4Box mkvinfo mkvextract; do
	if hash -r "$i" >/dev/null 2>&1; then
		ncecho;
	else
		cecho " [i] $i is not available.";
		DIE=1;
	fi
done

if [ $DIE ]; then
	cecho " [i] Needed programs weren't found, exiting...";
	exit 1;
fi		

SOURCE="$1"
if [ -z "$2" ];
then
	DEST="${1%.*}.mp4"
else
	DEST="$2"
fi
cecho " [x] Source filename: ${SOURCE}\n [x] Destination filename: ${DEST}";

if [ -f ${DEST} ];
then
	cecho ' [i] Destination filename already exists -- please delete and rerun the script, or select another destination';
	exit 1;
fi

identify() {
	mplayer -frames 0 -identify -ao null -vo null "$SOURCE" 2>/dev/null > /tmp/info.$$.txt
	grep ^ID_VIDEO /tmp/info.$$.txt >/dev/null && VIDEO=1
	grep ^ID_AUDIO /tmp/info.$$.txt >/dev/null && AUDIO=1

	WIDTH=$(grep ^ID_VIDEO_HEIGHT /tmp/info.$$.txt | sed 's/^ID_VIDEO_HEIGHT=//g')
	HEIGHT=$(grep ^ID_VIDEO_WIDTH /tmp/info.$$.txt | sed 's/^ID_VIDEO_WIDTH=//g')
	FPS=$(grep ^ID_VIDEO_FPS /tmp/info.$$.txt | sed 's/^ID_VIDEO_FPS=//g')
	VIDEO_CODEC=$(grep ^ID_VIDEO_CODEC /tmp/info.$$.txt | awk -F= '{print $2}')
	AUDIO_CHANNELS=$(grep ^ID_AUDIO_NCH /tmp/info.$$.txt | sort -r | head -n1 | awk -F= '{print $2}')
	AUDIO_CODEC=$(grep ^ID_AUDIO_CODEC /tmp/info.$$.txt | awk -F= '{print $2}')
	DEMUXER=$(grep ^ID_DEMUXER /tmp/info.$$.txt | awk -F= '{print $2}')
	rm -f /tmp/info.$$.txt

	if [ -z "$VIDEO" ];
	then
		cecho " [-] Missing a video stream -- please check the source file.";
		exit 1;
	else
		cecho " [x] Video stream found, $HEIGHT x $WIDTH @ $FPS fps, using $VIDEO_CODEC";
	fi

	if [ -z "$AUDIO" ];
	then
		cecho " [-] Missing a audio stream -- please check the source file.";
		exit 1;
	else
		cecho " [x] Audio stream found, $AUDIO_CHANNELS audio channels, using $AUDIO_CODEC"; 
	fi
	cecho " [x] Muxed in $DEMUXER format";
}

dumpAndReencodeAudio() {
	ncecho " [x] Dumping the audio...";
	mplayer "$SOURCE" -vo null -vc null -ao "pcm:fast:file=$DEST.wav" -channels 2 >>"$log" 2>&1 &
	pid=$!;progress $pid

	ncecho " [x] Normalizing the audio...";
	normalize-audio --peak "$DEST.wav" >>"$log" 2>&1 &
	pid=$!;progress $pid

	ncecho " [x] Encoding the audio to low-complexity AAC...";
	neroAacEnc -lc -if "$DEST.wav" -of "$DEST.m4a" >>"$log" 2>&1 &
	pid=$!;progress $pid

	rm -f "$DEST.wav"
	ncecho " [x] Extracting audio from MP4 container (silly neroAacEnc)...";
	MP4Box -raw 1 "$DEST.m4a" >>"$log" 2>&1 &
	pid=$!;progress $pid

	mv "${DEST}_track1.aac" "$DEST.aac"
	rm -f "$DEST.m4a"
	AUDIO_FILE="$DEST.aac"
}

dumpVideo() {
	if [[ $DEMUXER = "mkv" ]];
	then
		ncecho " [x] Extracting the video from the mkv...";
		TRACKNUM=$(mkvinfo "$SOURCE" | grep -B2 "Track type: video"|head -n1|awk -F": " '{print $2}')
		mkvextract tracks "$SOURCE" "$TRACKNUM":"$DEST.h264" >>"$log" 2>&1 &
	else
		ncecho " [x] Dumping the video...";
		mencoder "$SOURCE" -nosound -of rawvideo -ovc copy -o "$DEST.264" >>"$log" 2>&1 &
	fi
	pid=$!;progress $pid
	VIDEO_FILE="$DEST.h264"
	ncecho " [x] Changing the 5.1 bit to 4.1...";
	bbe -e "r 7 \41" --output="$VIDEO_FILE.new" "$VIDEO_FILE" >>"$log" 2>&1 &
	pid=$!;progress $pid
	ncecho " [x] Deleting the 5.1 video source...";
	rm -f "$VIDEO_FILE" >>"$log" 2>&1 &
	pid=$!;progress $pid
	ncecho " [x] Renaming the new video ext to .h264...";
	mv "$VIDEO_FILE.new" "$VIDEO_FILE" >>"$log" 2>&1 &
	pid=$!;progress $pid
}



reencodeVideo() {
	ncecho " [x] Encoding video to h264, first pass...";
	mencoder "${SOURCE}" -o /dev/null -nosound -of rawvideo -ovc x264 -x264encopts "$X264OPTS:turbo=2:pass=1" ${VF} -passlogfile /tmp/x264enc.$$.log  >>"$log" 2>&1 &
	pid=$!;progress $pid

	ncecho " [x] Encoding video to h264, second pass...";
	mencoder "$SOURCE" -o "$DEST.264" -nosound -of rawvideo -ovc x264 -x264encopts "$X264OPTS:turbo=2:pass=2" ${VF} -passlogfile /tmp/x264enc.$$.log >>"$log" 2>&1 &
	pid=$!;progress $pid

	VIDEO_FILE="$DEST.264"
	rm -f /tmp/x264enc.$$.log
}

mux() {
	ncecho " [x] Muxing video at $FPS fps...";
	MP4Box -new "$DEST" -add "$VIDEO_FILE" -add "$AUDIO_FILE" -fps "$FPS" -nosys >>"$log" 2>&1 &
	pid=$!;progress $pid

	ncecho " [x] Deleting audio and video tempfiles...";
	rm -f "$VIDEO_FILE" "$AUDIO_FILE" >>"$log" 2>&1 &
	pid=$!;progress $pid
}

finish() {
	cecho " [o] All done!";
}

identify;
dumpAndReencodeAudio;
if [[ $VIDEO_CODEC = "ffh264" ]];
then
	dumpVideo;
else
	reencodeVideo;
fi
mux;
finish;

rm -f "$log"

```

---

### Post by jexxie on 2008-04-06
Wow, thanks for editing the script, looks perfect =)

Probably would want the echo text being more specific, but that's me just being anal :D

Thanks m3_del!

---

### Post by jexxie on 2008-04-06
Also, can anyone confirm this is working?  My 360 is still busted, ETA 2 weeks. :mad:

---

### Post by maknapower on 2008-04-06
Sorry for my english (french user)
I have tested your last script about the debian lenny amd64.

it works perfectly , tested on my xbox360 . (file burned in a dvd )

It's good for less than 4 GB mp4 file  but for more than 4 GB's  Xbox don't want to play the file ...
The solution is to cut the mp4 in 2 parts , but with MP4Box and it's "--splits" option , only the second parts can be read :(

The right way for me is to cut directly the MKV file and apply  afterwards your script .

Another way is recompress the video to obtain a file smaller than 4GB ( a new option for the script ? :) ) 

If you have an idea about the problem with MP4Box don't hesitate to tell me.

Thanks very much to everyone for your great WORKS !!

---

### Post by m3_del on 2008-04-06
I too have the problem (4 gb files and larger)

When I manually follow my steps [HERE]("http://ubuntuforums.org/showthread.php?t=689757"), The files work just fine.

---

### Post by trusatori on 2008-04-06
I possess uber appreciation for all the work and research that has gone into getting this done.  Thanks to the work of m3_del, jexxie, and some others, I have been happily making lots of 720p mp4 files for my 360 to play.  Cheers mates!

As maknapower stated, the proper way to split a >4gb file for the 360 is to split the mkv before working with it at all.  This can be done using mkvmerge:

```
mkvmerge -o output.mkv --split 2300M input.mkv
```

This should split the movie roughly in half, assuming the file is a standard 4.4gb mkv.  You can then work with each half independently and get two playable files in the end.

Hope that helps. \m/ 8]

---

### Post by jexxie on 2008-04-07
Has that 4GB MP4Box patch been pushed upstream so it can be released?

If you manually patched the source and installed gpac, this script should still work with 4GB or larger files.

---

### Post by trusatori on 2008-04-07
> **jexxie said:**
> Has that 4GB MP4Box patch been pushed upstream so it can be released?

If you manually patched the source and installed gpac, this script should still work with 4GB or larger files.

I have the patched gpac, but the limitation is in the 360's playback capabilities.  Specifically, it won't play h264 files larger than 4gb.

[http://www.xbox.com/en-us/support/systemuse/xbox360/digitalmedia/videoplaybackfaq.htm#maxfilesize](http://www.xbox.com/en-us/support/systemuse/xbox360/digitalmedia/videoplaybackfaq.htm#maxfilesize)

---

### Post by m3_del on 2008-04-07
Well dangit....I must just be grabing files just below the limit....Sounds like there needs to be a bit more added to the script....Have it detirmine if the file size is above 4G then split into 2300M chunks and Mux all those individually

SIZE=${$(du -m $SOURCE):0:5}




if [[ $SIZE > 4400 ]]; then
	splitMKV;
fi

---

### Post by m3_del on 2008-04-07
Here is what I have 

I keep getting syntax error unexpected end of file .... Can anyone help?

```

#!/bin/bash

# TODO:
# Need to add:
#  if video is already h264, don't encode, just copy.
#   this works now by extracting from mkv files, doesn't work if we're extractking h264 video from an avi.
#   more research needed into mencoder to copy the video stream out.

#  maybe add getopts-style script arguments? ./test inputfile -o outputfile --debug ?
#  also add debug mode where it doesn't autodelete the logfile when successful execution has completed.

VERSION="0.5.0"

X264OPTS="threads=auto"
VF="-vf harddup,spp"

log="$PWD/log.$(date +%T-%F).txt"

if [ -f "$log" ];
then
    echo " [i] Logfile already exists!\n [i] Exiting!";
    exit 1;
else
	touch "$log";
fi

cecho() {
	echo -e "${1}"
	echo -e "$1" >>"$log"
	tput sgr0;
}

ncecho () {
	echo -ne "${1}"
	echo -ne "$1" >>"$log"
	tput sgr0
}

sp="/-\|"
spinny () {
	echo -ne "\b${sp:i++%${#sp}:1}"
}

progress () {
	ncecho "  ";
	while [ /bin/true ];
	do
		kill -0 "${pid}" 2>/dev/null;
		if [ "$?" = "0" ];
		then
			spinny
			sleep 0.1
		else
			ncecho "\b\b";
			wait ${pid}
			retcode=$?
			echo ${pid}\'s retcode: ${retcode} >> "$log"
			if [ "${retcode}" = "0" ];
			then
				cecho success
			else
				cecho failed
				echo -e " [i] Showing the last 5 lines from the logfile (${log})...";
				tail -n5 "$log"
				exit 1;
			fi
			break 2;
		fi
	done
} 

cecho " [x] reMuxToMP4 script, v${VERSION}, written by jexxie\n [x] Contact at: http://ubuntuforums.org/member.php?u=207388"

if [ $# -lt 1	  ];
then
	cecho ' [i] Please supply a filename to remux to MP4, and the target filename optionally';
	exit 1;
fi

for i in mplayer normalize-audio mencoder MP4Box mkvinfo mkvextract; do
	if hash -r "$i" >/dev/null 2>&1; then
		ncecho;
	else
		cecho " [i] $i is not available.";
		DIE=1;
	fi
done

if [ $DIE ]; then
	cecho " [i] Needed programs weren't found, exiting...";
	exit 1;
fi		

SOURCE="$1"
if [ -z "$2" ];
then
	DEST="${1%.*}.mp4"
else
	DEST="$2"
fi
cecho " [x] Source filename: ${SOURCE}\n [x] Destination filename: ${DEST}";

if [ -f ${DEST} ];
then
	cecho ' [i] Destination filename already exists -- please delete and rerun the script, or select another destination';
	exit 1;
fi

identify() {
	mplayer -frames 0 -identify -ao null -vo null "$SOURCE" 2>/dev/null > /tmp/info.$$.txt
	grep ^ID_VIDEO /tmp/info.$$.txt >/dev/null && VIDEO=1
	grep ^ID_AUDIO /tmp/info.$$.txt >/dev/null && AUDIO=1

	WIDTH=$(grep ^ID_VIDEO_HEIGHT /tmp/info.$$.txt | sed 's/^ID_VIDEO_HEIGHT=//g')
	HEIGHT=$(grep ^ID_VIDEO_WIDTH /tmp/info.$$.txt | sed 's/^ID_VIDEO_WIDTH=//g')
	FPS=$(grep ^ID_VIDEO_FPS /tmp/info.$$.txt | sed 's/^ID_VIDEO_FPS=//g')
	VIDEO_CODEC=$(grep ^ID_VIDEO_CODEC /tmp/info.$$.txt | awk -F= '{print $2}')
	AUDIO_CHANNELS=$(grep ^ID_AUDIO_NCH /tmp/info.$$.txt | sort -r | head -n1 | awk -F= '{print $2}')
	AUDIO_CODEC=$(grep ^ID_AUDIO_CODEC /tmp/info.$$.txt | awk -F= '{print $2}')
	DEMUXER=$(grep ^ID_DEMUXER /tmp/info.$$.txt | awk -F= '{print $2}')
	SZ=$(du -m $SOURCE)
	SIZE=${sz:0:5}
	rm -f /tmp/info.$$.txt

	if [ -z "$VIDEO" ];
	then
		cecho " [-] Missing a video stream -- please check the source file.";
		exit 1;
	else
		cecho " [x] Video stream found, $HEIGHT x $WIDTH @ $FPS fps, using $VIDEO_CODEC";
	fi

	if [ -z "$AUDIO" ];
	then
		cecho " [-] Missing a audio stream -- please check the source file.";
		exit 1;
	else
		cecho " [x] Audio stream found, $AUDIO_CHANNELS audio channels, using $AUDIO_CODEC"; 
	fi
	cecho " [x] Muxed in $DEMUXER format";
}

splitMKV() {
	ncecho " [x] Spliting the source file: $SOURCE...";
	mkvmerge -o split.$source --split 2300M $SOURCE >>"$log" 2>&1 &
	pid=$!;progress $pid
}

dumpAndReencodeAudio() {
	ncecho " [x] Dumping the audio...";
	mplayer "$1" -vo null -vc null -ao "pcm:fast:file=$DEST.wav" -channels 2 >>"$log" 2>&1 &
	pid=$!;progress $pid

	ncecho " [x] Normalizing the audio...";
	normalize-audio --peak "$DEST.wav" >>"$log" 2>&1 &
	pid=$!;progress $pid

	ncecho " [x] Encoding the audio to low-complexity AAC...";
	neroAacEnc -lc -if "$DEST.wav" -of "$DEST.m4a" >>"$log" 2>&1 &
	pid=$!;progress $pid 

	rm -f "$DEST.wav"
	ncecho " [x] Extracting audio from MP4 container (silly neroAacEnc)...";
	MP4Box -raw 1 "$DEST.m4a" >>"$log" 2>&1 &
	pid=$!;progress $pid

	mv "${DEST}_track1.aac" "$DEST.aac"
	rm -f "$DEST.m4a"
	AUDIO_FILE="$DEST.aac"
}

dumpVideo() {
	if [[ $DEMUXER = "mkv" ]];
	then
		ncecho " [x] Extracting the video from the mkv...";
		TRACKNUM=$(mkvinfo "$1" | grep -B2 "Track type: video"|head -n1|awk -F": " '{print $2}')
		mkvextract tracks "$1" "$TRACKNUM":"$DEST.h264" >>"$log" 2>&1 &
	else
		ncecho " [x] Dumping the video...";
		mencoder "$1" -nosound -of rawvideo -ovc copy -o "$DEST.264" >>"$log" 2>&1 &
	fi
	pid=$!;progress $pid
	VIDEO_FILE="$DEST.h264"
	ncecho " [x] Changing the 5.1 bit to 4.1...";
	bbe -e "r 7 \41" --output="$VIDEO_FILE.new" "$VIDEO_FILE" >>"$log" 2>&1 &
	pid=$!;progress $pid
	ncecho " [x] Deleting the 5.1 video source...";
	rm -f "$VIDEO_FILE" >>"$log" 2>&1 &
	pid=$!;progress $pid
	ncecho " [x] Renaming the new video ext to .h264...";
	mv "$VIDEO_FILE.new" "$VIDEO_FILE" >>"$log" 2>&1 &
	pid=$!;progress $pid
}



reencodeVideo() {
	ncecho " [x] Encoding video to h264, first pass...";
	mencoder "$1" -o /dev/null -nosound -of rawvideo -ovc x264 -x264encopts "$X264OPTS:turbo=2:pass=1" ${VF} -passlogfile /tmp/x264enc.$$.log  >>"$log" 2>&1 &
	pid=$!;progress $pid

	ncecho " [x] Encoding video to h264, second pass...";
	mencoder "$1" -o "$DEST.264" -nosound -of rawvideo -ovc x264 -x264encopts "$X264OPTS:turbo=2:pass=2" ${VF} -passlogfile /tmp/x264enc.$$.log >>"$log" 2>&1 &
	pid=$!;progress $pid

	VIDEO_FILE="$DEST.264"
	rm -f /tmp/x264enc.$$.log
}

mux() {
	ncecho " [x] Muxing video at $FPS fps...";
	MP4Box -new "$DEST" -add "$VIDEO_FILE" -add "$AUDIO_FILE" -fps "$FPS" -nosys >>"$log" 2>&1 &
	pid=$!;progress $pid

	ncecho " [x] Deleting audio and video tempfiles...";
	rm -f "$VIDEO_FILE" "$AUDIO_FILE" >>"$log" 2>&1 &
	pid=$!;progress $pid
}

finish() {
	cecho " [o] All done!";
}

identify;
if [[ "$SIZE" > "4096 " ]]; then
	splitMKV;
fi
for j in $( ls *.mkv ); do
dumpAndReencodeAudio $j;
if [[ $VIDEO_CODEC = "ffh264" ]];
then
	dumpVideo $j;
else
	reencodeVideo $j;
fi
done
mux;
finish;

rm -f "$log"
```

---

### Post by jexxie on 2008-04-09
I'll work on rewriting this tonight.

---

### Post by jexxie on 2008-04-11
Bah, keep getting sidetracked -- on a happier note, my Xbox is getting repaired at the service station...

I'll try to work on this over the weekend.

---

### Post by girgaz on 2008-04-11
I think where you have SIZE=${sz:0:5} it should be  SIZE=${**SZ**:0:5}

---

### Post by Mega__ on 2008-04-11
I've been following this thread for a while, thanks everyone for their contributions! I ran the script posted before on a HD file and the output would play on my computer, but not on my xbox. This was a large 4+ gig file split into smaller chunks. The smaller chunks were then passed through the script. Alas they would not play.

Currently to get HD content to play I use the following script, but it takes about the length of the video to convert. I'm running an Athlon 3700+

```
#!/bin/sh
 
INPUT=$1
OUTPUT=$2
 
mplayer "$INPUT" -ao pcm:fast:file=audio.wav -vc null -vo null
mencoder "$INPUT" \
    -ffourcc divx \
    -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=3989 \
    -audiofile audio.wav \
    -oac mp3lame -lameopts vbr=5 \
    -slang eng \
    -o "$OUTPUT"
 
rm -f audio.wav
```

Adjust the bitrate accordingly.

---

### Post by m3_del on 2008-04-13
The end result we are going for is to not have to re-encode the video but thanks for your contribution. If you split the mkv prior to the script running this works just fine...You should check it out.

---

### Post by Mega__ on 2008-04-13
I knew that was the objective...

I did in fact split my file first and then pass it through the script from this thread, and unfortunately it would not play on my xbox...

---

### Post by m3_del on 2008-04-14
That is strange. Would you be willing to try the steps manually and see if that works? 9 times out of 10 this works for me...

---

### Post by Mega__ on 2008-04-14
I'll give it a shot, I'll let you know tomorrow.

---

### Post by Nergar on 2008-04-15
I really appreciate the work is being put to this. It would be awesome to be able to watch HiDef mkvs (converted [or should i say remuxed?] to mp4) in my mighty ps3 :) 

i would help but my current knowledge in scripting is very limited right now.

---

### Post by RedNalie on 2008-04-19
Is there any update for this script?

I'm trying to remux a .mkv and when trying to play it on my XboX 360 I get the error: 69-C00D002F, and I have no idea what it means. And the main scripters haven't posted in here for a week or so. Just wondering :).

[edit]
Did some research, apparently it has something to do with the audio. I tried two .mkv samples and both give the same error

---

### Post by DSGamer on 2008-04-20
This doesn't work for me, the script "reMuxToMp4". It doesn't remux the audio. Not sure why. Any ideas? I'm getting the following output...


> 
dsgamer@ubuntu:/movies/$ reMuxToMp4 MyMovie.mkv MyMovie.mp4 --debug
 [x] reMuxToMP4 script, v0.5.0, written by jexxie
 [x] Contact at: [http://ubuntuforums.org/member.php?u=207388](http://ubuntuforums.org/member.php?u=207388)
 [x] Source filename: MyMovie.mkv
 [x] Destination filename: MyMovie.mp4
 [x] Video stream found, 1280 x 720 @ 23.976 fps, using ffh264
 [x] Audio stream found, 6 audio channels, using a52
 [x] Muxed in mkv format
 [x] Dumping the audio...success
 [x] Muxing video at 23.976 fps...failed
 [i] Showing the last 5 lines from the logfile (/movies/log.17:47:02-2008-04-20.txt)...
success
 [x] Muxing video at 23.976 fps...  Unknown input file type
Error importing : Bad Parameter
30161's retcode: 1
failed




---

### Post by The Fold on 2008-04-21
I've just come across this thread as I've recently converted to Ubuntu and was looking for a way to convert some MKV files to a format my 360 will play as previously I was using Encode360.

Which is the current **working** version of the script as taking from [this]("http://ubuntuforums.org/showpost.php?p=4674963&postcount=55") post from m3_del am I to believe that it does not work? I would try it out but currently I'm at work so I can't try it out until this evening :(

---

### Post by The Fold on 2008-04-21
Ok, so I've tried the script and it converted a video ok (after gathering all the necessary apps to do so, if possible it may be an idea to update the OP with details on all of them).

It doesn't play on my 360 though :(

Also, it didn't pull out and re-mux the subtitles, but then this isn't something that's needed everytime so I'm just working that part out now :)

---

### Post by RedNalie on 2008-04-22
Did you get an error code from your XboX? Is it the same as mine or do you get a different one?

---

### Post by The Fold on 2008-04-22
I didn't get any error code, the file just showed with a red 'no-entry-computer-says-no' symbol.

---

### Post by RedNalie on 2008-04-22
Maybe you could post your logfile to we can see what happens, since it should be able to play but give you an error. 

In order to do that you have to change the final line of the script, or rather remove it, since that deletes the generated logfile :).
--
I'll see if I can examine my b0rking file in a few days, see if I can find compatibility issues. It would be nice though, if the creators of the script would help us.

---

### Post by The Fold on 2008-04-23
I've attached the log from a video I just tried to convert as a test. I've made no alterations to the script so this shouldn't work. If you think it should then let me know as it may be a problem with ushare?

---

### Post by RedNalie on 2008-04-23
Found your problem then ;)

The XboX 360 doesn't stream .mp4's via uShare or anything like it, it just won't (the computer-says-no sign). When you rename it to .mov however, it should work (no computer-says-no sign).

You will probably encouter an error like mine though, and I want to know if you get the same one. I tested it via a usb-harddrive (then the XboX 360 will play .mp4).

---

### Post by The Fold on 2008-04-23
Ah I see!! Strange that it won't play MP4 when that's a pretty common format these days :confused:

I'll try the renaming method when I get home and let you know the outcome! :)

---

### Post by The Fold on 2008-04-23
Ok, so I renamed my file from .mp4 to .mov and ran it through ushare to my 360.

It plays fine :)

---

### Post by RedNalie on 2008-04-24
> **The Fold said:**
> Ok, so I renamed my file from .mp4 to .mov and ran it through ushare to my 360.

It plays fine :)

Strange, I'll try it with my movies this afternoon when I get home from work :)

---

### Post by jexxie on 2008-04-24
Arg, been too busy with life lately.

I'll get an autosplitting version of this out within a week.

Cheers all.

---

### Post by magickangaroo on 2008-04-24
> **trusatori said:**
> I possess uber appreciation for all the work and research that has gone into getting this done.  Thanks to the work of m3_del, jexxie, and some others, I have been happily making lots of 720p mp4 files for my 360 to play.  Cheers mates!

As maknapower stated, the proper way to split a >4gb file for the 360 is to split the mkv before working with it at all.  This can be done using mkvmerge:

```
mkvmerge -o output.mkv --split 2300M input.mkv
```

This should split the movie roughly in half, assuming the file is a standard 4.4gb mkv.  You can then work with each half independently and get two playable files in the end.

Hope that helps. \m/ 8]

Hi

As far as i can tell streaming files through fuppes wont require splitting. Can anyone else confirm this?

Cheers

/Mgk

---

### Post by magickangaroo on 2008-04-24
> **The Fold said:**
> Ah I see!! Strange that it won't play MP4 when that's a pretty common format these days :confused:

I'll try the renaming method when I get home and let you know the outcome! :)

Hi

I know for sure that the 360 plays mp4s.  What i think is happening here is the mp4 isnt representing itself correctly or maybe that the the xbox cant identify it as the mp4.  The xbox 360 seems to work mostly off of file extensions to identify a file type.

Anyone know if this is the case?

/Mgk

---

### Post by RedNalie on 2008-04-27
> **magickangaroo said:**
> Hi

As far as i can tell streaming files through fuppes wont require splitting. Can anyone else confirm this?

Cheers

/Mgk

It won't need splitting. The only reason why you need to split is for files on a harddisk (Fat32), but the XboX 360 does support HFS+ (Used by Apple for iPods) which doesn't have the 4,5GB limit.

---

### Post by RedNalie on 2008-04-27
> **m3_del said:**
> Give this a go..... I am still testing this with a few files..... This should change the 33 bit to 29 instead of re-encoding.... I am sure jexxie will come out with an official release soon.
[code]
#!/bin/bash

# TODO:
# Need to add:
#  if video is already h264, don't encode, just copy.
CUT SHORT :P


Ok, I did some testing with this script, for some magical reason it appears to work now (w00t w00t). Just a minor glitch:

The 'Changing the 5.1 bit to 4.1...success' is not always true, I'm seeing the same glitches I see when watching a 5.1 movie. I tested 5 samples (not knowing if one is 5.1) and one movie had the glitches. 

It could be that the others were 5.1 as well, but I'm not sure how I can check this :)

---

### Post by RedNalie on 2008-04-28
ok, did a large sample (10GB) and apparently you do need to split it. Even on a HFS+ formatted harddrive. :(

---

### Post by trusatori on 2008-04-28
Just some info for those of you as into watching hd on your 360 as I now am ;]...

1) The 360 requires that .mp4 files remain under 4gb (see [http://www.xbox.com/en-us/support/systemuse/xbox360/digitalmedia/videoplaybackfaq.htm#maxfilesize](http://www.xbox.com/en-us/support/systemuse/xbox360/digitalmedia/videoplaybackfaq.htm#maxfilesize)).

2) Ushare: First of all, ushare has .mp4 registered as an audio format.  This can be changed by compiling your own binary after messing around with mime types.  If you prefer a far more simple work-around, simply rename your .mp4 as .m4v (others say .mov also works).  However, even once you have your files properly split and with the proper extension for ushare, you'll notice that your files will stop playing with an error once you get to about the 2gb mark.  This seems to be an issue with ushare itself, as using fuppes instead streams the files just fine (although they still have to be less than 4gb as again this is a 360 limitation).

A deb for a relatively recent version of fuppes can be found here: [http://ppa.launchpad.net/james-lee/ubuntu/pool/main/f/fuppes/fuppes_0+svn578-0ubuntu1~gutsy7_i386.deb](http://ppa.launchpad.net/james-lee/ubuntu/pool/main/f/fuppes/fuppes_0+svn578-0ubuntu1~gutsy7_i386.deb)

Once you have it installed, you will need a valid fuppes.cfg and vfolder.cfg (it's just a smidge more complicated than ushare).  Mine are attached and should give you a good start.  The vfolder.cfg should not have to be touched, just enter your shared directories in fuppes.cfg and put both files in ".fuppes/" in your home directory.  Type "fuppes" to get it running then "r <enter>" (this is actually a prompt).  Once your database is created, type "v <enter>".  Once your virtual container is created, your xbox should be able to see the files and stream them fine.

This setup has really been working well for me, hope that helps some of you ;].

---

### Post by The Fold on 2008-04-30
Doesn't fuppes transcode the video much like TVersity does?

---

### Post by trusatori on 2008-04-30
> **The Fold said:**
> Doesn't fuppes transcode the video much like TVersity does?

You can set it up to do so if that sort of thing interests you.  I'm simply using it as a non-2gb+ crashing replacement for ushare.

---

### Post by jexxie on 2008-04-30
Heh, still too busy to look at this, I have this working, but I don't like the code yet.

Give me a bit of time to purdy it up and I'll release.

p.s. I think this is my first 'contribution', so it's great to see people wanting/using it. Thanks all!

---

### Post by Nergar on 2008-04-30
> **jexxie said:**
> Heh, still too busy to look at this, I have this working, but I don't like the code yet.

Give me a bit of time to purdy it up and I'll release.

p.s. I think this is my first 'contribution', so it's great to see people wanting/using it. Thanks all!

Congrats!!
It made my life a lil better!!!

I'll begin testing it tomorrow with my PS3

---

### Post by obi22 on 2008-05-04
> **jexxie said:**
> I think this is my first 'contribution', so it's great to see people wanting/using it. Thanks all!

Yes, we want it! In a meantime v0.5.0 is superb, thanks to You and M3.

---

### Post by m3_del on 2008-05-04
> **obi22 said:**
> Yes, we want it! In a meantime v0.5.0 is superb, thanks to You and M3.

All praise goes to jexxie here....

---

### Post by invigorated on 2008-05-05
I'm new somewhat new to Ubuntu and I'm having a couple of problems with the script. 

I'm getting an error:
 [-] Missing a video stream -- please check the source file.

Am I missing some codecs or something necessary to discovery the video steam?

---

### Post by jexxie on 2008-05-05
> **invigorated said:**
> 
Am I missing some codecs or something necessary to discovery the video steam?
No, you're probably not supplying a video file.  Run file on the movie file and let us know what it says:
```
file filename.avi
```

Also, run this on the file and post what it says:
```
mplayer -frames 0 -identify -ao null -vo null 2>/dev/null filename.avi
```

---

### Post by invigorated on 2008-05-05
I managed to sort it out, after installing some codec updates to mplayer and rebooting it worked fine. Could have been the restarted after mass changes/installs/updates that fixed it, could have been the codecs. 

Now I get further through the script before getting an error:

```
 [x] Extracting audio from MP4 container (silly neroAacEnc)...success
 [x] Extracting the video from the mkv...success
 [x] Changing the 5.1 bit to 4.1...failed
 [i] Showing the last 5 lines from the logfile (/home/matt/Videos/log.22:00:40-2008-05-05.txt)...
10764's retcode: 0
success
 [x] Changing the 5.1 bit to 4.1...  ./covertToMP4.txt: line 177: bbe: command not found
11295's retcode: 127
failed
```

---

### Post by invigorated on 2008-05-05
Ok all sorted and working!

Thanks for the great work guys!

---

### Post by jexxie on 2008-05-05
I'll add a check for the bbe application on the next release, forgot to add it, my bad. :)

---

### Post by Nergar on 2008-05-06
> **jexxie said:**
> I'll add a check for the bbe application on the next release, forgot to add it, my bad. :)

OK, I think we should start cleaning this. I will help with everything I can. Here are a few things i think are missing:

1. Add a bbe check.
2. Suggest installing mkvtoolnix and gpac instead of the tools that come with them.
3. name an official beta or alpha release and work form there.
4. add neroAacEnc as a dependency and link to it (can't get it form repositories).
5. Clean the code.

Jexxie, I suggest you post the code so we can help.

---

### Post by jexxie on 2008-05-06
> **Nergar said:**
> OK, I think we should start cleaning this. I will help with everything I can. Here are a few things i think are missing:

1. Add a bbe check.
2. Suggest installing mkvtoolnix and gpac instead of the tools that come with them.
3. name an official beta or alpha release and work form there.
4. add neroAacEnc as a dependency and link to it (can't get it form repositories).
5. Clean the code.

Jexxie, I suggest you post the code so we can help.
1. Done
2. Why?
3. Why?
4. Done, produce the link and this'll be done.
5. What needs to be cleaned?  Pretty tidy to me.

I'll try to upload it maybe tonight, need to install Ubuntu and other required apps.

---

### Post by Mega__ on 2008-05-07
Fantastic script! Thanks again!

Once I read the post about renaming the file to a .m4v, everything worked great. Great work!

---

### Post by Nergar on 2008-05-07
> **jexxie said:**
> 1. Done
2. Why?
3. Why?
4. Done, produce the link and this'll be done.
5. What needs to be cleaned?  Pretty tidy to me.

I'll try to upload it maybe tonight, need to install Ubuntu and other required apps.

1. Thanks.
2. Because that's the name of the packages in the repos.
3. I ment post it in the first thread post so people doesn't need to read the entire thread to find it.
4. [http://www.nero.com/enu/nero-aac-codec.html](http://www.nero.com/enu/nero-aac-codec.html)
5. > **jexxie said:**
> Heh, still too busy to look at this, I have this working, but I don't like the code yet.

Give me a bit of time to **purdy** it up and I'll release.

I guess I don't know the meaning of purdy :]

---

### Post by jexxie on 2008-05-07
Ah, I don't like my code at this point, so it needs tidying. :)

As for the links to what's needed, once this works we can create a new thread.

---

### Post by Nergar on 2008-05-09
I've tried lots of things but can't get it to work.
All I get is a:
```
[x] Muxing video at 23.976...  Cannot find H264 start code
Error importing halcyon-1000corpses.720p-sample.mp4.264: BitStream Not Compliant
16480's retcode: 1
failed

```

I get the same error with every video I try.

---

### Post by jexxie on 2008-05-10
> **Nergar said:**
> 
I get the same error with every video I try.

Try using the latest version. ;)

---

### Post by magickangaroo on 2008-05-10
> **jexxie said:**
> Try using the latest version. ;)

Heya

Is that version 0.5.0?

Since upgrading to hardy i have had problems with the script.  

Below is the terminal output

 [x] reMuxToMP4 script, v0.5.0, written by jexxie
 [x] Contact at: [http://ubuntuforums.org/member.php?u=207388](http://ubuntuforums.org/member.php?u=207388)
 [x] Source filename: Serafalls.mkv
 [x] Destination filename: Serafalls.mp4
 [x] Video stream found, 1280 x 528 @ 23.976 fps, using ffh264
 [x] Audio stream found, 6 audio channels, using dts
 [x] Muxed in mkv format
 [x] Dumping the audio...success
 [x] Normalizing the audio...success
 [x] Encoding the audio to low-complexity AAC...success
 [x] Extracting audio from MP4 container (silly neroAacEnc)... \./m3_Del: line 44: 14908 Aborted                 MP4Box -raw 1 "$DEST.m4a" >> "$log" 2>&1
failed
 [i] Showing the last 5 lines from the logfile (/home/adz/Desktop/mounts/entry/output/convert/test/log.11:00:03-2008-05-10.txt)...
8394's retcode: 0
success
 [x] Extracting audio from MP4 container (silly neroAacEnc)...  Extracting MPEG-4 AAC
14908's retcode: 134
failed

Log attached and trimmed.
 
it seems to me and i could be wrong that theres a problem with MP4Box.  so this is the version i have installed.

MP4Box -version
MP4Box - GPAC version 0.4.5-DEV (build 21)
GPAC Copyright: (c) Jean Le Feuvre 2000-2005
                (c) ENST 2005-200X



Can anyone help with this?




Thanks

/mgk

---

### Post by magickangaroo on 2008-05-10
hmm since looking at it i guess theyre could be an issue with the install mp4box version so i have removed that and installed the one from gpac packaged.  will rerun the script and let you know how it goes
===update===

ok unfortunately i still get an error at the same point.

===update part deux===

ok this maybe some permision issue on my pc, i have rerun the script as root and am currently getting past the point of failure from before.  Will update if it completes ok

cheers

====update===

yep was a permisions issue, not sure on what thou or why the hardy upgrade would have changed permisions on anything?

---

### Post by Nergar on 2008-05-11
I have the latest version. 

does the 360 plays vob files? I just found an ap for windows that does almost the same but it uses vob as container. I tested the output file in my ps3 and it plays perfectly, h264 + ac3 6 channels!!!

Maybe the script could also do this.

Edit:

Latest version of what? gpac or script? I have gpac ver 0.4.4 and where's the latest version of the script, i just lost track.

---

### Post by jexxie on 2008-05-12
> **Nergar said:**
> 
Maybe the script could also do this.


The 360 can't play vob files, no.  And yes, v0.5 is the latest version of my script.

---

### Post by RedNalie on 2008-05-22
> **jexxie said:**
> The 360 can't play vob files, no.  And yes, v0.5 is the latest version of my script.

Jexxie, how's the update coming :)

---

### Post by jexxie on 2008-06-16
I don't think I'm going to release an update for this, I built a htpc a month or two ago, and haven't used my 360 for video playback since.

For people wanting the latest version of my script, it's available at my blog here (I ended up revamping the blog):
[http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/](http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/)

If anybody wants to add that functionality in, feel free.  I've GPL'd the code, please email me the updated script so I can post it.

Cheers

---

### Post by jcr1 on 2008-07-07
Hi wondering if you could help...?

I am trying to run this script...it spends a long time dumping the audio but then from there on get this error:

```
[x] Dumping the audio...success
 [x] Normalizing the audio...success
 [x] Encoding the audio to low-complexity AAC...failed
 [i] Showing the last 5 lines from the logfile (/path/to/files/log.15:25:58-2008-07-07.txt)...                                                                            23788's retcode: 0
success
 [x] Encoding the audio to low-complexity AAC...  /home/serveradmin/bin/remuxtomp4.sh: line 157: neroAacEnc: command not found                                30519's retcode: 127
failed

```

Any ideas? Not sure what this neroaacenc is or how to get it.

Cheers for all the work on this, I hope i can get it to work.

---

### Post by jexxie on 2008-07-07
What version of the script are you running?

You need to install the neroaac program, here's the link to it (please  try reading the thread):
[http://www.nero.com/enu/nero-aac-codec.html](http://www.nero.com/enu/nero-aac-codec.html)

The newer version of the script should detect if you don't have it installed, and fail gracefully, so you're probably running an older script.

---

### Post by jcr1 on 2008-07-08
Hi, thanks for the reply, must have missed that bit, as I thought I had read through it all.

I am running the version from your blog page in post #107. It did work well at telling me what packages I had missing, but it didn't call this nero one up until after it had spent time dumping the audio. Plus the packages it did call up at the beginning took me a while to find out what I actually needed to get (i.e. some packages come within a another) but that could be just my inexperience.

I shall get that nero package installed and run it again. 

Thanks for your help! Hope this works... have been trying all sorts to get an mkv to work on my xbox... ffmpeg, mencoder...varying results...none of which worked lol.

---

### Post by jexxie on 2008-07-08
Hi Jon,

Please make sure you have the latest script available here as well:
[http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/](http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/)

---

### Post by jcr1 on 2008-07-09
Yup thats the one I got...dependant on whether you updated it in the last 3 days.

---

### Post by jcr1 on 2008-07-09
What do I do with the nero thing I downloaded? There are two files in the 'linux' folder within that I assume I need to use...but what do I do with them?

---

### Post by roadmouse on 2008-07-09
Just copy them to the /usr/bin/ folder on your computer.

Open a new Terminal window and cd to the NeroDigitalAudio/linux/ folder.
Then type:

sudo cp neroAacDec /usr/bin/
sudo cp neroAacEnc /usr/bin/

That should work :)

---

### Post by jcr1 on 2008-07-09
Hey Success! 

Well as far as the script ranand finished with no errors! Just need to get home now and test the actual mp4 it has created!

This is great!

---

### Post by jcr1 on 2008-07-09
OK...now I am home and when I go to Media > Videos on my xbox360, this newly created mp4 does not appear in my list of videos. 

Any ideas why? (yes it is in the right place, yes I am using twonkymedia...all other vids in the same directory (that are compatible) show up on the xbox) its as if this is not compatible and therefore not showing up on the xbox.

Plays fines on my laptop.

---

### Post by jcr1 on 2008-07-09
Does this script work with avi's?

I have an avi, that shows up on my xbox, but will not play..says wrong codecs. So I thought I would run it through this script...but it cannot deal with the video:

```
] Encoding video to h264, first pass...failed
 [i] Showing the last 5 lines from the logfile (/home/path/to/log.19:43:04-2008-07-09.txt
FATAL: Cannot initialize video driver.

Exiting...                                                                    25459's retcode: 1
failed

```

Any ideas?

---

### Post by roadmouse on 2008-07-10
I have no experience with twonkymedia. I use uShare and Fuppes without any problems.
If twonkymedia only sees your avi-files, and not the mp4, try renaming the extension of the mp4 to .avi
That might work.

If your other avi-files don't play, are you sure you've got the right updates installed on your xbox? Did it ever play avi files before?

---

### Post by jcr1 on 2008-07-10
yeah it plays other avi's ok... seems certain ones it doesn't like. 

Will try renaming the mp4 to avi (didn't know you could simply do that)

---

### Post by donkeyX on 2008-07-14
Hey guys, I have spent a fair bit of time trying to get some avi's to play on the 360 so i thought i would post the link to my forum with the description on what i ended up doing. This may not be the best method, but it did work for me and seems pretty easy. I am also happy for anyone to suggest an alternative that is better, but for the moment working seems great ;) . 

[http://edens-gate.com/blog/2008/07/13/convert-video-for-xbox-360/]("http://edens-gate.com/blog/2008/07/13/convert-video-for-xbox-360/")

Hope this helps and saves some of the pain i had

PS: you  might be able to mod my command to get it to work in the format you are after, if wmv is no good for you?

Cheers Dave

---

### Post by jcr1 on 2008-07-14
> **donkeyX said:**
> Hey guys, I have spent a fair bit of time trying to get some avi's to play on the 360 so i thought i would post the link to my forum with the description on what i ended up doing. This may not be the best method, but it did work for me and seems pretty easy. I am also happy for anyone to suggest an alternative that is better, but for the moment working seems great ;) . 

[http://edens-gate.com/blog/2008/07/13/convert-video-for-xbox-360/]("http://edens-gate.com/blog/2008/07/13/convert-video-for-xbox-360/")

Hope this helps and saves some of the pain i had

PS: you  might be able to mod my command to get it to work in the format you are after, if wmv is no good for you?

Cheers Dave


Interesting...I am giving it a go...trying to find something that works for me too.

---

### Post by jexxie on 2008-07-14
I hate the wmv format, I refuse to use it.  At least Microsoft's avi format is open, wmv isn't.

---

### Post by donkeyX on 2008-07-14
Thats cool, and you have every right to hate it but like I said: I was sick of it not working and was happy to use whatever to actually get it working. If you know of the correct command for containers etc then i would be happy to hear it? I did have a go at using :

A: The Xbox 360 console supports the following for AVI:

    * File extensions: .avi, .divx
    * Containers: AVI
    * Video profiles: MPEG-4 Part 2 (Simple Profile and Advanced Simple Profile)
    * Video bit rate: 5 Mbps with resolutions of 1280 × 720 at 30 fps. See the question about max bit rate, resolution, and frames per second.
    * Audio profiles: Dolby® Digital (2 channel and 5.1 channel), MP3
    * Audio max bit rate: No restrictions. See the question about max bit rate, resolution, and frames per second. 


but no luck with that ;)

Cheers Dave

---

### Post by jcr1 on 2008-07-15
Well your method worked, donkeyx, but gave a poor image quality. Very blocky and pixelated. Any idea why? How can I tell it to keep the same image quality as the original source?

---

### Post by roadmouse on 2008-07-15
Same here. It works, but quality is very poor.

I would like to use this as an alternative for my HD mkv-files that won't work with the reMuxToMP4 script from jexxie.

---

### Post by donkeyX on 2008-07-15
You could try this one, I have not tested just had a read of the doc and they sound alright ;) . 

mencoder "BBC-Planets_8.avi" -o "BBC-Planets_9_test.wmv" -of lavf -lavfopts format=asf -ovc lavc -lavcopts vcodec=wmv2:vbitrate=1000:vhq:turbo:vpass=1 -oac lavc -lavcopts acodec=wmav2


There was also a post processing option for quality that might help as well.

Let me know how that goes.

cheers Dave

---

### Post by jexxie on 2008-07-15
The point of my script is to remux (note, remux) a hidef mkv file into something playable on the Xbox.  Re encoding the movie is really quite tedious, the script just copies the video stream and encodes the audio into a compatible format.

If you're looking better, I remember the Linux program avidemux being awesome, you just want mpg4 video, and mp3 audio in an avi wrapper -- that should play fine on your 360, and shouldn't be blocky or pixelated.

---

### Post by jcr1 on 2008-07-16
> **jexxie said:**
> The point of my script is to remux (note, remux) a hidef mkv file into something playable on the Xbox.  Re encoding the movie is really quite tedious, the script just copies the video stream and encodes the audio into a compatible format.

If you're looking better, I remember the Linux program avidemux being awesome, you just want mpg4 video, and mp3 audio in an avi wrapper -- that should play fine on your 360, and shouldn't be blocky or pixelated.


I couldn't get videos to work with your script. Will try again though. 

Been using ffmpeg a lot to do this too, but nothing seems to be right to keep the xbox happy. 

I have been trying to utilise the H.264 stream (no re-encoding) with a AAC 2 channel audio stream, but it just doesn't show up on my xbox...

Will press on.

---

### Post by jexxie on 2008-07-17
Let me know the error message (or give me the log) and I'll take a peek.

---

### Post by rsambuca on 2008-07-17
Just a heads-up that the Avidemux avi's will not play on the XBox.  They are not sure why yet, but if you go to the Avidemux forums, they are aware of the issue.

---

### Post by donkeyX on 2008-07-18
Hey Again guys,

I will see if i get time this weekend to do some more testing with avi, but like i said earlier i did try a lot of options without success including Avidmux using all the xbox formats. I would much prefer avi and better quality but will keep using wmv until i see a working solution, which i have yet to see for anything other than the command i posted. 

Cheers Dave

---

### Post by jcr1 on 2008-07-18
> **jexxie said:**
> Let me know the error message (or give me the log) and I'll take a peek.

Trouble is, there is no error. It creates the MP4 as if everything is fine, but they won't play on my XBOX...they don't even show up.

...hope this isn't an issue with my xbox. DIVX avi's show up, so I assume that means I have the patch? How do I know if I have the patch??

---

### Post by jcr1 on 2008-07-18
OK here's the current deal. 

Seems twonkymedia has something to do with mp4s not showing up in the list of videos to play. 

I created an mp4 using jexxie's script and put it on a USB stick and the xbox found it!! hurrah!

BUT....audio, NO VIDEO. just a black screen, but with audio playing.

I am close to giving up...I can get low quality divx avi;s to play, and I am sure the low quality will be fixed with a certain parameter in ffmpeg, but this is kind of defeated the point that the h.264 shouldn't need to be changed...it is meant to be supported.

---

### Post by xsnoopyx on 2008-07-20
I know everyone here hates Windows, but I highly recommend GotSent.
It basically does everything and even splits if > 4gb.

Try it out if you're dualbooting. Pretty fast at remuxing. It's worked on every 720p MKV i have. Its basically a GUI for a whole bunch of scripts like MP4Box which i saw earlier in this thread.

---

### Post by roadmouse on 2008-07-21
GotSent works fine under wine also. I use it from time to time, but it's much slower than jexxie's script.

---

### Post by jexxie on 2008-07-22
> **jcr1 said:**
> 
I am close to giving up...I can get low quality divx avi;s to play, and I am sure the low quality will be fixed with a certain parameter in ffmpeg, but this is kind of defeated the point that the h.264 shouldn't need to be changed...it is meant to be supported.

I can't help you if you don't post more information.  Run midentify and post the logfile from running my remux script, complete with version info please.

Cheers.

---

### Post by jexxie on 2008-07-22
> **xsnoopyx said:**
> 
It basically does everything and even splits if > 4gb.


If you're looking for something to split an mkv, just use mkvsplit.

---

