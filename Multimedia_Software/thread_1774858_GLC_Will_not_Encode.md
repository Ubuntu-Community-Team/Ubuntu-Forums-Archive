---
title: "GLC Will not Encode"
date: 2011-06-03
forum: Multimedia Software
---

### Post by Joseph Schwenker on 2011-06-03
I'm trying to encode a video I made in GLC, and... well, jeez.
There's so little documentation for GLC that it's nearly impossible to get it working. I just tried encoding a file I made using the script provided, and got this output:

```
joseph@joseph:~/Desktop$ sh encode.sh lugaru-17880-0.glc 
[: 103: lugaru-17880-0.glc: unexpected operator
[  97.80s       file error ] unexpected EOF
Warning: unsupported audio format
[: 167: yes: unexpected operator
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
Option x264encopts: Bad argument b_pyramid=(null)
Option x264encopts: Unknown suboption bime
Option x264encopts: turbo option is deprecated; use slow_firstpass to disable turbo
Reading from stdin...
success: format: 0  data: 0x0 - 0x0
YUV4MPEG2 file format detected.
YUV4MPEG2 Video stream 0 size: display: 1680x1050, codec: 1680x1050
VIDEO:  [YV12]  1680x1050  12bpp  30.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:12  fourcc:0x32315659  size:1680x1050  fps:30.000  ftime:=0.0333
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B-frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit.
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is undefined - no prescaling applied.
[swscaler @ 0xa2d79a0]using unscaled yuv420p -> yuv420p special converter
FATAL: Cannot initialize video driver.
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffrawyv12] vfm: ffmpeg (RAW YV12)
==========================================================================
Movie-Aspect is undefined - no prescaling applied.
FATAL: Cannot initialize video driver.

Exiting...
MEncoder 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
Option x264encopts: Bad argument b_pyramid=(null)
Option x264encopts: Unknown suboption bime
Option x264encopts: turbo option is deprecated; use slow_firstpass to disable turbo
Reading from stdin...
success: format: 0  data: 0x0 - 0x0
File not found: 'audio.mp3.tmp'
Failed to open audio.mp3.tmp.
Cannot open audio stream: audio.mp3.tmp
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...

```

Can anyone help me figure out GLC? I'm sure that this would help me along with a ton of other people who want to do Let's Play videos and whatnot on Linux.

---

### Post by andrew.46 on 2011-06-04
I could not find a copy of that encoding script as nullkey.ath.cx seems to be offline at the moment. Could you post the actual script here? What would be nice would be for you to also post one of your game captures somewhere in glc format although I appreciate that these files are mostly pretty big. Its just that if MEncoder and lame can do it FFmpeg should be able to do it better....

**Edit:** I note some examples here using FFmpeg:

