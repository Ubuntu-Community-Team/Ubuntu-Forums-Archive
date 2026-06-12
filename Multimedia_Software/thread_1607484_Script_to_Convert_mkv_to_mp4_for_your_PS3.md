---
title: "Script to Convert mkv to mp4 for your PS3"
date: 2010-10-27
forum: Multimedia Software
---

### Post by ASULutzy on 2010-10-27
I noticed that a lot of the HD video content I find on the internet is usually a .mkv file. Unfortunately, the PS3 won't natively play these files, and reencoding HD video takes forever, but luckily we can convert to .mp4 with no quality loss and no video reencoding.

This script assumes you already have all the necessary tools for converting mkv files and dealing with aac audio. (gpac, unstripped libs, mkvtoolsnix)

Anyway, here's the script. It will convert all mkv's in the current folder and all subfolders to mp4's, deleting the mkv's and cleaning up all the temp stuff. It currently deletes the original mkv file, but if you don't want it to do that or you think I suck at writing scripts, just comment out the if statement and the rm -f line.

Let me know if you encounter any problems while using it.

```
#!/bin/bash

find . -type f | grep .mkv$ | while read file
do
 directory=`dirname "$file"`
 title=`basename "$file" .mkv`
 AC3=`mkvinfo "$file" | grep AC3` #check if it's AC3 audio or DTS
 AAC=`mkvinfo "$file" | grep AAC`
 order=`mkvinfo "$file" | grep "Track type" | sed 's/.*://' | head -n 1 | tr -d " "` #check if the video track is first or the audio track
 if [ "$order" = "video" ]; then
  fps=`mkvinfo "$file" | grep duration | sed 's/.*(//' | sed 's/f.*//' | head -n 1` #store the fps of the video track
  if [ -n "$AC3" ]; then
   mkvextract tracks "$file" 1:"${title}".264 2:"${title}".ac3 
   ffmpeg -i "${title}".ac3 -acodec libfaac -ab 576k "${title}".aac
 #  mplayer -ao pcm:file="${title}".wav:fast "${title}".ac3
 #  faac -o "${title}".aac "${title}".wav
  elif [ -n "$AAC" ]; then
   mkvextract tracks "$file" 1:"${title}".264 2:"${title}".aac
  else
   mkvextract tracks "$file" 1:"${title}".264 2:"${title}".dts
   ffmpeg -i "${title}".dts -acodec libfaac -ab 576k "${title}".aac
  fi
 else
  fps=`mkvinfo "$file" | grep duration | sed 's/.*(//' | sed 's/f.*//' | tail -n 1`
  if [ -n "$AC3" ]; then
   mkvextract tracks "$file" 1:"${title}".ac3 2:"${title}".264
   ffmpeg -i "${title}".ac3 -acodec libfaac -ab 576k "${title}".aac
  # mplayer -ao pcm:file="${title}".wav:fast "${title}".ac3
  # faac -o "${title}".aac "${title}".wav
  elif [ -n "$AAC" ]; then
   mkvextract tracks "$file" 1:"${title}".264 2:"${title}".aac
  else
   mkvextract tracks "$file" 1:"${title}".dts 2:"${title}".264
   ffmpeg -i "${title}".dts -acodec libfaac -ab 576k "${title}".aac
  fi
 fi
 MP4Box -new "${directory}/${title}".mp4 -add "${title}".264 -add "${title}".aac -fps $fps
 rm -f "$title".aac "$title".dts "$title".ac3 "$title".264 "${title}".wav
 if [ -f "${directory}/${title}".mp4 ]; then
  rm -f "$file"
 fi
done

```

---

### Post by frustratednerd on 2010-12-15
Whenever I try this, the script tries to import a .aac file with an identical filename of the .mkv that I'm trying to convert, but it can't find it, so it stops right there. What do I do now?

---

### Post by rubylaser on 2010-12-16
Can you run mkvinfo against your mkv file and paste the results in here?  I'm guessing that you have either a weird audio codec, or the mkv file has the tracks in a different order than video, audio.  Looking at this script it should work in most situations.

---

### Post by divinebovine on 2011-02-05
I was running into the same problem that frustratednerd mentioned above.  I had to change the libfaac to aac and I had to add a -strict experimental flag on the ffmpeg lines.

