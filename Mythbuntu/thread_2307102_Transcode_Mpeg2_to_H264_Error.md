---
title: "Transcode Mpeg2 to H264 Error"
date: 2015-12-21
forum: Mythbuntu
---

### Post by elliott6 on 2015-12-21
Hi All!

Turned my mythbuntu server over, and am trying to transcode the recordings using the "Transcode Mpeg2 to H264" page from the mythTV wiki - [https://www.mythtv.org/wiki/Transcode_Mpeg2_to_H264](https://www.mythtv.org/wiki/Transcode_Mpeg2_to_H264)

Hoping this is an easy fix. I am using v2, and getting the following error ->

```
mythuser@mythboxBE:/usr/bin$ /usr/bin/transcode-h264-v2.py 5024
Traceback (most recent call last):
  File "/usr/bin/transcode-h264-v2.py", line 627, in <module>
    main()
  File "/usr/bin/transcode-h264-v2.py", line 619, in main
    runjob(jobid=args[0])
  File "/usr/bin/transcode-h264-v2.py", line 292, in runjob
    task = System(path=transcoder, db=db)
  File "/usr/lib/python2.7/dist-packages/MythTV/system.py", line 108, in __init__
    raise MythFileError('Defined executable path does not exist.')
MythTV.exceptions.MythFileError: Defined executable path does not exist.
```

I followed the wiki's instructions to compile FFMPEG. Added "Transcode h264" as a User Job. When run from within Mythbuntu, I get "ERROR: User Job returned non-zero, check logs." So I checked the logs only to find nothing of substance - mythboxBE mythbackend: mythbackend[1813]: E UserJob_5024 jobqueue.cpp:2444 (DoUserJobThread) JobQueue: User Job '/usr/bin/transcode-h264-v2.py 5024' failed. That's when I ran in a command prompt and received the above error "MythTV.exceptions.MythFileError: Defined executable path does not exist."

Any ideas? Hoping it's a permissions issue or something else - and yes, I have correctly sudo chmod a+x /usr/bin/transcode-h264-v2.py as well as tried it on two other recordings with the same result.

Thanks for reading!

elliott

---

### Post by blm-ubunet on 2015-12-22
That script (by default) expects ffmpeg to be in /usr/bin.
If you built ffmpeg from source it is very likely in /usr/local/bin

Depending on how old your mythtv is & where & how your packages are built..
You could just use mythffmpeg (/usr/bin)

---

### Post by FakeOutdoorsman on 2015-12-23
If you followed the compile guide on FFmpeg Wiki, then the ffmpeg binary will be in ~/bin (in the bin directory of the user who compiled ffmpeg). You can change the script to point there instead.

---

### Post by elliott6 on 2015-12-23
Thanks for the replies. Unfortunately, I'm not finding FFmpeg any of the spots mentioned, which may be the issue. And I tried changing to use mythffmpeg, but that bombed out as well. 

Therefore, I tried to "recompile" FFmpeg ([https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu#ffmpeg](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu#ffmpeg)) copying and pasting line by line instead of a mass copy and paste, and noticed the following:

For x265 (end - make distclean "stops", but like the first time, I ignored it):

```
mythuser@mythboxBE:~/ffmpeg_sources/x265/build/linux$ PATH="$HOME/bin:$PATH" cmake -G "Unix Makefiles" -DCMAKE_INSTALL_PREFIX="$HOME/ffmpeg_build" -DENABLE_SHARED:bool=off ../../source
-- cmake version 2.8.12.2
-- Detected x86_64 target processor
-- Could NOT find NUMA (missing:  NUMA_ROOT_DIR NUMA_INCLUDE_DIR NUMA_LIBRARY) 
-- Found Yasm 1.2.0 to build assembly primitives
-- hg found at /usr/bin/hg
-- x265 version 1.8+129-e2e507ffe752
-- Configuring done
-- Generating done
-- Build files have been written to: /home/mythuser/ffmpeg_sources/x265/build/linux
mythuser@mythboxBE:~/ffmpeg_sources/x265/build/linux$ make
[ 63%] Built target common
[ 87%] Built target encoder
[ 87%] Built target x265-static
[100%] Built target cli
mythuser@mythboxBE:~/ffmpeg_sources/x265/build/linux$ make install
[ 63%] Built target common
[ 87%] Built target encoder
[ 87%] Built target x265-static
[100%] Built target cli
Install the project...
-- Install configuration: "Release"
-- Up-to-date: /home/mythuser/ffmpeg_build/lib/libx265.a
-- Up-to-date: /home/mythuser/ffmpeg_build/include/x265.h
-- Up-to-date: /home/mythuser/ffmpeg_build/include/x265_config.h
-- Up-to-date: /home/mythuser/ffmpeg_build/lib/pkgconfig/x265.pc
-- Up-to-date: /home/mythuser/ffmpeg_build/bin/x265
mythuser@mythboxBE:~/ffmpeg_sources/x265/build/linux$ make distclean
make: *** No rule to make target `distclean'.  Stop.
mythuser@mythboxBE:~/ffmpeg_sources/x265/build/linux$ 
```

And in my build of FFmpeg:

```
mythuser@mythboxBE:~/ffmpeg_sources$ cd ffmpeg
mythuser@mythboxBE:~/ffmpeg_sources/ffmpeg$ PATH="$HOME/bin:$PATH" PKG_CONFIG_PATH="$HOME/ffmpeg_build/lib/pkgconfig" ./configure \
>   --prefix="$HOME/ffmpeg_build" \
>   --pkg-config-flags="--static" \
>   --extra-cflags="-I$HOME/ffmpeg_build/include" \
>   --extra-ldflags="-L$HOME/ffmpeg_build/lib" \
>   --bindir="$HOME/bin" \
>   --enable-gpl \
>   --enable-libass \
>   --enable-libfdk-aac \
>   --enable-libfreetype \
>   --enable-libmp3lame \
>   --enable-libopus \
>   --enable-libtheora \
>   --enable-libvorbis \
>   --enable-libvpx \
>   --enable-libx264 \
>   --enable-libx265 \
>   --enable-nonfree

[COLOR="#FF0000"]ERROR: x265 not found using pkg-config[/COLOR]

If you think configure made a mistake, make sure you are using the latest
version from Git.  If the latest version fails, report the problem to the
ffmpeg-user@ffmpeg.org mailing list or IRC #ffmpeg on irc.freenode.net.
Include the log file "config.log" produced by configure as this will help
solve the problem.
mythuser@mythboxBE:~/ffmpeg_sources/ffmpeg$ PATH="$HOME/bin:$PATH" make
Makefile:2: config.mak: No such file or directory
Makefile:63: /common.mak: No such file or directory
Makefile:105: /libavutil/Makefile: No such file or directory
Makefile:105: /library.mak: No such file or directory
Makefile:107: /doc/Makefile: No such file or directory
Makefile:190: /tests/Makefile: No such file or directory
make: *** No rule to make target `/tests/Makefile'.  Stop.
mythuser@mythboxBE:~/ffmpeg_sources/ffmpeg$
```

Did I do something else wrong? Is there a better way of going about this?

Thanks again for looking, and I appreciate any and all trying to help me through this! Happy Holidays!

elliott

---

### Post by FakeOutdoorsman on 2015-12-24
> **elliott6 said:**
> ```

make: *** No rule to make target `distclean'.  Stop.

```
You can ignore that. Understandably this confuses users once in a while. I may remove that step. It's only there in the rare chance that someone wants to re-compile using the same source, but the guide simply deletes that stuff anyway in the updating section.


> **elliott6 said:**
> ```
ERROR: x265 not found using pkg-config
```
Did I do something else wrong? Is there a better way of going about this?
You did nothing wrong. This is an upstream issue. Rarely happens, but it is a known issue.

Do this:
```
cd ~/ffmpeg_sources/ffmpeg
make distclean
```

Then run the configure line from the guide without the --enable-libx265 part and continue as usual.

Alternatively, instead of compiling, you could just [download an already compiled binary](http://johnvansickle.com/ffmpeg/) and point your script to it. There are other alternatives too (PPAs), but I don't know what Ubuntu version you're using.

---

### Post by elliott6 on 2015-12-24
Thanks FakeOutdoorsman! Is this your script?! Or you a contributor to the wiki for ffmpeg?

I fired away, and tried the mythffmpeg again, and it looks like it is running! Woohoo.. and very well - my 10Gb recording went to 3Gb! "Transcode Completed @ 5529kbps, compressed file by 72% (clipped 20%, transcoder compressed...)

I did see this error - "Read no lines of ffmpeg output for 80 secs. Possible Hang?" - at the end. Thoughts?

Here's my version information:

```
mythuser@mythboxBE:~/ffmpeg_sources$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.3 LTS
Release:	14.04
Codename:	trusty
```

Would I be better with compiling, already compiled, or continue with mythffmpeg? Is there a benefit?

I really appreciate the help. My wife's Hallmark Movies were taking up far too much space (as well as the kids cartoons..)!!! I'm hoping to actually drop cable, so trying to binge record before making the switch (I'll keep OTA, and possibly setup an off-site recording back-end.. maybe.). This is super.

Again, Thank you thank you thank you! Merry Christmas, or Happy Holidays if you celebrate something else!

elliott

---

### Post by FakeOutdoorsman on 2015-12-24
> **elliott6 said:**
> Is this your script?!
I have no experience with the myth stuff and didn't really take a close look at the script.

> **elliott6 said:**
> Or you a contributor to the wiki for ffmpeg?
I've contributed, but it's a wiki and anyone can edit.

> **elliott6 said:**
> "Read no lines of ffmpeg output for 80 secs. Possible Hang?" - at the end. Thoughts?
Must be a mythffmpeg message, so I don't have a clue if it is important or not. If the output looks good I guess you can ignore it.

> **elliott6 said:**
> Would I be better with compiling, already compiled, or continue with mythffmpeg? Is there a benefit?
For H.264...whatever is easiest for you. x264 is mature so compiling has fewer benefits for that encoder than it did back in the day. However, FFmpeg is still very active in development. Main advantage of compiling is customization for your exact needs, but if the downloadable build works fine for you it's an easy option. If you're familiar with PPAs then [mc4man has a good one]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media") for 14.04 if you prefer that method.

> **elliott6 said:**
> ...Hallmark Movies...
My condolences.

---

### Post by blm-ubunet on 2015-12-24
Definitely check the output PQ before wasting time & effort..

MythTV contains/builds against a private copy/version of ffmpeg's source.
MythTV master's copy of ffmpeg is only couple months old, 0.27+fixes is a lot older.
mythffmpeg/mythffplay etc are optionally compiled from mythtv and this is decided by the package manager.

I would check the compiled options of mythffmpeg to make sure it was configured for external libx264 support and is actually using libx264. Ffmpeg also has a lower quality internal H264 encoder that might be in use.
You could see this info in the stdout messages/logs.

---

### Post by FakeOutdoorsman on 2015-12-24
> **blm-ubunet said:**
> Ffmpeg also has a lower quality internal H264 encoder that might be in use.
FFmpeg does not have a native H.264 encoder. Maybe you meant the encoder "mpeg4" for MPEG-4 Part 2 video?

---

### Post by blm-ubunet on 2015-12-24
Definitely not, I meant H264 MPEG4-part 10.
My mistake, thought ffmpeg had some fallback H264 encoder.

Have a nice Christmas.. (checkout the MythCenter Xmas theme)

---

