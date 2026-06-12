---
title: "Convert audio track in MKV to AAC using Nero AAC encoder"
date: 2014-08-13
forum: Multimedia Software
---

### Post by ernstblaauw on 2014-08-13
The problem: I want to convert the audio track of a MKV file (containing audio + video) to AAC using Nero's encoder. How should I do that?

Some background information: I want to convert my DVD's to MKV, so my RPi (running OpenElec) can play the movie (it does not have MPEG2 support out of the box). I use HandBrake for this, but HandBrake does not have very advanced audio encoders; for AAC only ffmpeg is supported.

Therefore, I want to passthrough the audio to the MKV (for example, an AC3 stream) and then convert the audio stream to Nero AAC. 

However, I did not found any solutions. The only solution to me would be:
[LIST]
[*]Split audio and video using ffmpeg
[*]Convert audio using nero aac
[*]Mux the original video and new audio track using ffmpeg
[/LIST]

However, I think this would introduce not synchronized audio and video, as I throw away any delays stored in the original MKV.

So how should I convert the audio track? Is it possible using command line tools?

---

### Post by SeijiSensei on 2014-08-13
You do know that [AAC is a patented technology]("http://www.vialicensing.com/licensing/aac-faq.aspx"), right?  So there won't be any open-source encoders which is why Handbrake doesn't support the format.

Can you really hear the difference between AC3 and AAC?  I know I can't, but my ears are probably older than yours.

---

### Post by ernstblaauw on 2014-08-13
> **SeijiSensei said:**
> You do know that [AAC is a patented technology]("http://www.vialicensing.com/licensing/aac-faq.aspx"), right?  So there won't be any open-source encoders which is why Handbrake doesn't support the format.

Can you really hear the difference between AC3 and AAC?  I know I can't, but my ears are probably older than yours.

Thanks for your reply. Handbrake does support AAC, using ffmpeg.