ASULutzy or rubylaser, did you compile ffmpeg from source?  If so, maybe thats why it doesn't work for us.  I know I just installed it from the repos.  Just a thought.

---

### Post by ki3456 on 2011-02-21
thank you, that was really helpful. I didn't need to convert the audio since it was all aac.   One suggestion. mkvextract automatically overwrites files with the same name. So instead of extracting to   ```
$Title.264 and $Title.aac
``` you can just extract to video.264 and audio.aac.    then in mp4box mux -add video.264 -add audio.aac  When it comes to demuxing the next mkv in the folder video.264 and audio.aac will be overwritten and the file names reused.

---

### Post by inobe on 2011-02-21
why not just use DeVeDe and maintain the high resolution .mkv offers?

just choose the divx option.

the ps3 will play this file, so would divx home players if the file is burned as a data dvd.

---

### Post by ki3456 on 2011-02-21
Here is a cut down version of the script I used. There is no conversion, no checking that video is first stream, and no deletion.

```
#!/bin/bash

find . -type f | grep .mkv$ | while read file
do
 directory=`dirname &quot;$file&quot;`
 title=`basename &quot;$file&quot; .mkv`
 AAC=`mkvinfo &quot;$file&quot; | grep AAC`
 fps=`mkvinfo &quot;$file&quot; | grep duration | sed 's/.*(//' | sed 's/f.*//' | head -n 1` 
 mkvextract tracks &quot;$file&quot; 0:video.264 1:audio.aac
 MP4Box -new &quot;${directory}/${title}&quot;.mp4 -add video.264 -add audio.aac -fps $fps
done
```

---

### Post by ki3456 on 2011-02-21
It just occured to me the other problem with PS3 is it won't attempt to play video higher than level 4.1. Some encoders accidentally set the level to 5.1 Since the tracks are already demuxed might as well set the level to 4.1, so at least the PS3 will try to play the file.

To do that you need to hexedit raw video file. Hexalter will do the job from the command line.

```
#!/bin/bash

find . -type f | grep .mkv$ | while read file
do
 directory=`dirname &quot;$file&quot;`
 title=`basename &quot;$file&quot; .mkv`
 AAC=`mkvinfo &quot;$file&quot; | grep AAC`
 fps=`mkvinfo &quot;$file&quot; | grep duration | sed 's/.*(//' | sed 's/f.*//' | head -n 1` 
 mkvextract tracks &quot;$file&quot; 0:video.264 1:audio.aac
 hexalter video.264 0x7=41
 MP4Box -new &quot;${directory}/${title}&quot;.mp4 -add video.264 -add audio.aac -fps $fps
