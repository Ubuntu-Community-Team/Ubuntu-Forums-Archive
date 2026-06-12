---
title: "mencoder script problem"
date: 2013-03-25
forum: Multimedia Software
---

### Post by bbb13 on 2013-03-25
```
Code:
#!/bin/bash for file do base=${file%.*} ext=${file##*.} newname=${base}"_subt".mpg mencoder "$file" -sub ${base}.srt -subcp utf-8 -font /usr/share/fonts/msttcorefonts/arial.ttf -subfont-text-scale 2.5 -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf harddup -srate 44100 -af lavcresample=44100 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:vstrict=0:acodec=mp2:abitrate=128:aspect=16/9 -ofps 25 -o "$newname" | zenity --progress --text="Working: $file" --pulsate --auto-close done zenity --info \ --text="Finished"
```

whats wrong with this script?it's supposed to convert a video file to mpeg2 and embed the subtitles.i tried it in an mp4 file and it worked.i tried in mkv and it does convert the video but doesn't embed the subs. so any ideas how should i make the script to work.with all filetypes?

---

### Post by shantiq on 2013-03-25
you might want to work [mkvmerge]("http://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge.html") somewhere in your script ; it might be a lot easier than mencoder for this specific task


part of   ```
sudo apt-get install mkvtoolnix
```

---

### Post by bbb13 on 2013-03-25
what would be the benefit of mkvmerge and how would it help me to embed the subs?

---

### Post by shantiq on 2013-03-26
> i tried in mkv and it does convert the video but doesn't embed the subs.  ::]]



**if my suggestion is not of use to you i apologize.**   [it was only a thought]


syntax [here]("http://superuser.com/questions/292608/add-another-subtitles-to-matroska-file-on-linux")

and to see tracks use


> First, use mkvmerge to list the MKV file&#8217;s contents:

mkvmerge -i MovieFile.mkv
You&#8217;ll see a listing similar to this:

File 'MovieFile.mkv': container: Matroska
Track ID 1: subtitles (S_TEXT/ASS)
Track ID 2: audio (A_MPEG/L3)
Track ID 3: video (V_MPEG4/ISO/AVC)

---

### Post by SeijiSensei on 2013-03-26
Well after that less than informative response, let me ask a couple of questions.

First, are you trying to create a standard DVD playable in a DVD player?  When you say you want to "embed" the subtitles, do you mean you want to keep them as "soft" subtitles which can be switched on or off, or "hard" subtitles that are burned into the video image?

Matroska (".mkv") is a container format that supports soft subtitles.  In the script you posted, the subtitles are stored in a .srt file, but a Matroska file includes the subs as a "stream" just like the audio and video streams.  You can extract the subs, and the audio and video streams, using mkvtoolnix, convert the video, and reassemble the result into a new Matroska file, but I don't think that is really what you are trying to do.  Perhaps you can extract the subs to an .srt file then run your script.

If you want to create a standard DVD from existing media files, I suggest trying DeVeDe.  It's in the Ubuntu repositories.  If that's not what you want to accomplish, why are you bothering with mpeg2, an old and inefficient format compared to modern mpeg4 derivatives like H.264?

Mencoder was designed long ago and was targeted at producing AVI files from various material. I used it when H.264 was first released because my computer didn't have the horsepower to decode the more processor-intensive format.  It was pretty foolproof for converting H.264-encoded videos in the Matroska container to XviD-encoded videos in the AVI container.  Mencoder has been tweaked to try and keep up with changes in video technologies, but at this point it is pretty much a dead project.  The [mplayer2]("http://www.mplayer2.org/") developers, for instance, explicitly removed mencoder from their mplayer fork because the code was just too shoddy to warrant further development.  You might want to look into using ffmpeg (aka avconv) instead.

---

### Post by shantiq on 2013-03-26
removed

---

### Post by SeijiSensei on 2013-03-26
Your original post above mine originally read simply "::]]".  I have no idea what this is supposed to mean. In general, smileys and their equivalents should be avoided in forums like this one with an emphasis on content and a worldwide audience. I notice that you have since added more content to your posting.  I was responding to the original version which was, to say the least, uninformative.

---

### Post by shantiq on 2013-03-26
oh Sensei terrible misunderstanding  !!
For some reason your browser only displayed a tiny portion of my reply  [it was all there from the start!]

   i see it happens from time to time.....    no worries....     it seemed right out of character   [seen much of your good work on Forum previously]...   hope you see it all now..   and i was not sure how much help mkvtoolnix and especially mkvmerge could help here  but somehow always a better tool for mkv than mencoder for the reasons you mentioned;    to see if it can b worked in into a script    anyway   best of luck to OP here.

---

