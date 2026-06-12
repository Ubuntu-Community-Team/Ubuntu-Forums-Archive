---
title: "BASH script: MP4 bitrate, scale &amp; encode to AAC/AVC"
date: 2008-10-31
forum: Multimedia Software
---

### Post by ahaslam on 2008-10-31
The purpose of my script is to easily encode HD content to a format that's playable on popular devices including the PS3 & 360. Some files can simply be remuxed into an MP4, for that purpose see [here]("http://www.dufault.info/blog/a-script-to-remux-mkv-videos-into-mp4-videos/"). Otherwise, read on. ;)

Everything should be self explanatory, just note that the PS3 & 360 can't play MP4's > 4096MB. The target file size should come in slightly under what's specified, so no need to undershoot.

```
#!/bin/bash

#Script to calculate bitrate, scale & encode to aac/avc mp4
#uses ffmpeg presets within ~/.ffmpeg (-vpre fast/-vpre vhq)
#examples: http://svn.mplayerhq.hu/ffmpeg/trunk/ffpresets
#depends: mplayer, ffmpeg, x264 & faac
#use: ./mp4 inputFile requiredSize(MB)

IN="$1"
MB="$2"

info() {
mplayer -identify -frames 0 "$IN" 2>/dev/null > /tmp/$$
RESX=`grep ID_VIDEO_WIDTH /tmp/$$ | cut -d"=" -f2`
RESY=`grep ID_VIDEO_HEIGHT /tmp/$$ | cut -d"=" -f2`
LENGTH=`grep ID_LENGTH /tmp/$$ | cut -d"=" -f2`
rm /tmp/$$ && echo ${RESX} ${RESY} ${LENGTH}
}

height() {
ASPECT=$(echo "scale=3; ${RESX} / ${RESY}" | bc)
    
if [ "${RESX}" -ge "1280" ]; 
then
    HEIGHT=$(echo "1280 / ${ASPECT}" | bc)
    MOD16=$(( ${HEIGHT} / 16 * 16 ))
else
    MOD16=$(( ${RESY} / 16 * 16 ))    
fi
echo ${MOD16}
}

audioSize() {
ffmpeg -i "$IN" -vn -acodec libfaac -ac 2 -aq 200 -async 2 "$IN.m4a"
STAT=$(stat "$IN.m4a" | grep Size | awk '{print $2}')
SIZE=$( echo "scale=6; ${STAT} / 1024" | bc)
echo ${SIZE}
}

bitrate() {
RATE=$(echo "(( "$MB" * 1024 ) / ${LENGTH}) - ( ${SIZE} / ${LENGTH})" | bc)
R8=$(echo "(( ${RATE} * 8 ) * 1.02)" | bc)
KBPS=`echo "tmp=${R8}; tmp /= 1; tmp" | bc`
echo ${KBPS}
}

encode() {
ffmpeg -i "$IN" -an -pass 1 -s 1280x${MOD16} -vcodec libx264 -vpre fast \
-b ${KBPS}k -threads 0 -rc_eq 'blurCplx^(1-qComp)' -level 41 "$IN.mp4"
ffmpeg -i "$IN" -acodec libfaac -ac 2 -aq 200 -async 2 -pass 2 \
-s 1280x${MOD16} -vcodec libx264 -vpre vhq -b ${KBPS}k -threads 0 \
-rc_eq 'blurCplx^(1-qComp)' -level 41 -psnr -y "$IN.mp4"
}

info;
height;
audioSize;
bitrate;
encode;
rm *.m4a *.log && echo Finished!
```


**Ffmpeg presets**

What's used here can impact the bitrate required to achieve the specified size. Line 42 of my script may need editing if different presets are used. For example, if no bframes are used you'd certainly need to reduce '1.02' closer to 1.00. If different presets are used frequently, either remove this modifier or specify a preset on the command line & have it change accordingly. 

libx264-fast.ffpreset:

```
coder=1
flags=+loop
cmp=+chroma
partitions=-parti8x8-parti4x4-partp8x8-partp4x4-partb8x8
me_method=dia
subq=1
me_range=16
g=480
keyint_min=24
sc_threshold=40
i_qfactor=0.71
b_strategy=2
qcomp=0.6
qmin=10
qmax=51
qdiff=4
bf=3
refs=1
directpred=1
trellis=0
flags2=-bpyramid-wpred-mixed_refs-dct8x8+fastpskip
```

libx264-vhq.ffpreset:

```
coder=1
flags=+loop
cmp=+chroma
partitions=+parti8x8+parti4x4+partp8x8+partp4x4+partb8x8
me_method=umh
subq=9
me_range=32
g=480
keyint_min=24
sc_threshold=40
i_qfactor=0.71
b_strategy=2
qcomp=0.6
qmin=10
qmax=51
qdiff=4
bf=3
refs=6
directpred=3
trellis=2
flags2=+bpyramid+wpred+mixed_refs+dct8x8-fastpskip
```

The presets above will only work with x264 & ffmpeg > 20081002 (a highly recommended update).

I hope this is of use to someone. It should be easy to customise for other uses, feel free to share your deviations. ;)

---