I believe there is a free (i.e. it does not cost money) AAC encoder from Nero: [http://www.videohelp.com/tools/Nero-AAC-Codec](http://www.videohelp.com/tools/Nero-AAC-Codec)
Alternatively, I could use the 'qaac' encoder using wine or use faac. All three are better than ffmpeg's AAC as far as I know.

The main reason for converting AC3 is that my RPi cannot decode it; I need to encode it to AAC or MP3, I believe. AAC is the only option if you want to keep 5.1, but ffmpeg does not support that. Also, the AAC implementation from ffmpeg is not very good, I read on several sites.

That's the reason I would like to convert the audio track outside Handbrake, so if people have advice for me I would be very grateful.

---

### Post by shantiq on 2014-08-13
HI ernst


[U]you have more control/options with Handbrake from the command line so you can keep your 5.1
[/U]

see here:



```
### Audio Options-----------------------------------------------------------


    -a, --audio <string>    Select audio track(s), separated by commas
                            ("none" for no audio, "1,2,3" for multiple
                             tracks, default: first one).
                            Multiple output tracks can be used for one input.
    **[COLOR=#ff0000]-E, --aencoder <string> [/COLOR]**Audio encoder(s):
                               **[COLOR=#ff0000]faac[/COLOR]**
                               ffaac
                               copy:aac
                               ffac3
                               copy:ac3
                               copy:dts
                               copy:dtshd
                               lame
                               copy:mp3
                               vorbis
                               ffflac
                               ffflac24
                               copy
                            copy:* will passthrough the corresponding
                            audio unmodified to the muxer if it is a
                            supported passthrough audio type.
                            Separated by commas for more than one audio track.
                            (default: faac for mp4, lame for mkv)
        --audio-copy-mask   Set audio codecs that are permitted when the
                <string>    "copy" audio encoder option is specified
                            (aac/ac3/dts/dtshd/mp3, default: all).
                            Separated by commas for multiple allowed options.
        --audio-fallback    Set audio codec to use when it is not possible
                <string>    to copy an audio track without re-encoding.
    -B, --ab <kb/s>         Set audio bitrate(s) (default: depends on the
                            selected codec, mixdown and samplerate)
                            Separated by commas for more than one audio track.
    -Q, --aq <quality>      Set audio quality metric (default: depends on the
                            selected codec)
                            Separated by commas for more than one audio track.
    -C, --ac <compression>  Set audio compression metric (default: depends on the
                            selected codec)
                            Separated by commas for more than one audio track.
    [COLOR=#ff0000]**-6, --mixdown <string>**[/COLOR]  Format(s) for audio downmixing/upmixing:
                               mono
                               left_only
                               right_only
                               stereo
                               dpl1
                               dpl2
                               [COLOR=#ff0000]**5point1**[/COLOR]
                               6point1
                               7point1
                               5_2_lfe
                            Separated by commas for more than one audio track.
                            Defaults:
                               faac             up to dpl2
                               ffaac            up to dpl2
                               ffac3            up to 5point1
                               lame             up to dpl2
                               vorbis           up to dpl2
                               ffflac           up to 7point1
                               ffflac24         up to 7point1
```


so   it will look something like this

```
HandBrakeCLI -i ~/Videos/whateveryourmkviscalled.mkv -o ~/Videos/yournewname.mkv -e ffmpeg2 -w 690 -l 520 -b 2500 **[COLOR=#ff0000]-E faac -6  5point1  -B 448[/COLOR]**

```      check you original ac3 bitrate and enter numbers accordingly

to see all the options run this

```
cd Desktop/ ; HandBrakeCLI -h > HandBrakeCLI.txt
```  and find text file on your desktop EASIER TO READ

it looks thus  see the video options too

```
Syntax: HandBrakeCLI [options] -i <device> -o <file>

### General Handbrake Options------------------------------------------------


    -h, --help              Print help
    -u, --update            Check for updates and exit
    -v, --verbose <#>       Be verbose (optional argument: logging level)
    -Z. --preset <string>   Use a built-in preset. Capitalization matters, and
                            if the preset name has spaces, surround it with
                            double quotation marks
    -z, --preset-list       See a list of available built-in presets
        --no-dvdnav         Do not use dvdnav for reading DVDs


### Source Options-----------------------------------------------------------


    -i, --input <string>    Set input device
    -t, --title <number>    Select a title to encode (0 to scan all titles only,
                            default: 1)
        --min-duration      Set the minimum title duration (in seconds). Shorter
                            titles will not be scanned (default: 10).
        --scan              Scan selected title only.
        --main-feature      Detect and select the main feature title.
    -c, --chapters <string> Select chapters (e.g. "1-3" for chapters
                            1 to 3, or "3" for chapter 3 only,
                            default: all chapters)
        --angle <number>    Select the video angle (DVD or Blu-ray only)
        --previews <#:B>    Select how many preview images are generated,
                            and whether or not they're stored to disk (0 or 1).
                            (default: 10:0)
    --start-at-preview <#>  Start encoding at a given preview.
    --start-at    <unit:#>  Start encoding at a given frame, duration (in seconds),
                            or pts (on a 90kHz clock)
    --stop-at     <unit:#>  Stop encoding at a given frame, duration (in seconds),
                            or pts (on a 90kHz clock)
### Destination Options------------------------------------------------------


    -o, --output <string>   Set output file name
    -f, --format <string>   Set output format (mp4/mkv, default:
                            autodetected from file name)
    -m, --markers           Add chapter markers
    -4, --large-file        Create 64-bit mp4 files that can hold more than 4 GB
                            of data. Note: breaks pre-iOS iPod compatibility.
    -O, --optimize          Optimize mp4 files for HTTP streaming ("fast start")
    -I, --ipod-atom         Mark mp4 files so 5.5G iPods will accept them


### Video Options------------------------------------------------------------


    -e, --encoder <string>  Set video library encoder
                            Options: x264/ffmpeg4/ffmpeg2/theora
                            (default: ffmpeg4)
        --x264-preset       When using x264, selects the x264 preset:
          <string>          ultrafast/superfast/veryfast/faster/fast/
                            medium/slow/slower/veryslow/placebo
        --x264-tune         When using x264, selects the x264 tuning:
          <string>          film/animation/grain/stillimage/psnr/ssim/
                            fastdecode/zerolatency
    -x, --encopts <string>  Specify advanced encoder options in the
                            same style as mencoder (x264 and ffmpeg only):
                            option1=value1:option2=value2
        --h264-profile      When using x264, ensures compliance with the
          <string>          specified H.264 profile:
                            auto/high/main/baseline
        --h264-level        When using x264, ensures compliance with the
          <string>          specified H.264 level:
                            auto/1.0/1b/1.1/1.2/1.3/2.0/2.1/2.2/3.0/3.1/
                            3.2/4.0/4.1/4.2/5.0/5.1/5.2
    -q, --quality <number>  Set video quality
    -b, --vb <kb/s>         Set video bitrate (default: 1000)
    -2, --two-pass          Use two-pass mode
    -T, --turbo             When using 2-pass use "turbo" options on the
                            1st pass to improve speed (only works with x264)
    -r, --rate              Set video framerate (5/10/12/15/23.976/24/25/29.97/30/50/59.94/60)
                            Be aware that not specifying a framerate lets
                            HandBrake preserve a source's time stamps,
                            potentially creating variable framerate video
    --vfr, --cfr, --pfr     Select variable, constant or peak-limited
                            frame rate control. VFR preserves the source
                            timing. CFR makes the output constant rate at
                            the rate given by the -r flag (or the source's
                            average rate if no -r is given). PFR doesn't
                            allow the rate to go over the rate specified
                            with the -r flag but won't change the source
                            timing if it's below that rate.
                            If none of these flags are given, the default
                            is --cfr when -r is given and --vfr otherwise


### Audio Options-----------------------------------------------------------


    -a, --audio <string>    Select audio track(s), separated by commas
                            ("none" for no audio, "1,2,3" for multiple
                             tracks, default: first one).
                            Multiple output tracks can be used for one input.
    -E, --aencoder <string> Audio encoder(s):
                               faac
                               ffaac
                               copy:aac
                               ffac3
                               copy:ac3
                               copy:dts
                               copy:dtshd
                               lame
                               copy:mp3
                               vorbis
                               ffflac
                               ffflac24
                               copy
                            copy:* will passthrough the corresponding
                            audio unmodified to the muxer if it is a
                            supported passthrough audio type.
                            Separated by commas for more than one audio track.
                            (default: faac for mp4, lame for mkv)
        --audio-copy-mask   Set audio codecs that are permitted when the
                <string>    "copy" audio encoder option is specified
                            (aac/ac3/dts/dtshd/mp3, default: all).
                            Separated by commas for multiple allowed options.
        --audio-fallback    Set audio codec to use when it is not possible
                <string>    to copy an audio track without re-encoding.
    -B, --ab <kb/s>         Set audio bitrate(s) (default: depends on the
                            selected codec, mixdown and samplerate)
                            Separated by commas for more than one audio track.
    -Q, --aq <quality>      Set audio quality metric (default: depends on the
                            selected codec)
                            Separated by commas for more than one audio track.
    -C, --ac <compression>  Set audio compression metric (default: depends on the
                            selected codec)
                            Separated by commas for more than one audio track.
    -6, --mixdown <string>  Format(s) for audio downmixing/upmixing:
                               mono
                               left_only
                               right_only
                               stereo
                               dpl1
                               dpl2
                               5point1
                               6point1
                               7point1
                               5_2_lfe
                            Separated by commas for more than one audio track.
                            Defaults:
                               faac             up to dpl2
                               ffaac            up to dpl2
                               ffac3            up to 5point1
                               lame             up to dpl2
                               vorbis           up to dpl2
                               ffflac           up to 7point1
                               ffflac24         up to 7point1
        --normalize-mix     Normalize audio mix levels to prevent clipping.
               <string>     Separated by commas for more than one audio track.
                            0 = Disable Normalization (default)
                            1 = Enable Normalization
    -R, --arate             Set audio samplerate(s) (8/11.025/12/16/22.05/24/32/44.1/48 kHz)
                            Separated by commas for more than one audio track.
    -D, --drc <float>       Apply extra dynamic range compression to the audio,
                            making soft sounds louder. Range is 1.0 to 4.0
                            (too loud), with 1.5 - 2.5 being a useful range.
                            Separated by commas for more than one audio track.
        --gain <float>      Amplify or attenuate audio before encoding.  Does
                            NOT work with audio passthru (copy). Values are in
                            dB.  Negative values attenuate, positive values
                            amplify. A 1 dB difference is barely audible.
        --adither <string>  Apply dithering to the audio before encoding.
                            Separated by commas for more than one audio track.
                            Only supported by some encoders (ffflac).
                            Options:
                               auto (default)
                               none
                               rectangular
                               triangular
                               triangular_hp
                               triangular_ns
    -A, --aname <string>    Audio track name(s),
                            Separated by commas for more than one audio track.


### Picture Settings---------------------------------------------------------


    -w, --width  <number>   Set picture width
    -l, --height <number>   Set picture height
        --crop  <T:B:L:R>   Set cropping values (default: autocrop)
        --loose-crop  <#>   Always crop to a multiple of the modulus
                            Specifies the maximum number of extra pixels
                            which may be cropped (default: 15)
    -Y, --maxHeight   <#>   Set maximum height
    -X, --maxWidth    <#>   Set maximum width
    --strict-anamorphic     Store pixel aspect ratio in video stream
    --loose-anamorphic      Store pixel aspect ratio with specified width
    --custom-anamorphic     Store pixel aspect ratio in video stream and
                            directly control all parameters.
    --display-width         Set the width to scale the actual pixels to
      <number>              at playback, for custom anamorphic.
    --keep-display-aspect   Preserve the source's display aspect ratio
                            when using custom anamorphic
    --pixel-aspect          Set a custom pixel aspect for custom anamorphic
      <PARX:PARY>
                            (--display-width and --pixel-aspect are mutually
                             exclusive and the former will override the latter)
    --itu-par               Use wider, ITU pixel aspect values for loose and
                            custom anamorphic, useful with underscanned sources
    --modulus               Set the number you want the scaled pixel dimensions
      <number>              to divide cleanly by. Does not affect strict
                            anamorphic mode, which is always mod 2 (default: 16)
    -M, --color-matrix      Set the color space signaled by the output
                            Values: 709, pal, ntsc, 601 (same as ntsc)
                            (default: detected from source)


### Filters---------------------------------------------------------


    -d, --deinterlace       Deinterlace video with Libav, yadif or mcdeint
          <fast/slow/slower/bob> or omitted (default settings)
           or
          <YM:FD:MM:QP>     (default 0:-1:-1:1)
    -5, --decomb            Selectively deinterlaces when it detects combing
          <fast/bob> or omitted (default settings)
           or
          <MO:ME:MT:ST:BT:BX:BY:MG:VA:LA:DI:ER:NO:MD:PP:FD>
          (default: 7:2:6:9:80:16:16:10:20:20:4:2:50:24:1:-1)
    -9, --detelecine        Detelecine (ivtc) video with pullup filter
                            Note: this filter drops duplicate frames to
                            restore the pre-telecine framerate, unless you
                            specify a constant framerate (--rate 29.97)
          <L:R:T:B:SB:MP:FD> (default 1:1:4:4:0:0:-1)
    -8, --denoise           Denoise video with hqdn3d filter
          <weak/medium/strong> or omitted (default settings)
           or
          <SL:SC:TL:TC>     (default 4:3:6:4.5)
    -7, --deblock           Deblock video with pp7 filter
          <QP:M>            (default 5:2)
        --rotate            Flips images axes
          <M>               (default 3)
    -g, --grayscale         Grayscale encoding


### Subtitle Options------------------------------------------------------------


    -s, --subtitle <string> Select subtitle track(s), separated by commas
                            More than one output track can be used for one
                            input.
                            Example: "1,2,3" for multiple tracks.
                            A special track name "scan" adds an extra 1st pass.
                            This extra pass scans subtitles matching the
                            language of the first audio or the language 
                            selected by --native-language.
                            The one that's only used 10 percent of the time
                            or less is selected. This should locate subtitles
                            for short foreign language segments. Best used in
                            conjunction with --subtitle-forced.
    -F, --subtitle-forced   Only display subtitles from the selected stream if
          <string>          the subtitle has the forced flag set. The values in
                            "string" are indexes into the subtitle list
                            specified with '--subtitle'.
                            Separated by commas for more than one subtitle track.
                            Example: "1,2,3" for multiple tracks.
                            If "string" is omitted, the first track is forced.
        --subtitle-burned   "Burn" the selected subtitle into the video track
          <number>          If "number" is omitted, the first track is burned.
                            "number" is an index into the subtitle list
                            specified with '--subtitle'.
        --subtitle-default  Flag the selected subtitle as the default subtitle
          <number>          to be displayed upon playback.  Setting no default
                            means no subtitle will be automatically displayed
                            If "number" is omitted, the first track is default.
                            "number" is an index into the subtitle list
                            specified with '--subtitle'.
    -N, --native-language   Specifiy your language preference. When the first
          <string>          audio track does not match your native language then
                            select the first subtitle that does. When used in
                            conjunction with --native-dub the audio track is
                            changed in preference to subtitles. Provide the
                            language's iso639-2 code (fre, eng, spa, dut, et cetera)
        --native-dub        Used in conjunction with --native-language
                            requests that if no audio tracks are selected the
                            default selected audio track will be the first one
                            that matches the --native-language. If there are no
                            matching audio tracks then the first matching
                            subtitle track is used instead.
        --srt-file <string> SubRip SRT filename(s), separated by commas.
        --srt-codeset       Character codeset(s) that the SRT file(s) are
          <string>          encoded in, separated by commas.
                            Use 'iconv -l' for a list of valid
                            codesets. If not specified, 'latin1' is assumed
        --srt-offset        Offset (in milliseconds) to apply to the SRT file(s),
          <string>          separated by commas. If not specified, zero is assumed.
                            Offsets may be negative.
        --srt-lang <string> Language as an iso639-2 code fra, eng, spa et cetera)
                            for the SRT file(s), separated by commas. If not specified,
                            then 'und' is used.
        --srt-default       Flag the selected srt as the default subtitle
          <number>          to be displayed upon playback.  Setting no default
                            means no subtitle will be automatically displayed
                            If "number" is omitted, the first srt is default.
                            "number" is an 1 based index into the srt-file list



```


Hope this helps!


ran it to test and as you see 5.1 all there


```
HandBrakeCLI -i ~/Videos/'Josie and The Pussycats'.mkv -o ~/Videos/Josie.mkv -e ffmpeg2 -w 690 -l 520 -b 2500 -E faac -6  5point1   -B 448[15:57:08] hb_init: starting libhb thread
HandBrake 0.9.9 (2013051800) - Linux x86_64 - http://handbrake.fr
1 CPU detected
Opening /home/shantiq/Videos/Josie and The Pussycats.mkv...
[15:57:08] hb_scan: path=/home/shantiq/Videos/Josie and The Pussycats.mkv, title_index=1
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening /home/shantiq/Videos/Josie and The Pussycats.mkv/BDMV/index.bdmv
libbluray/bdnav/index_parse.c:162: indx_parse(): error opening /home/shantiq/Videos/Josie and The Pussycats.mkv/BDMV/BACKUP/index.bdmv
libbluray/bluray.c:1725: nav_get_title_list(/home/shantiq/Videos/Josie and The Pussycats.mkv) failed (0x7ff258000900)
[15:57:08] bd: not a bd - trying as a stream/file instead
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.13 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
[15:57:08] dvd: not a dvd - trying as a stream/file instead
Input #0, matroska,webm, from '/home/shantiq/Videos/Josie and The Pussycats.mkv':
  Metadata:
    TITLE           : JOSIE_SKU1
  Duration: 01:34:28.16, start: 0.000000, bitrate: N/A
    Chapter #0.0: start 0.000000, end 409.960000
    Metadata:
      title           : Chapter 1
    Chapter #0.1: start 409.960000, end 569.000000
    Metadata:
      title           : Chapter 2
    Chapter #0.2: start 569.000000, end 934.920000
    Metadata:
      title           : Chapter 3
    Chapter #0.3: start 934.920000, end 1225.720000
    Metadata:
      title           : Chapter 4
    Chapter #0.4: start 1225.720000, end 1798.800000
    Metadata:
      title           : Chapter 5
    Chapter #0.5: start 1798.800000, end 2046.040000
    Metadata:
      title           : Chapter 6
    Chapter #0.6: start 2046.040000, end 2196.960000
    Metadata:
      title           : Chapter 7
    Chapter #0.7: start 2196.960000, end 2520.480000
    Metadata:
      title           : Chapter 8
    Chapter #0.8: start 2520.480000, end 2900.720000
    Metadata:
      title           : Chapter 9
    Chapter #0.9: start 2900.720000, end 3079.240000
    Metadata:
      title           : Chapter 10
    Chapter #0.10: start 3079.240000, end 3771.400000
    Metadata:
      title           : Chapter 11
    Chapter #0.11: start 3771.400000, end 4099.200000
    Metadata:
      title           : Chapter 12
    Chapter #0.12: start 4099.200000, end 4318.640000
    Metadata:
      title           : Chapter 13
    Chapter #0.13: start 4318.640000, end 4991.680000
    Metadata:
      title           : Chapter 14
    Chapter #0.14: start 4991.680000, end 5339.160000
    Metadata:
      title           : Chapter 15
    Chapter #0.15: start 5339.160000, end 5668.160000
    Metadata:
      title           : Chapter 16
    Stream #0.0(eng): Video: mpeg4 (Simple Profile), yuv420p, 720x552 [PAR 64:45 DAR 128:69], 25 fps, 25 tbr, 1k tbn, 25 tbc (default)
    Stream #0.1(eng): Audio: ac3, 48000 Hz, 5.1, fltp, 448 kb/s (default)
    Stream #0.2(ita): Subtitle: dvdsub (default)
    Stream #0.3(swe): Subtitle: dvdsub
    Stream #0.4(ger): Subtitle: dvdsub
    Stream #0.5(eng): Subtitle: dvdsub
[15:57:08] scan: decoding previews for title 1
[15:57:08] scan: audio 0x1: AC-3, rate=48000Hz, bitrate=448000 English (AC3) (5.1 ch)
[15:57:08] scan: 10 previews, 720x552, 25.000 fps, autocrop = 0/0/0/0, aspect 16:9, PAR 64:45
[15:57:08] libhb: scan thread found 1 valid title(s)
+ title 1:
  + stream: /home/shantiq/Videos/Josie and The Pussycats.mkv
  + duration: 01:34:28
  + size: 720x552, pixel aspect: 64/45, display aspect: 1.86, 25.000 fps
  + autocrop: 0/0/0/0
  + chapters:
    + 1: cells 0->0, 0 blocks, duration 00:06:50
    + 2: cells 0->0, 0 blocks, duration 00:02:39
    + 3: cells 0->0, 0 blocks, duration 00:06:06
    + 4: cells 0->0, 0 blocks, duration 00:04:51
    + 5: cells 0->0, 0 blocks, duration 00:09:33
    + 6: cells 0->0, 0 blocks, duration 00:04:07
    + 7: cells 0->0, 0 blocks, duration 00:02:31
    + 8: cells 0->0, 0 blocks, duration 00:05:24
    + 9: cells 0->0, 0 blocks, duration 00:06:20
    + 10: cells 0->0, 0 blocks, duration 00:02:59
    + 11: cells 0->0, 0 blocks, duration 00:11:32
    + 12: cells 0->0, 0 blocks, duration 00:05:28
    + 13: cells 0->0, 0 blocks, duration 00:03:39
    + 14: cells 0->0, 0 blocks, duration 00:11:13
    + 15: cells 0->0, 0 blocks, duration 00:05:47
    + 16: cells 0->0, 0 blocks, duration 00:05:29
  + audio tracks:
    + 1, English (AC3) (5.1 ch) (iso639-2: eng), 48000Hz, 448000bps
  + subtitle tracks:
    + 1, Italian (iso639-2: ita) (Bitmap)(VOBSUB)
    + 2, Swedish (iso639-2: swe) (Bitmap)(VOBSUB)
    + 3, German (iso639-2: deu) (Bitmap)(VOBSUB)
    + 4, English (iso639-2: eng) (Bitmap)(VOBSUB)
[15:57:08] 1 job(s) to process
[15:57:08] starting job
[15:57:08] sync: expecting 141704 video frames
[15:57:08] job configuration:
[15:57:08]  * source
[15:57:08]    + /home/shantiq/Videos/Josie and The Pussycats.mkv
[15:57:08]    + title 1, chapter(s) 1 to 16
[15:57:08]    + container: matroska,webm
[15:57:08]  * destination
[15:57:08]    + /home/shantiq/Videos/Josie.mkv
[15:57:08]    + container: Matroska (.mkv)
[15:57:08]  * video track
[15:57:08]    + decoder: mpeg4
[15:57:08]    + frame rate: same as source (around 25.000 fps)
[15:57:08]    + filters
[15:57:08]      + Framerate Shaper (0:27000000:1080000)
[15:57:08]        + frame rate: same as source (around 25.000 fps)
[15:57:08]      + Crop and Scale (690:520:0:0:0:0)
[15:57:08]        + source: 720 * 552, crop (0/0/0/0): 720 * 552, scale: 690 * 520
[15:57:08]    + dimensions: 690 * 520, mod 0
[15:57:08]    + encoder: MPEG-2 (FFmpeg)
[15:57:08]      + bitrate: 2500 kbps, pass: 0
[B][COLOR=#ff0000][15:57:08]  * audio track 1
[15:57:08]    + decoder: English (AC3) (5.1 ch) (track 1, id 0x1)
[15:57:08]      + bitrate: 448 kbps, samplerate: 48000 Hz
[15:57:08]    + mixdown: 5.1 Channels
[15:57:08]    + encoder: AAC (faac)[/COLOR][/B]
[15:57:08]      + bitrate: 448 kbps, samplerate: 48000 Hz
[15:57:08] encavcodecInit: MPEG-2 encoder
[15:57:08] reader: first SCR 0 id 0x1 DTS 0
Encoding: task 1 of 1, 0.30 % (23.13 fps, avg 25.96 fps, ETA 01h30m42s)^Z
[3]+  Stopped 
```

---

### Post by mc4man on 2014-08-13
I believe Hb can use fdkaac  which is as good or better than nero

---

### Post by shantiq on 2014-08-13
hi mc   no audio defaults on my HB   version   0.9.9 (x86_64) on 13.10 which one are you on?  is this a new thing?   nice 


ha [i see]("https://trac.handbrake.fr/browser/trunk/doc/BUILD-Linux")


and enable everything  

>      ./configure --launch --enable-fdk-aac --enable-hwd  --enable-x265 --enable-libav-aac

what do you see under audio options in [COLOR=#000000][FONT=Ubuntu Mono]HandBrakeCLI -h
[/FONT][/COLOR]

so i can improve on the command line and replace

[COLOR=#000000]HandBrakeCLI -i ~/Videos/whateveryourmkviscalled.mkv -o ~/Videos/yournewname.mkv -e ffmpeg2 -w 690 -l 520 -b 2500 **[COLOR=#ff0000]-E faac -6  5point1  -B 448[/COLOR]**[B][COLOR=#ff0000]
[/COLOR][/B]
[/COLOR]
faac for the wunderful [COLOR=#000000]fdkaac and is it there as is or did you have to [add it]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media")[/COLOR]

---

### Post by ernstblaauw on 2014-08-13
> **shantiq said:**
> 
```
### Audio Options-----------------------------------------------------------


    -a, --audio <string>    Select audio track(s), separated by commas
                            ("none" for no audio, "1,2,3" for multiple
                             tracks, default: first one).
                            Multiple output tracks can be used for one input.
    **[COLOR=#ff0000]-E, --aencoder <string> [/COLOR]**Audio encoder(s):
                               **[COLOR=#ff0000]faac[/COLOR]**
                               ffaac
                               copy:aac
                               ffac3
                               copy:ac3
                               copy:dts
                               copy:dtshd
                               lame
                               copy:mp3
                               vorbis
                               ffflac
                               ffflac24
                               copy
                            copy:* will passthrough the corresponding
                            audio unmodified to the muxer if it is a
                            supported passthrough audio type.
                            Separated by commas for more than one audio track.
                            (default: faac for mp4, lame for mkv)
        --audio-copy-mask   Set audio codecs that are permitted when the
                <string>    "copy" audio encoder option is specified
                            (aac/ac3/dts/dtshd/mp3, default: all).
                            Separated by commas for multiple allowed options.
        --audio-fallback    Set audio codec to use when it is not possible
                <string>    to copy an audio track without re-encoding.
    -B, --ab <kb/s>         Set audio bitrate(s) (default: depends on the
                            selected codec, mixdown and samplerate)
                            Separated by commas for more than one audio track.
    -Q, --aq <quality>      Set audio quality metric (default: depends on the
                            selected codec)
                            Separated by commas for more than one audio track.
    -C, --ac <compression>  Set audio compression metric (default: depends on the
                            selected codec)
                            Separated by commas for more than one audio track.
    [COLOR=#ff0000]**-6, --mixdown <string>**[/COLOR]  Format(s) for audio downmixing/upmixing:
                               mono
                               left_only
                               right_only
                               stereo
                               dpl1
                               dpl2
                               [COLOR=#ff0000]**5point1**[/COLOR]
                               6point1
                               7point1
                               5_2_lfe
                            Separated by commas for more than one audio track.
                            Defaults:
                               faac             up to dpl2
                               ffaac            up to dpl2
                               ffac3            up to 5point1
                               lame             up to dpl2
                               vorbis           up to dpl2
                               ffflac           up to 7point1
                               ffflac24         up to 7point1
```


so   it will look something like this

```
HandBrakeCLI -i ~/Videos/whateveryourmkviscalled.mkv -o ~/Videos/yournewname.mkv -e ffmpeg2 -w 690 -l 520 -b 2500 **[COLOR=#ff0000]-E faac -6  5point1  -B 448[/COLOR]**

```      check you original ac3 bitrate and enter numbers accordingly



faac support is not available in 14.04:
[http://changelogs.ubuntu.com/changelogs/pool/universe/h/handbrake/handbrake_0.9.9+dfsg-2~2.gbpa4c3e9/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/h/handbrake/handbrake_0.9.9+dfsg-2~2.gbpa4c3e9/changelog)
Handbrake only supports codecs that are included during compiling, so I believe I cannot use that codec.

> **mc4man said:**
> I believe Hb can use fdkaac  which is as good or better than nero
How can I use fdkaac? By choosing ffmpeg as aac encoder? (ffmpeg has multiple aac encoders and I thought they would use another one).
However, in the front-end 5.1 is grayed out if aac (ffmpeg) is chosen. 

Your interface is different than mine, what is your setup (including Handbrake version)?

---

### Post by shantiq on 2014-08-13
ok simple    run ```
HandBrakeCLI -h
```

find the code for fdkaac   and replace faac in the line i wrote    and it will do what you wish for

it is probably    fdk    or fdkaac    but i cannot see it as i have an earlier version

```
[COLOR=#000000][I]HandBrakeCLI -i ~/Videos/whateveryourmkviscalled.mkv -o ~/Videos/yournewname.mkv -e ffmpeg2 -w 690 -l 520 -b 2500 **[COLOR=#ff0000]-E faac -6  5point1  -B 448[/COLOR]**[B][COLOR=#ff0000]
[/COLOR][/B]
[/I][/COLOR]
```


the greyed-out goes away in command-line of course hence my suggestion of going that way

hope it makes sense

---

### Post by ernstblaauw on 2014-08-13
Ok thanks, will try this if I got the time.

Still I'm curious how I can convert an audio track using the command myself, including correct muxing. Can anyone point me in the right direction?

---

### Post by shantiq on 2014-08-13
mmmm  i thought that was what i had just answered for you :)

---

### Post by ernstblaauw on 2014-08-13
If I understood your posts correctly: you are explaining how I could use Handbrake to encode in more formats, but not how I could use other tools to encode the audio.
Is that correct? Or am I misreading something?

---

### Post by shantiq on 2014-08-13
ok ernst   you asked how to retain the 5.1 on an aac file from an ac3 audio track on an mkv video file

So what i explained was how to do this with HB on the command line where it allows you to do that

i do not think i misunderstood your question altho it is a possibility

If you run the line i wrote and replace faac with whichever code they use for fdkaac   [probably fdk or fdkaac]   then you should end up with what you asked for

ie:  keep the video but convert the ac3 5.1 to m4a or aac 5.1 with the same bitrate

That is what i understood     shan


**And   if you want to **then strip the audio from the video

```
ffmpeg -i video.mkv  -vn  -c:a copy  audioonly.m4a
```

-vn   means video no

---

### Post by SeijiSensei on 2014-08-13
The version of Handbrake that Ubuntu ships does not contain any encumbered technologies.  Indeed it doesn't even support the [MP4 container]("http://ubuntuforums.org/showthread.php?t=2221790") for that reason.  For an unencumbered version, you need to install it from John Stebbins's PPA repository: [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots)

Also the "[encoders]("https://trac.handbrake.fr/wiki/Encoders")" page at Handbrake includes this comment:  "HandBrake does not support external encoders. It is not possible to add an encoder to HandBrake at runtime. All the encoder libraries are built in and not dynamically linked/loaded at runtime."  The version of ffmpeg in HandBrake is [statically compiled with code modifications]("https://trac.handbrake.fr/wiki/SupportFAQ#Development") by the Handbrake team.

---

### Post by ernstblaauw on 2014-08-13
> **shantiq said:**
> ok ernst   you asked how to retain the 5.1 on an aac file from an ac3 audio track on an mkv video file

So what i explained was how to do this with HB on the command line where it allows you to do that

i do not think i misunderstood your question altho it is a possibility

If you run the line i wrote and replace faac with whichever code they use for fdkaac   [probably fdk or fdkaac]   then you should end up with what you asked for

ie:  keep the video but convert the ac3 5.1 to m4a or aac 5.1 with the same bitrate

That is what i understood     shan


**And   if you want to **then strip the audio from the video

```
ffmpeg -i video.mkv  -vn  -c:a copy  audioonly.m4a
```

-vn   means video no

Ok, I did not phrase my question correctly. Of course I want to encode to 5.1 AAC and you showed me a possible solution!
However, I still am interested how I could freely encode / alter the audio track - the main problem for me is the correct muxing and demuxing and I was hoping someone could explain me how to do that. 

> **shantiq said:**
> 

```
HandBrakeCLI -i ~/Videos/whateveryourmkviscalled.mkv -o ~/Videos/yournewname.mkv -e ffmpeg2 -w 690 -l 520 -b 2500 **[COLOR=#ff0000]-E faac -6  5point1  -B 448[/COLOR]**

```    

This command does not work, it exists with 
```
ERROR: Invalid audio codec: 0x100
```
ffaac does work (but then it uses the ffmpeg aac). No other aac encoders are available here.
If I install Stebbins' version, both faac and ffaac lead to the encoder 'AAC (libavcodec)' according to the log file

So, I would still be interested how I can encode the audio track in another program than Handbrake. How I should demux and mux again?

Thanks all for your help!

---

### Post by mc4man on 2014-08-13
> **ernstblaauw said:**
> 
```
ERROR: Invalid audio codec: 0x100
```
ffaac does work (but then it uses the ffmpeg aac). No other aac encoders are available here.
If I install Stebbins' version, both faac and ffaac lead to the encoder 'AAC (libavcodec)' according to the log file

So, I would still be interested how I can encode the audio track in another program than Handbrake. How I should demux and mux again?

Thanks all for your help!

As mentioned only use ppa builds of Hb
I've never used before but what I've noticed about the gui - 
As far as audio seems a little wierd. One way is to set fdk_aac in audio defaults, then go to the audio list tab & click on 'reset defaults'. That will give you what you set. Or maybe just add to the audio list directly...
see screens

---

### Post by shantiq on 2014-08-14
ok ernst   so now i know it is fdk_aac



the line will be

```
[COLOR=#000000][I]HandBrakeCLI -i ~/Videos/whateveryourmkviscalled.mkv -o ~/Videos/yournewname.mkv -e ffmpeg2 -w 690 -l 520 -b 2500 **[COLOR=#ff0000]-E fdk_aac -6  5point1  -B 448[/COLOR]**[B][COLOR=#ff0000]
[/COLOR][/B][/I][/COLOR]
```


other way
[COLOR=#000000][I][B][COLOR=#ff0000]

[/COLOR][/B][/I][/COLOR][COLOR=#000000][I][B]To split video and audio 


[/B][/I]```
time ffmpeg -i input.mkv -vn -c:a libfdk_aac -b:a 256k audio.m4a
```
[[I][B]

and remux


[/B][/I][/COLOR]```
time ffmpeg -i silentvideoinput.mkv -i audioinput.m4a -c copy muxednewvideo.mkv
```[COLOR=#000000][I][B][COLOR=#ff0000]


[/COLOR][/B][/I][/COLOR]

---

### Post by ernstblaauw on 2014-08-14
> **shantiq said:**
> ok ernst   so now i know it is fdk_aac



the line will be

```
[COLOR=#000000][I]HandBrakeCLI -i ~/Videos/whateveryourmkviscalled.mkv -o ~/Videos/yournewname.mkv -e ffmpeg2 -w 690 -l 520 -b 2500 **[COLOR=#ff0000]-E fdk_aac -6  5point1  -B 448[/COLOR]**[B][COLOR=#ff0000]
[/COLOR][/B][/I][/COLOR]
```


other way
[COLOR=#000000][I][B][COLOR=#ff0000]

[/COLOR][/B][/I][/COLOR][COLOR=#000000][I][B]To split video and audio 


[/B][/I]```
time ffmpeg -i input.mkv -vn -c:a libfdk_aac -b:a 256k audio.m4a
```
[[I][B]

and remux


[/B][/I][/COLOR]```
time ffmpeg -i silentvideoinput.mkv -i audioinput.m4a -c copy muxednewvideo.mkv
```[COLOR=#000000][I][B][COLOR=#ff0000]


[/COLOR][/B][/I][/COLOR]

Thanks again for your answer :). I will try this when I get home.
One last question: I don't see any information on delays of the audio stream in the (de)muxing command. Do I have to worry about that? Or is this not an issue with MKV's?

Update:
I found my answer here:
[http://www.kkoncepts.net/blog/fixing-out-sync-audio-and-video-ffmpeg](http://www.kkoncepts.net/blog/fixing-out-sync-audio-and-video-ffmpeg)

---

### Post by ernstblaauw on 2014-08-14
> **SeijiSensei said:**
> The version of Handbrake that Ubuntu ships does not contain any encumbered technologies.  Indeed it doesn't even support the [MP4 container]("http://ubuntuforums.org/showthread.php?t=2221790") for that reason.  For an unencumbered version, you need to install it from John Stebbins's PPA repository: [https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots)

Also the "[encoders]("https://trac.handbrake.fr/wiki/Encoders")" page at Handbrake includes this comment:  "HandBrake does not support external encoders. It is not possible to add an encoder to HandBrake at runtime. All the encoder libraries are built in and not dynamically linked/loaded at runtime."  The version of ffmpeg in HandBrake is [statically compiled with code modifications]("https://trac.handbrake.fr/wiki/SupportFAQ#Development") by the Handbrake team.
It is a shame, but I just found out I did not install Stebbins' build - I was confused by the handbrake (Ubuntu) vs handbrake-gtk (Stebbins) version.

Now, I'm using the correct version and I can use both AAC (FDK) as HE-AAC (FDK). I guess I will be using the HE-AAC version, as that is using more advanced techniques I guess?

---

### Post by mc4man on 2014-08-15
> **ernstblaauw said:**
> It is a shame, but I just found out I did not install Stebbins' build - I was confused by the handbrake (Ubuntu) vs handbrake-gtk (Stebbins) version.

Now, I'm using the correct version and I can use both AAC (FDK) as HE-AAC (FDK). I guess I will be using the HE-AAC version, as that is using more advanced techniques I guess?
HE-AAC is only good for bitrates of 80kbps or less. At bitrates of 96kbps and above, you are just better off using LC-AAC. (AAC (FDK)

---

### Post by andrew.46 on 2014-09-17
> **mc4man said:**
> I believe Hb can use fdkaac  which is as good or better than nero

And interestingly NeroAacEnc has been purged from the nero website.....

---

### Post by shantiq on 2014-09-17
and if you suffer from nostalgia :)  >>>  [ATTACH]256490[/ATTACH]

---

### Post by FakeOutdoorsman on 2014-09-17
Stolen from the [neroaacenc AUR package](https://aur.archlinux.org/packages/neroaacenc/):
[http://ftp6.nero.com/tools/NeroAACCodec-1.5.1.zip](http://ftp6.nero.com/tools/NeroAACCodec-1.5.1.zip)

---