### Post by bbb13 on 2013-03-26
i have a crappy sony bravia TV that supports usb. for some reason this TV only responds well and foolproof to mpeg2 files and some avis. But mpeg2 is the guarantee way. and of course, the TV doesnt support external subs,so the only way its hardcoded. so what i.need is a way to convert every video (avi,mkv,mp4) to mpeg2, fast -no avidemux. i didnt actually knew tha mencoder is dead, so i'll take a look into mkvmerge.any other suggestions are welcome.

p.s.every video i own has external srt subs, so no streams in any of my mkv's.

---

### Post by evilsoup on 2013-03-26
MKVmerge is a very useful tool in general, but I don't think it can do what you want. It can set up soft subtitles, but it can't burn them into the image (hardsub). Your best bet would be to use ffmpeg's subtitles filter. Assuming your input file is called 'input.mp4', and the subtitles file is called 'subtitle.srt':

```

ffmpeg -i input.mp4 -filter:v 'subtitles=subtitle.srt' -c:v mpeg2video -q:v 4 -c:a ac3 -ac 2 -ab 192k output.avi

```

This will give you mpeg2 video, with a quantiser setting of 4 - this sets a sort of constant quality, rather than a bit rate (VBR, Variable Bit Rate). The range is 1-32, where lower=better quality and about 2-5 is generally a sensible range to use. You should consider using MPEG4 video, which will give you smaller/better quality files, and should be compatible with most DVD players, even most cheap ones. MPEG4 uses the same quantiser range as MPEG2.

This command will also convert the audio to AC3 with two audio channels (so, stereo) and a constant bit rate of 192 kbit/s. AC3 is a standard part of DVD VOB files, so should be compatible. If you have surround-sound audio that you don't want to be downmixed to stereo, just ditch the '-ac 2' and dial the bit rate up to 384k. If you have some audio that you just want copied (because you're sure that it will work), use '-c:a copy' and ditch the other audio options.
 
The following command will use MPEG4 video with an xvid tag (which some players need for some reason), and will simply copy the audio:

```

ffmpeg -i input.mp4 -filter:v 'subtitles=subtitle.srt' -c:v mpeg4 -q:v 4 -tag:v xvid -c:a copy output.avi

```

Note that the version of ffmpeg in the Ubuntu repos is a crippled, fake version from the libav team. If you use avconv instead, that *might* work; you'd be best off either grabbing a [static build from the downloads page](https://ffmpeg.org/download.html) or [compiling it yourself](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide). The [Jon Severinsson PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg) might be an option (I don't know if it has the subtitles filter yet).

[This blog post](http://evilsoup.wordpress.com/2013/02/10/general-ffmpeg-encoding-guide-2/) gives a decent general overview of useful delivery codecs & their usage with ffmpeg (though the information of VP8 is out of date).

---

### Post by bbb13 on 2013-03-27
> **evilsoup said:**
> MKVmerge is a very useful tool in general, but I don't think it can do what you want. It can set up soft subtitles, but it can't burn them into the image (hardsub). Your best bet would be to use ffmpeg's subtitles filter. Assuming your input file is called 'input.mp4', and the subtitles file is called 'subtitle.srt':

```

ffmpeg -i input.mp4 -filter:v 'subtitles=subtitle.srt' -c:v mpeg2video -q:v 4 -c:a ac3 -ac 2 -ab 192k output.avi

```

This will give you mpeg2 video, with a quantiser setting of 4 - this sets a sort of constant quality, rather than a bit rate (VBR, Variable Bit Rate). The range is 1-32, where lower=better quality and about 2-5 is generally a sensible range to use. You should consider using MPEG4 video, which will give you smaller/better quality files, and should be compatible with most DVD players, even most cheap ones. MPEG4 uses the same quantiser range as MPEG2.

This command will also convert the audio to AC3 with two audio channels (so, stereo) and a constant bit rate of 192 kbit/s. AC3 is a standard part of DVD VOB files, so should be compatible. If you have surround-sound audio that you don't want to be downmixed to stereo, just ditch the '-ac 2' and dial the bit rate up to 384k. If you have some audio that you just want copied (because you're sure that it will work), use '-c:a copy' and ditch the other audio options.
 
The following command will use MPEG4 video with an xvid tag (which some players need for some reason), and will simply copy the audio:

```

ffmpeg -i input.mp4 -filter:v 'subtitles=subtitle.srt' -c:v mpeg4 -q:v 4 -tag:v xvid -c:a copy output.avi

```

Note that the version of ffmpeg in the Ubuntu repos is a crippled, fake version from the libav team. If you use avconv instead, that *might* work; you'd be best off either grabbing a [static build from the downloads page]("https://ffmpeg.org/download.html") or [compiling it yourself]("http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide"). The [Jon Severinsson PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg") might be an option (I don't know if it has the subtitles filter yet).

[This blog post]("http://evilsoup.wordpress.com/2013/02/10/general-ffmpeg-encoding-guide-2/") gives a decent general overview of useful delivery codecs & their usage with ffmpeg (though the information of VP8 is out of date).

thnx a lot, i'll post back soon with results!

---

