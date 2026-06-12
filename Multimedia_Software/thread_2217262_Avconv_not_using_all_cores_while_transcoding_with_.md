---
title: "Avconv not using all cores while transcoding with libx264 codec"
date: 2014-04-16
forum: Multimedia Software
---

### Post by filiprino2 on 2014-04-16
Hi all,
I tried to get a movie transcoded with libx264 and libvorbis instead of AC3-DTS but avconv is not using all 4 cores of my computer. The original file has the video track plus three audio tracks, one in DTS-HD MA, one in DTS and the last one in AC3.

My command line is this:

> avconv -i MOVIE.mkv -map 0:0 -codec:v libx264 -pass 1 -threads 6 -coder:v ac -g 240 -keyint_min 23 -bf:v 16 -b_strategy 2 -b-bias 0 -refs 3 -b:v 11000k -partitions p8x8,b8x8,i8x8,i4x4 -mixed-refs 1 -me_range:v 20 -me_method:v umh -subq 8 -b-pyramid strict -8x8dct 1 -direct-pred 1 -weightb 1 -weightp 2 -deblock 0:0 -an -f rawvideo -y /dev/null **;**

avconv -i MOVIE.mkv -map 0 -map -0:2 -map -0:3 -codec:s copy -codec:v libx264 -pass 2 -threads 6 -coder:v ac -g 240 -keyint_min 23 -bf:v 16 -b_strategy 2 -b-bias 0 -refs 3 -b:v 11000k -partitions p8x8,b8x8,i8x8,i4x4 -mixed-refs 1 -me_range:v 20 -me_method:v umh -subq 8 -b-pyramid strict -8x8dct 1 -direct-pred 1 -weightb 1 -weightp 2 -deblock 0:0 -acodec libvorbis -async 1 -b:a:0 640k -metadata:s:a:0 title="arc Vorbis 640k 5.1" OUTPUT-MOVIE.mkv

I tried to do a 1 pass encode with the second pass command (without the -pass 2 option) for testing purposes and it didn't use more than 1 core (total load of avconv remained ~130%, I assume it's 100% of libx264 plus some processing for the audio). At moments it went up to 70-90% but it never didn't stay at full load, most of the time was spent on ~130%. I've also tried with -threads auto, -threads 0, -threads 4 but no luck.

I'm using the avconv available in Ubuntu 13.10 repositories (I'm on Kubuntu 13.10).

Any suggestions? Any option that could unlock full avconv performance?
Thanks in advance.

---

### Post by filiprino2 on 2014-04-16
Well guys, to anyone whom this can be of interest, if you want to use libx264 with avconv at full throttle (all cores/threads) available you must use the presets and then if you want you can override the selected preset with your own options.

So, the command line ends being like this:

> avconv -i MOVIE.mkv -map 0 -map -0:2 -map -0:3 -codec:s copy -codec:v libx264 -crf 20 **-preset veryslow** -tune film -g 240 -keyint_min 23 -acodec libvorbis -filter_complex 'asyncts=compensate=1:max_comp=500' -b:a:0 640k -metadata:s:a:0 title="arc Vorbis 640k 5.1" OUTPUT-MOVIE.mkv

I've changed to CRF, but that doesn't matter, if you want you can use 2 passes. After the -preset option you could specify any option you want, those options will override the options chosen by the -preset selected. For more information you can read x264 --fullhelp:

