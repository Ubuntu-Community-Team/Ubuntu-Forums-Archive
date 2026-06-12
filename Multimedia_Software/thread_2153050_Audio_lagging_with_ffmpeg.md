---
title: "Audio lagging with ffmpeg"
date: 2013-06-10
forum: Multimedia Software
---

### Post by Predictability on 2013-06-10
I'm trying to record some touhou gameplay on my laptop, using (from [this]("http://ubuntuforums.org/showthread.php?t=2152811") thread)
```
ffmpeg -f x11grab -framerate 60 -video_size 640x480 -i :0.0+2,23 -f pulse -i default -vcodec libx264 -preset ultrafast -qp 0 -acodec copy [VIDEO].mkv
```
to record and
```
ffmpeg -i [VIDEO].mkv -tune touhou -vcodec libx264 -preset slow -crf 24 -pix_fmt yuv420p -acodec libvorbis -aq 4 [VIDEO].mkv
```
to re-encode (because it's too large otherwise).

It wasn't lagging earlier today, but for some reason now the audio is about 3 seconds after the video.

Can anyone help?

Thanks in advance,
Predictability

---

### Post by andrew.46 on 2013-06-10
Try using the latest git FFmpeg and if this does not solve the issue perhaps experiment with the *itsoffset *option:

```

       -itsoffset offset (input)
           Set the input time offset in seconds.  "[-]hh:mm:ss[.xxx]" syntax is also
           supported.  The offset is added to the timestamps of the input files.
           Specifying a positive offset means that the corresponding streams are delayed
           by offset seconds.

```

What is this btw: *-tune touhou* ?? I have only:

```

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


```

---

### Post by Predictability on 2013-06-10
> **andrew.46 said:**
> Try using the latest git FFmpeg and if this does not solve the issue perhaps experiment with the *itsoffset *option:

```

       -itsoffset offset (input)
           Set the input time offset in seconds.  "[-]hh:mm:ss[.xxx]" syntax is also
           supported.  The offset is added to the timestamps of the input files.
           Specifying a positive offset means that the corresponding streams are delayed
           by offset seconds.

```

What is this btw: *-tune touhou* ?? I have only:

```

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


```


I seemed to have fixed it, it was an option I must have accidentally set in pavucontrol.  Thanks for your help, though.  I'll try using -itsoffset if it's persistent.

[QUOTE=andrew.46]What is this btw: *-tune touhou* ??[/QUOTE]
[QUOTE=en.touhouwiki.net][COLOR=#000000][FONT=sans-serif]There's hidden "tune" value in x264 video codec (free implementation of H.264) that changes codec's settings in the way that gives better quality if used for encoding replays from the [/FONT][/COLOR][Touhou Project]("http://en.touhouwiki.net/wiki/Touhou_Project")[COLOR=#000000][FONT=sans-serif] games (or [/FONT][/COLOR][danmaku]("http://en.touhouwiki.net/wiki/Danmaku")[COLOR=#000000][FONT=sans-serif] in general)[/FONT][/COLOR][/QUOTE][COLOR=#000000][FONT=sans-serif]
[/FONT][/COLOR]

---

### Post by andrew.46 on 2013-06-10
Found it in common.c:

```

        else if( !strncasecmp( s, "touhou", 6 ) )
        {
            if( psy_tuning_used++ ) goto psy_failure;
            param->i_frame_reference = param->i_frame_reference > 1 ? param->i_frame_reference*2 : 1;
            param->i_deblocking_filter_alphac0 = -1;
            param->i_deblocking_filter_beta = -1;
            param->analyse.f_psy_trellis = 0.2;
            param->rc.f_aq_strength = 1.3;
            if( param->analyse.inter & X264_ANALYSE_PSUB16x16 )
                param->analyse.inter |= X264_ANALYSE_PSUB8x8;
        }

```

Thanks for that, I have learnt something new today :)

---