done
```link for hexalter
```
http://www.kuwanger.net/hexalter.zip
```

---

### Post by Zilioum on 2011-04-23
I was fiddling around for a long time with this .mkv to .mp4 problem, and now I've finally written a little program to take care of it. Here is the URL of the projects page on github:[https://github.com/Basphil/MKVToMP4Converter]("https://github.com/Basphil/MKVToMP4Converter"). 
Turning an .mkv file in an .mp4 file works well, it does check for the order of audio/video streams and chooses the right fps. Depending of the orignal audio format it also changes the volume a bit, becuase in my experience aac tends to be louder in an .mkv than in an .mp4 file.
You can additionally have it watch a directory for new .mkv files, and then it automatically converts them. I'm still working on this part, but for single .mkv files it works reasonably well.

There are still improvements to do (like delete the temp files etc.) but I hope that it can be of use for you.

---

### Post by x0lani on 2011-06-21
ASULutzy's first script in this worked really well for me, though it needed some tweaking.  For example, if track 1 is AAC and track 2 is video, the extraction will output to the wrong files.

The AAC encoding bitrate seems really high at 576k.  Why not use 320k? Or am I missing something?

A further improvement might be to use the Nero AAC encoder, since the libfaac one seems to have a bit of a bad reputation.

@Zilioum, I was never able to get your converter to work.

I'm a noob on these forums.  Where would be the best place to create a HOW-TO on this topic.  It seems to come up a lot with all the PS3's out there.

---

### Post by Zilioum on 2011-06-23
Hi x0lani

My converter should work actually, and it does also extract the right tracks. What doesn't work exactly? Maybe I can give you hand and improve my scripts a bit.

Cheers

---

### Post by beadrifle on 2011-12-22
> **Zilioum said:**
> I was fiddling around for a long time with this .mkv to .mp4 problem, and now I've finally written a little program to take care of it. Here is the URL of the projects page on github:[https://github.com/Basphil/MKVToMP4Converter](https://github.com/Basphil/MKVToMP4Converter). 
Turning an .mkv file in an .mp4 file works well, it does check for the order of audio/video streams and chooses the right fps. Depending of the orignal audio format it also changes the volume a bit, becuase in my experience aac tends to be louder in an .mkv than in an .mp4 file.
You can additionally have it watch a directory for new .mkv files, and then it automatically converts them. I'm still working on this part, but for single .mkv files it works reasonably well.

There are still improvements to do (like delete the temp files etc.) but I hope that it can be of use for you.

I tried the script above, and it says its a successful result. But strangely I cannot locate the newly created .mp4 file. and it does not seem to have taken up any space, I shall try again. But if this is an issue do let me know. Here's what I did:

[PHP]python MKVToMP4Converter.py /media/musicmajor/watch/Planet.Earth.2006.1080p.HDDVD.x264-AJP/Planet.Earth.01.From.Pole.to.Pole.2006.1080p.HDDVD.x264-AJP.mkv 

Extracting tracks
mkvextract tracks /media/musicmajor/watch/Planet.Earth.2006.1080p.HDDVD.x264-AJP/Planet.Earth.01.From.Pole.to.Pole.2006.1080p.HDDVD.x264-AJP.mkv 1:movie.264 2:sound.aac
Extracting track 1 with the CodecID 'V_MPEG4/ISO/AVC' to the file 'movie.264'. Container format: AVC/h.264 elementary stream
Extracting track 2 with the CodecID 'A_AC3' to the file 'sound.aac'. Container format: Dolby Digital (AC3)
Progress: 100%

Adjusting volume of sound.aac and saving to sound_.aac
ffmpeg -i sound.aac -y -vn -acodec libfaac -vol 900 -ac 2 -ar 48000 -ab 160k sound_.aac

Boxing the extracted files into /media/musicmajor/watch/Planet.Earth.2006.1080p.HDDVD.x264-AJP/Planet.Earth.01.From.Pole.to.Pole.2006.1080p.HDDVD.x264-AJP.mp4
MP4Box -new /media/musicmajor/watch/Planet.Earth.2006.1080p.HDDVD.x264-AJP/Planet.Earth.01.From.Pole.to.Pole.2006.1080p.HDDVD.x264-AJP.mp4 -add movie.264 -add sound_.aac -fps 23.976
Done
-------------------------------[/PHP]

---

### Post by Zilioum on 2011-12-22
Hi beadrifle
There might be an issue with the paths. To make sure that the result files don't get put in a non-existing place try to run the program from the folder in which the video file is
```
python /path/to/file/MKVToMP4Converter.py yourMovie.mkv
```All the resulting files should then end up in this folder. Let me know if this worked for you. If this really is an issue with the program, I'll gladly improve it.

---

### Post by ki3456 on 2012-06-03
This script should remux all video, audio and subtitle  tracks from an mkv container into an mp4 container. With the proviso that audio tracks are aac and subtitle tracks are srt.
The script is meant to process all mkv files in a directory.

```
#!/bin/bash
#mkv2mp4.sh

find . -type f | grep .mkv$ | while read file
do
 title=`basename "$file" .mkv`

# script1 holds the video audio and subtitle parameters for mkvextract
# script2 holds the video audio and subtitle parameters for MP4Box
 vidscript1=
 vidscript2=
 audscript1=
 audscript2=
 subscript1=
 subscript2=

# count the number of tracks in the mkv file 
 track_count=`mkvinfo "$file" | grep "Track number:" | wc -l`
 for ((i=1; i<=track_count; i++))
  do

# mkvinfo displays information sorted by track so the first language 
# tag will refer to first track, the second language tag occurrence for the second
# track. Only video tracks hold correct fps information.

    track_nr=`mkvinfo "$file" | grep "Track number" | sed 's/.*number: //' | head -n "$i" | tail -n 1`
    track_type=`mkvinfo "$file" | grep "Track type" | sed 's/.*: //' | head -n "$i" | tail -n 1`
    fps=`mkvinfo "$file" | grep "Default duration" | sed 's/.*(//' | sed 's/ fps.*)//' | head -n "$i" | tail -n 1`
    codec_id=`mkvinfo "$file" | grep "Codec ID" | sed 's/.*: //' | head -n "$i" | tail -n 1`
    language=`mkvinfo "$file" | grep "Language" | sed 's/.*: //' | head -n "$i" | tail -n 1`

    case "$track_type" in
    "video" )
       vidscript1="$vidscript1 $track_nr:video$track_nr.264"
       vidscript2="$vidscript2 -add video$track_nr.264:fps=$fps:lang=$language"
    ;;

