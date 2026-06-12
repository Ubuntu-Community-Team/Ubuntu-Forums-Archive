---
title: "HOWTO: Convert Video to play on Xbox360 using ffmpeg"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by tito13kfm on 2007-12-07
Linux users have a hard time getting their video files converted to a format that xbox360 can play successfully.  I know I searched for well over a week and saw conflicting answers and techniques that work about half the time.  That is why I am putting this tutorial up.

This guide will assume you are using Ubuntu or another debian based distro.  This should be easily adaptable to any flavor of linux.
All of these steps can be copy/pasted to your terminal.

Step 1: Install SVN version of ffmpeg with x264 and AAC sound enabled.  The reason we need a new version of ffmpeg is that the one in the official ubuntu repositories doesn't include the needed codecs.
```

sudo apt-get build-dep ffmpeg

sudo apt-get install liblame-dev libfaad2-dev libfaac-dev libxvidcore4-dev liba52-0.7.4 liba52-0.7.4-dev libx264-dev checkinstall build-essential subversion

svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg

cd ffmpeg

./configure --enable-gpl --enable-pp --enable-libvorbis --enable-liba52 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-libx264 (if you have a dual-core processor also include --enable-pthreads)

make

sudo checkinstall

```

2. Converting the video
```

cd /path/to/your/videos/
ffmpeg -y -i INPUTVIDEO.AVI -vcodec libx264 -b BITRATE -flags +loop -cmp +chroma -partitions +parti4x4+partp8x8+partb8x8 -flags2 +mixed_refs -me umh -subq 5 -trellis 1 -refs 5 -bf 3 -b_strategy 1 -coder 1 -me_range 16 -g 250 -keyint_min 25 -sc_threshold 40 -i_qfactor 0.71 -bt "$vbitrate" -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.6 -qmin 10 -qmax 51 -qdiff 4 -level 41 -acodec libfaac -ac 2 -ar 48000 -ab "$abitrate" -f mov OUTPUTVIDEO.MOV

```

3. Get it to your 360
The easiest way would be to burn it to a DVD and play the file directly through the drive, you could also copy it to an external USB HD and view it that way.  Or you can setup ushare and share it across a network.

As you can see, it's not the easiest task in the world, but it does do an excellent job at transcoding videos for the 360

I wrote a bash script for converting that gives you more options.  You can get it here.
[http://for.game-server.cc/convert_for_360.sh](http://for.game-server.cc/convert_for_360.sh)
or attached below.

If anybody has any suggestions/improvements please message me or leave a comment.  If it doesn't work for you, I'll do my best to help you out.

NOTE: I copied/pasted this from a post I made on a different forum.  If the layout or wording seems odd.. it's original target audience was very inexperienced linux users.

---

