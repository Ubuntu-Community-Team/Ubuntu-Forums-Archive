---
title: "DVD to iPhone video: terrible screeching sound using mencoder..."
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by chadjohnson on 2007-09-22
My goal is to rip a DVD so I can watch it on my iPhone (I'm deleting it when I'm done watching it -- I'm not keeping it).

Using the following, the sound in the resulting avi file is terribly corrupted, and when I play it (using mplayer) I get a terrible, loud screeching that seems to very vaguely match the actual audio. The video is fine, however.

```

mencoder dvd:// -ovc xvid -xvidencopts pass=1 -alang en -oac copy -o /dev/null
mencoder dvd:// -ovc xvid -xvidencopts pass=2:bitrate=-700000 -alang en -oac mp3lame -lameopts vbr=3 -o tmp.avi &&
mencoder tmp.avi -vf scale=480:320 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=224 -srate 22050 -af resample=22050:0:0 -oac mp3lame -o movie.avi

```

What am I doing wrong? Is there a better way to encode video for the iPhone (from a shell script)?

---

### Post by chadjohnson on 2007-09-22
I found this URL -- I'll try that: [https://help.ubuntu.com/community/iPodVideoEncoding](https://help.ubuntu.com/community/iPodVideoEncoding)

---

### Post by chadjohnson on 2007-09-23
Ok, solved this myself (using that link I noted above). For anyone in the future having the same problem, the following enabled me to convert an existing avi file to mp4 which is readable by iTunes and the iPhone. I had been getting the same screeching sound both when ripping a DVD and converting an existing avi file before, so I bet this will also work for ripping DVD's iuf you use DVD://1 (or whatever track #) instead of an avi file as input.

```

#1/bin/bash

ffmpeg -y -i "$1" -an -v 1 -threads auto -vcodec libx264 -b 500k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -f mp4 -pass 1 /dev/null
ffmpeg -y -i "$1" -v 1 -threads auto -vcodec libx264 -b 500k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 480x320 -acodec libfaac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 2 $2

```

So run it like this:

./iphonevideo.sh /path/to/inputfile.avi /path/to/outputfile.mp4

or for DVD's:

./iphonevideo.sh "DVD://1" /path/to/outputfile.mp4

---

### Post by we_r_disturbed on 2007-09-24
I too was having the same problem with converting files using mencoder.  It appears to be a known issue and is a reported bug.  I managed to get mine working by downloading and replacing the mencoder and mplayer files under /usr/bin.  
Here is where it is reported [https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/85751)
About halfway down is where they refer to downloading mplayer and mencoder from DeVeDe's website.
Like I said, it worked for me.

---