Record an OpenGL game in Linux using GLC
[http://qubodup.wordpress.com/2010/06/02/record-an-opengl-game-in-linux-using-glc/](http://qubodup.wordpress.com/2010/06/02/record-an-opengl-game-in-linux-using-glc/)

---

### Post by Joseph Schwenker on 2011-06-04
Here's the script, taken from [here]("https://github.com/nullkey/glc/blob/master/scripts/encode.sh").

```
!/bin/bash
#
# encode.sh -- encoding glc stream to x264-encoded video
# Copyright (C) 2007-2008 Pyry Haulos
# For conditions of distribution and use, see copyright notice in glc.h

FILE=""
QUALITY=""

AUDIO="1"
VIDEO="1"

BITRATE="2000"
QP="20"
CRF="18"

METHOD="qp"

OUTFMT="mp4"
OUT="video.${OUTFMT}"

PASSLOG="pass.log"
AUDIOTMP="audio.mp3.tmp"

MULTIPASS="no"
ADDOPTS=""

showhelp () {
	echo "$0 [option]... [glc stream file]"
	echo "  -o, --out=FILE       write video to FILE"
	echo "                        default is ${OUT}"
	echo "  -v, --video=NUM      video stream number"
	echo "                        default is ${VIDEO}"
	echo "  -a, --audio=NUM      audio stream number"
	echo "                        default is ${AUDIO}"
	echo "  -m, --method=METHOD  bitrate calculation method"
	echo "                        supported methods are bitrate, qp, crf"
	echo "                        default method is ${METHOD}"
	echo "  -q, --quality=VAL    quality parameter"
	echo "  -f, --outfmt=FORMAT  output container format"
	echo "                        default is ${OUTFMT}"
	echo "  -x, --addopts=OPTS   additional options to mencoder"
	echo "  -h, --help           show this help"
}

OPT_TMP=`getopt -o o:v:a:m:q:f:x:h -l out:,video:,audio:,method:,quality:,outfmt:,addopts: \
	-n "$0" -- "$@"`
if [ $? != 0 ]; then showhelp; exit 1; fi

eval set -- "$OPT_TMP"

while true; do
	case "$1" in
		-o|--out)
			OUT="$2"
			shift 2
			;;
		-v|--video)
			VIDEO="$2"
			shift 2
			;;
		-a|--audio)
			AUDIO="$2"
			shift 2
			;;
		-m|--method)
			METHOD="$2"
			shift 2
			;;
		-q|--quality)
			QUALITY="$2"
			shift 2
			;;
		-f|--outfmt)
			OUTFMT="$2"
			shift 2
			;;
		-x|--addopts)
			ADDOPTS="$2"
			shift 2
			;;
		-h|--help)
			showhelp
			exit 0
			shift 2
			;;
		--)
			shift
			break
			;;
		*)
			echo "Unrecognized option: $1"
			showhelp
			exit 1
			;;
	esac
done

for arg do FILE=$arg; done
if [ "$FILE" == "" ]; then
	showhelp
	exit 1
fi

KEYINT=300

X264_OPTS="ref=4:mixed_refs:bframes=3:b_pyramid:bime:weightb:direct_pred=auto:filter=-1,0:partitions=all:turbo=1:threads=auto:keyint=${KEYINT}"
LAME_OPTS="q=4" # TODO configure q, cbr or abr

case ${METHOD} in
	crf)
		[ "$QUALITY" != "" ] && CRF=$QUALITY
		X264_OPTS="crf=${CRF}:${X264_OPTS}"
		MULTIPASS="no"
		;;
	bitrate)
		[ "$QUALITY" != "" ] && BITRATE=$QUALITY
		X264_OPTS="bitrate=${BITRATE}:${X264_OPTS}"
		MULTIPASS="yes"
		;;
	qp)
		[ "$QUALITY" != "" ] && QP=$QUALITY
		X264_OPTS="qp=${QP}:${X264_OPTS}"
		MULTIPASS="yes"
		;;
	*)
		showhelp
		exit 1
		;;
esac

[ "$OUTFMT" != "avi" ] && OUTFMT="lavf -lavfopts format=${OUTFMT}"

glc-play "${FILE}" -o - -a "${AUDIO}" | lame -hV2 - "${AUDIOTMP}"

if [ "${MULTIPASS}" == "no" ]; then
	glc-play "${FILE}" -o - -y "${VIDEO}" | \
		mencoder - \
			-audiofile "${AUDIOTMP}"\
			-demuxer y4m \
			-ovc x264 \
			-x264encopts "${X264_OPTS}" \
			-of ${OUTFMT} \
			${ADDOPTS} \
			-o "${OUT}"
else
	glc-play "${FILE}" -o - -y "${VIDEO}" | \
		mencoder - \
			-nosound \
			-demuxer y4m \
			-ovc x264 \
			-x264encopts "${X264_OPTS}:pass=1" \
			-passlogfile "${PASSLOG}" \
			-of ${OUTFMT} \
			${ADDOPTS} \
			-o "${OUT}"
	glc-play "${FILE}" -o - -y "${VIDEO}" | \
		mencoder - \
			-audiofile "${AUDIOTMP}" \
			-demuxer y4m \
			-ovc x264 \
			-x264encopts "${X264_OPTS}:pass=2" \
			-passlogfile "${PASSLOG}" \
			-oac copy \
			-of ${OUTFMT} \
			${ADDOPTS} \
			-o "${OUT}"
fi

rm -f "${PASSLOG}" "${AUDIOTMP}"
```

The file I'm trying to encode is around 800 MB, and my ISP is rather crappy, sadly. I'm not sure if it recorded sound, either. I told it to, but you know how PulseAudio and ALSA jam together.

---

### Post by Joseph Schwenker on 2011-06-04
With the help of the guy who made [this video]("http://www.youtube.com/all_comments?v=bD1z3HysURQ"), I was able to encode at least the video feed of my recording to an avi file using this command:

```
glc-play lugaru-11055-0.glc -y 1 -o - | ffmpeg -i - -sameq test3.avi
```

Unfortunately, audio still does not work, so I have to manually synchronize outRec's audio feed with glc's video feed once they're both encoded. This is best done in PiTiVi, where the audio's waveform is rendered in visual form, making it easy to cue up with the video.

---

### Post by Joseph Schwenker on 2011-06-04
[Here's the final video.]("http://www.youtube.com/watch?v=bBTMVCcWq5Y")

---

### Post by andrew.46 on 2011-06-05
Perhaps you could alter the script a little to work with a later MEncoder? Try the following line:

```

X264_OPTS="b_adapt=2:direct=auto:me=umh:partitions=all:rc_lookahead=60:ref=8:subq=9:trellis=2:threads=auto:keyint=${KEYINT}"

```

as replacement for the existing line in the script, it mirrors the x264 *slower *preset and might be enough to get the video going. As for the audio I suspect that your copy of MEncoder is not setup for mp3 work, try the following:

```

andrew@skamandros~$ **[COLOR="Red"]mencoder -oac help | grep 'lame'[/COLOR]**
   mp3lame  - cbr/abr/vbr MP3 using libmp3lame

```

and if you do not get the result shown above have a look at repairing your shared avcodec libraries:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

I am no longer a great MEncoder user so I am not sure if mp3 encoding can be reinstated in this way but I suspect it may :).

---

### Post by Joseph Schwenker on 2011-07-06
Though I still can't even begin to figure out how to get sound working with GLC, I've solved that problem to some extent with outrec/pa-clone (though I still have to manually sync up audio).

However, I'd like to try recording in different formats and higher qualities. What about 720p with libtheora for video? What command could I use to record in that format at that resolution?

---

### Post by Joseph Schwenker on 2011-07-11
Woot! Not sure why, but the command to extract sound from GLC is now working 100% and is completely synced up with the video feed automatically. The commands I'm using are:

To start capturing immediately at half the original resolution to the file "video":
```
glc-capture --resize=0.5 -s -o video /opt/PenumbraCollection/overture
```
To encode the video feed to the file "test.avi"
```
glc-play video -y 1 -o - | ffmpeg -i - -sameq test.avi
```
To encode the audio feed to the file "audio.wav"
```
glc-play video -a 1 -o audio.wav
```

Then you can import the audio and video into a video editor like OpenShot, and they should be synced up properly.

---

### Post by ubudog on 2011-07-24
Thanks for this!  WOOT!

---

### Post by Joseph Schwenker on 2011-07-24
> **ubudog said:**
> Thanks for this!  WOOT!

Glad this helped you! Keep in mind, however, that GLC can only capture audio from ALSA; games running on OSS (Unreal Tournament 2004) or PulseAudio (Amnesia: The Dark Descent) will record no audio. You'll have to use the pa-clone script and manually synchronize audio with video for games like those.

---