# only extract audio that is in aac format
    "audio" )
       if [ "$codec_id" = "A_AAC" ];
    then
         audscript1="$audscript1 $track_nr:audio$track_nr.aac"
         audscript2="$audscript2 -add audio$track_nr.aac:lang=$language:name="
       fi
    ;;

# only extract subtitle that is in srt format
    "subtitles" )
       if [ "$codec_id" = "S_TEXT/UTF8" ];
    then
         subscript1="$subscript1 $track_nr:subtitle$track_nr.srt"
         subscript2="$subscript2 -add subtitle$track_nr.srt:hdlr=sbtl:lang=$language:group=2:layer=-1:disabled:name="
       fi
    ;;
    esac 

  done

# create an mp4 file if a video track and aac audio track are both present
 if [[ $vidscript1 && $audscript1 ]];
    then

# The base filenames mkvextract creates are video.264, audio.aac and subtitle.srt
# Mkvextract extracts all suitable audio video and subtitle tracks.
# Since there could be more than one of each type, tracks have the 
# track number appended to their filenames.

      mkvextract tracks "$file" $vidscript1 $audscript1 $subscript1

# remove first occurrence of ":disabled" from subtitle parameters
  subscript2=${subscript2/:disabled/}

# MP4Box creates a file with the same base name as the mkv file.
      MP4Box -new "${title}".mp4 $vidscript2 $audscript2 $subscript2
 fi
done

```The script relies on the mkvinfo display to find the track information. Mkvinfo's  display does change with different versions of mkvinfo. This script works with mkvinfo version 5.1 (precise). 
To test if script will work with a different version just run this testmkvinfo script. If the output looks good then it should be okay. Otherwise the mkvinfo filters will need to be adjusted.

```
#!/bin/bash
#testmkvinfo.sh

echo
echo " File                       Track    Type     FPS         Codec ID        Lang"   # Header.
echo " -------------------       -------   ----  ---------   --------------   ------"

find . -type f | grep .mkv$ | while read file
do
 title=`basename "$file" .mkv`
 track_count=`mkvinfo "$file" | grep "Track number:" | wc -l`
 for ((i=1; i<=track_count; i++))
  do
    track_nr=`mkvinfo "$file" | grep "Track number" | sed 's/.*number: //' | head -n "$i" | tail -n 1`
    track_type=`mkvinfo "$file" | grep "Track type" | sed 's/.*: //' | head -n "$i" | tail -n 1`
    fps=`mkvinfo "$file" | grep "Default duration" | sed 's/.*(//' | sed 's/ fps.*)//' | head -n "$i" | tail -n 1`
    codec_id=`mkvinfo "$file" | grep "Codec ID" | sed 's/.*: //' | head -n "$i" | tail -n 1`
    language=`mkvinfo "$file" | grep "Language" | sed 's/.*: //' | head -n "$i" | tail -n 1`

    echo ${title// /} | awk '{printf("%-25s ", $1)}'
    echo $track_nr | awk '{printf("%6s", $1)}'
    echo $track_type | awk '{printf("%10s", $1)}'
    echo $fps | awk '{printf("%10s", $1)}'
    echo $codec_id | awk '{printf("%20s", $1)}'
    echo $language | awk '{printf("%6s\n", $1)}'    

  done
done
```

---

### Post by xltrigger on 2012-09-16
> **Zilioum said:**
> Hi beadrifle
There might be an issue with the paths. To make sure that the result files don't get put in a non-existing place try to run the program from the folder in which the video file is
```
python /path/to/file/MKVToMP4Converter.py yourMovie.mkv
```All the resulting files should then end up in this folder. Let me know if this worked for you. If this really is an issue with the program, I'll gladly improve it.

I ran it just like that and I have the same issue. It creates no mp4 file in the end, but says it completed successfully. 

I'm not sure why.

---

