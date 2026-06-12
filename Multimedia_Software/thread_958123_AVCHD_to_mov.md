---
title: "AVCHD to mov"
date: 2008-10-25
forum: Multimedia Software
---

### Post by relent on 2008-10-25
This relates to my experiences with 1080i60 footage from a Canon HF100.  The footage came from my friend's camcorder and he transferred the MTS files to my PC.  The latest versions of mencoder and ffmpeg (built from svn) both handle AVCHD, but each has problems.  Ffmpeg can't seem to handle the framerate of the HF100 footage, leading to stuttering (as noted by ArtInvent, to whom I am indebted, in his posts on this forum).  Mencoder can decode AVCHD correctly, but creates files which may not be compatible with other software.  In my case, Quicktime and Final Cut Pro can't read the files created by mencoder.  Therefore the solution for me has been to use both mencoder and ffmpeg to convert AVCHD footage into a usable, editable format:

ffmpeg -i 00058.MTS -acodec pcm_s16le -ac 2 ~/00058.wav
mencoder 00058.MTS -o ~/00058.yuv -vf format=i420 -oac pcm -ovc raw -noskip -fps 60000/1001 -ofps 30000/1001 -of rawvideo
ffmpeg -i ~/00058.wav -s 1920x1080 -i ~/00058.yuv -acodec pcm_s16le -ac 2 -vcodec mpeg4 -sameq -aspect 16:9 -copyts 00058.mov

The first command creates an audio file in pcm format.  Filesize is not an issue for me, so no compression.  

The second command creates a raw (i.e. uncompressed) video file.  Finding the format (i420) which worked for ffmpeg took a while.  The -fps and -ofps options are required to decode all the frames correctly without stuttering and relate to footage shot in 1080i60 (i.e. you would need to change these for 1080i50).

The third command takes the audio and video files just created and combines them into a mov file.  I am not sure whether the "-sameq -aspect 16:9 -copyts" bit is needed/appropriate, but it seems to work for me.

There was another problem.  My own camera (HV20) shoots 1080i50 footage and uses a different pixel and frame size.  I wanted the footage from both cameras to be in the same form for editing.  That meant reducing the framerate of the AVCHD footage and rescaling it.  The revised commands for that:

ffmpeg -i 00058.MTS -acodec pcm_s16le -ac 2 ~/00058.wav
mencoder 00058.MTS -o ~/00058.yuv -vf format=i420,filmdint=io=6:5,harddup -oac pcm -ovc raw -noskip -fps 60000/1001 -ofps 25 -of rawvideo
ffmpeg -i ~/00058.wav -s 1920x1080 -i ~/00058.yuv -acodec pcm_s16le -ac 2 -vcodec mpeg4 -sameq -s 1440x1080 -aspect 16:9 -copyts 00058.mov

Or, for batch processing:

for i in *MTS; 
do j=`echo $i | sed s/.MTS//`; 
ffmpeg -i $i -acodec pcm_s16le -ac 2 ~/$j.wav; 
mencoder $i -o ~/$j.yuv -vf format=i420,filmdint=io=6:5,harddup -oac pcm -ovc raw -noskip -fps 60000/1001 -ofps 25 -of rawvideo; 
ffmpeg -i ~/$j.wav -s 1920x1080 -i ~/$j.yuv -acodec pcm_s16le -ac 2 -vcodec mpeg4 -sameq -s 1440x1080 -aspect 16:9 -copyts $j.mov; 
rm ~/$j.wav ~/$j.yuv; 
done

To use mplayer to view the original MTS files:

mplayer -demuxer lavf -lavdopts threads=4:fast:skiploopfilter=all:skipframe=none -fps 60000/1001 [filename]

To build ffmpeg and mplayer/mencoder from source, i used the following configure options for ffmpeg:

./configure --enable-gpl --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid

and for mplayer/mencoder:

./configure --enable-gui

Hope this helps someone!

---

