---
title: "Mencoder (or a GUI) Conversion for Android"
date: 2010-04-28
forum: Multimedia Software
---

### Post by HarshReality on 2010-04-28
So I typically use cat to put my avi files together.. but today  I figure lets see about ripping over so I can watch on my Droid.

As nobody has a xvid or vlc player on the droid (yet.. coders are doing alot for Android ya know) I will have to convert the video down and change the format.. So.. can anybody tell me a mencoder command line directive to get as close to this as possible (I found ipod settings leave the actual video lacking).

Video
Format          MP4
Encoder        H.264
Resolution     854 x 480 (or 720 x 480; 480 x 320; 320 x 240)
Frame Rate   12 fps - 30 fps
Bit Rate        254Kbps - 2500Kbps

Audio
Encoder        AAC
Sample Rate 22050Hz - 48000Hz
Bit Rate        128Kbps - 256Kbps

---

### Post by sorceror on 2010-10-01
Here's a sample script I use to convert high-def video from my camcorder for viewing on my Droid 1. It encodes to H264 & AAC, and uses MP4Box to put it into an mp4 file.

```
#!/bin/bash
# Helps handling filenames with spaces
IFS=`printf '\n\t'`

## Set up parameters for encoding

# If you're skipping frames, increase FPS. If duplicating, decrease FPS.
# Usual values are 24000/1001 (23.976), 24, 25 (PAL), 30000/1001 (29.97), 30.
#OFPS="-ofps 24"
#OFPS="-ofps 30"
#OFPS="-ofps 24000/1001"
OFPS="-ofps 30000/1001"

# Aspect ratio of video
ASPECT=16:9
# Height of the output video (default for Droid: 480)
SCALEH=480

# Width of the output video (default for Droid: 848) Yes, the screen's bigger than 848,
# but 854 isn't divisible by 16.
SCALEW=848

# Log file name
TEMP_FILE_DIR=`mktemp -d`

# This is the key parameter we gotta have from the user.
# Spaces in the output file name are probably not a good idea.
if [ -n "$1" ]; then
  NEWNAME=$1
else
  echo Output file name not specified, aborting!
  echo "Usage: " $0 " output-name input-video"
  exit 0
fi

# Do the actual encoding (2 passes)
nice -n 10 /usr/bin/mencoder $2 \
-o /dev/null -passlogfile ${TEMP_FILE_DIR}/pass.log -vf softskip,dsize=${ASPECT},scale=${SCALEW}:${SCALEH}:0,harddup -sws 10 -channels 2 -oac faac -faacopts mpeg=4:object=2:br=128 ${OFPS} -ovc x264 -x264encopts pass=1:bitrate=1000:turbo=2:me=umh:me_range=16:dct_decimate:nointerlaced:no8x8dct:nofast_pskip:trellis=0:partitions=p8x8,i4x4:mixed_refs:keyint=240:keyint_min=24:psy_rd=0.8,0.0:frameref=1:bframes=0:b_adapt=0:noweight_b:direct_pred=none:subq=8:chroma_me:nocabac:aq_mode=1:deblock:vbv_maxrate=1500:vbv_bufsize=1000:level_idc=30:threads=auto:ssim:psnr:weightp=0

nice -n 10 /usr/bin/mencoder $2 \
-o ${TEMP_FILE_DIR}/${NEWNAME}.avi -passlogfile ${TEMP_FILE_DIR}/pass.log -vf softskip,dsize=${ASPECT},scale=${SCALEW}:${SCALEH}:0,harddup -sws 10 -af lavcresample=48000:16:1 -srate 48000 -channels 2 -oac faac -faacopts mpeg=4:object=2:br=128 ${OFPS} -ovc x264 -x264encopts pass=2:bitrate=1000:me=umh:me_range=16:dct_decimate:nointerlaced:no8x8dct:nofast_pskip:trellis=0:partitions=p8x8,i4x4:mixed_refs:keyint=240:keyint_min=24:psy_rd=0.8,0.0:frameref=1:bframes=0:b_adapt=0:noweight_b:direct_pred=none:subq=8:chroma_me:nocabac:aq_mode=1:deblock:vbv_maxrate=1500:vbv_bufsize=1000:level_idc=30:threads=auto:ssim:psnr:weightp=0


# Extract the video and sound from the .avi
/usr/bin/mencoder ${TEMP_FILE_DIR}/${NEWNAME}.avi -nosound -ovc copy -of rawvideo -o ${TEMP_FILE_DIR}/h264_video.h264

/usr/bin/MP4Box -aviraw audio ${TEMP_FILE_DIR}/${NEWNAME}.avi -out ${TEMP_FILE_DIR}/aac.raw
mv -f ${TEMP_FILE_DIR}/aac_audio.raw ${TEMP_FILE_DIR}/aac_audio.aac

# Package the video and sound into the .mp4
/usr/bin/mplayer ${TEMP_FILE_DIR}/${NEWNAME}.avi -noconfig all -loop 1 -identify -nosound -vo null -nocache -frames 1 2>/dev/null | grep '^ID_VIDEO_FPS' | tail -n 1 | awk -F= '{print $2}' > ${TEMP_FILE_DIR}/mp4fps

/usr/bin/MP4Box -fps $(cat ${TEMP_FILE_DIR}/mp4fps) -tmp ${TEMP_FILE_DIR} -add ${TEMP_FILE_DIR}/h264_video.h264  -add ${TEMP_FILE_DIR}/aac_audio.aac#audio:name="LC-AAC Stereo"   -itags name="${NEWNAME}":comment="Tagged on $(date)" -ipod -mpeg4 -new "${NEWNAME}.mp4"

# Clean up the intermediate stuff
rm -rf ${TEMP_FILE_DIR}

```

---

