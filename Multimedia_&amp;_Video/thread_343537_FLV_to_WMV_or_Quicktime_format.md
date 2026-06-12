---
title: "FLV to WMV or Quicktime format?"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by siersmak on 2007-01-21
Is it possible to use mencoder or ffmpeg (or any other encoder) to convert FLV files to a format that Windows Media Player or Quicktime can play by default?  If so, can you tell me the options to pass to the encoder?

Thanks
-Ken

---

### Post by jbayone on 2007-01-21
If you can't convert, you can always use VLC to play the videos.

---

### Post by DerHesse on 2007-01-21
... or mplayer.
[http://mpui.sourceforge.net/index.php?page=about&lang=en](http://mpui.sourceforge.net/index.php?page=about&lang=en)

---

### Post by siersmak on 2007-01-21
Thanks, but I already know that.  I need to be able to convert because I need to play the FLV on a Windows machine which I don't have admin access to, and which only has Windows Media Player and Quicktime.

---

### Post by DerHesse on 2007-01-22
for mpui aka mplayer you don NOT need admin privilleges.
If you must convert try this script:

```
#!/bin/sh

if [ -z "$1" ]; then
  echo "Usage: $0 {-divx|-xvid} list_of_flv_files"
  exit 1
fi

# video encoding bit rate
V_BITRATE=1000

while [ "$1" ]; do
  case "$1" in
    -divx)
      MENC_OPTS="-ovc lavc -lavcopts \
        vcodec=mpeg4:vbitrate=$V_BITRATE:mbd=2:v4mv:autoaspect"
      ;;
    -xvid)
      MENC_OPTS="-ovc xvid -xvidencopts bitrate=$V_BITRATE:autoaspect"
      ;;
    *)
      if file "$1" | grep -q "Macromedia Flash Video"; then
        mencoder "$1" $MENC_OPTS -vf pp=lb -oac mp3lame \
          -lameopts fast:preset=standard -o \
          "`basename $1 .flv`.avi"
      else
        echo "$1 is not Flash Video. Skipping"
      fi
      ;;
  esac
  shift
done
```

You will need mencoder installed. Get it from the universe repository.

---

### Post by siersmak on 2007-01-22
Thanks for the tips.  I should have said that I cannot encourage the user of the Windows machine to run anything that is not already installed on the machine, since the machine is under the control of a public school system here in the states and I doubt they would appreciate her running 'rogue' applications on it.  

Anyway, I tried that script earlier today, without luck.  Using divx required a divx codec for Windows Media Player, and my installation of mencoder could not encode xvid.  

I was able to create an AVI that WMP could play with ffmpeg:

ffmpeg -i movie.flv -vcodec msmpeg4v2 movie.avi

This also worked:

ffmpeg -i movie.flv -vcodec wmv1 -acodec adpcm_ima_wav movie.wmv

---

### Post by DerHesse on 2007-01-22
> **siersmak said:**
> T

I was able to create an AVI that WMP could play with ffmpeg:

ffmpeg -i movie.flv -vcodec msmpeg4v2 movie.avi

This also worked:

ffmpeg -i movie.flv -vcodec wmv1 -acodec adpcm_ima_wav movie.wmv

That's just great! I will try myself, later! :grin:

Edit: depending on the version of ffmpeg you could even use "-svcd". Works great, Thank's for for that!

---

### Post by hypnotic_frog on 2007-01-30
U need convert FLV to WMV or MOV, right?

I can suggest "Flash to Video Encoder PRO". This converter was made from geovid. May be u heard about this firm? As far as I know it's one of the best in this deal. I have their tool too. Can't say nothing bad about its work and quality. One minus that I know - it costs. But all in all all worth things costs. :)

---

### Post by koshari on 2007-01-30
> Thanks, but I already know that. I need to be able to convert because I need to play the FLV on a Windows machine which I don't have admin access to, and which only has Windows Media Player and Quicktime.


vlc doesnt need to be installed on a win system, just copy the folder over, or execute it off a memory stick, and it will play your flv files for you.

---

### Post by koshari on 2007-01-30
otherwise you can use vlc to transcode the file to whatever you like from command line, or the wizard, 

[http://wiki.videolan.org/IPod](http://wiki.videolan.org/IPod)

for example

---

### Post by ubu-for on 2007-02-26
> **siersmak said:**
> 
ffmpeg -i movie.flv -vcodec msmpeg4v2 movie.avi

THX for the tip but does it also work with the [.undf](http://www.veoh.com/videos/e135447HnWpNPXT?searchId=5444513237868961230&rank=0) video codec?

How can I keep the original audio codec (mp3) from my .flv file? The MP42 audio codec reduced the quality very much.

---

### Post by moyea on 2007-03-21
search "flv to video converter" in google.

---