> --preset <string>       Use a preset to select encoding settings [medium]
                                  Overridden by user settings.
                                  - ultrafast:
                                    --no-8x8dct --aq-mode 0 --b-adapt 0
                                    --bframes 0 --no-cabac --no-deblock
                                    --no-mbtree --me dia --no-mixed-refs
                                    --partitions none --rc-lookahead 0 --ref 1
                                    --scenecut 0 --subme 0 --trellis 0
                                    --no-weightb --weightp 0
                                  - superfast:
                                    --no-mbtree --me dia --no-mixed-refs
                                    --partitions i8x8,i4x4 --rc-lookahead 0
                                    --ref 1 --subme 1 --trellis 0 --weightp 1
                                  - veryfast:
                                    --no-mixed-refs --rc-lookahead 10
                                    --ref 1 --subme 2 --trellis 0 --weightp 1
                                  - faster:
                                    --no-mixed-refs --rc-lookahead 20
                                    --ref 2 --subme 4 --weightp 1
                                  - fast:
                                    --rc-lookahead 30 --ref 2 --subme 6
                                    --weightp 1
                                  - medium:
                                    Default settings apply.
                                  - slow:
                                    --b-adapt 2 --direct auto --me umh
                                    --rc-lookahead 50 --ref 5 --subme 8
                                  - slower:
                                    --b-adapt 2 --direct auto --me umh
                                    --partitions all --rc-lookahead 60
                                    --ref 8 --subme 9 --trellis 2
                                  - veryslow:
                                    --b-adapt 2 --bframes 8 --direct auto
                                    --me umh --merange 24 --partitions all
                                    --ref 16 --subme 10 --trellis 2
                                    --rc-lookahead 60
                                  - placebo:
                                    --bframes 16 --b-adapt 2 --direct auto
                                    --slow-firstpass --no-fast-pskip
                                    --me tesa --merange 24 --partitions all
                                    --rc-lookahead 60 --ref 16 --subme 11
                                    --trellis 2
      --tune <string>         Tune the settings for a particular type of source
                              or situation
                                  Overridden by user settings.
                                  Multiple tunings are separated by commas.
                                  Only one psy tuning can be used at a time.
                                  - film (psy tuning):
                                    --deblock -1:-1 --psy-rd <unset>:0.15
                                  - animation (psy tuning):
                                    --bframes {+2} --deblock 1:1
                                    --psy-rd 0.4:<unset> --aq-strength 0.6
                                    --ref {Double if >1 else 1}
                                  - grain (psy tuning):
                                    --aq-strength 0.5 --no-dct-decimate
                                    --deadzone-inter 6 --deadzone-intra 6
                                    --deblock -2:-2 --ipratio 1.1 
                                    --pbratio 1.1 --psy-rd <unset>:0.25
                                    --qcomp 0.8
                                  - stillimage (psy tuning):
                                    --aq-strength 1.2 --deblock -3:-3
                                    --psy-rd 2.0:0.7
                                  - psnr (psy tuning):
                                    --aq-mode 0 --no-psy
                                  - ssim (psy tuning):
                                    --aq-mode 2 --no-psy
                                  - fastdecode:
                                    --no-cabac --no-deblock --no-weightb
                                    --weightp 0
                                  - zerolatency:
                                    --bframes 0 --force-cfr --no-mbtree
                                    --sync-lookahead 0 --sliced-threads
                                    --rc-lookahead 0
      --slow-firstpass        Don't force these faster settings with --pass 1:
                                  --no-8x8dct --me dia --partitions none
                                  --ref 1 --subme {2 if >2 else unchanged}
                                  --trellis 0 --fast-pskip


---

### Post by andrew.46 on 2014-04-16
> **filiprino2 said:**
>  Any option that could unlock full avconv performance?

I see that you have found the answer to the threads problem but if you really want full performance from avconv / FFmpeg you would be better to use the most recent git version. Your commandline indicates you are an advanced user and the repository versions represent a snapshot from quite some time ago while avconv / FFmpeg development has been white hot for years...

---

### Post by filiprino2 on 2014-04-17
Hum, yep, it seems so. But I don't like relying on self compiles instead of packages and the latest package available on a PPA is from ffmpeg 0.10 :(

---

### Post by andrew.46 on 2014-04-17
Have a look on the FFmpeg Wiki for a nice page on compiling a local, static FFmpeg and this might be your path...

---

