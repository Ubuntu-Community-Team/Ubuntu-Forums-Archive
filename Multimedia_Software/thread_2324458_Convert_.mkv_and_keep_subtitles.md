---
title: "Convert .mkv and keep subtitles"
date: 2016-05-14
forum: Multimedia Software
---

### Post by John Jason Jordan on 2016-05-14
Xubuntu 14.04, up to date.

I have an .mkv file of a video in a language that I do not speak. The video includes optional (not burned in) subtitles in English, which are vobsub. It plays just fine in VLC (no error messages). The file is 6.6 GB and I wish to shrink it to about 1 GB. Normally I would do this in Handbrake, but Handbrake will not open the file; that is, it appears to open it, but the GUI still says New Video and it clearly has not imported the file. 

I can successfully convert it to a new .mkv with mkvmerge-gui, but the subtitles get stripped out of the output file. This, in spite of the fact that the subs are listed as vobsub in mkvmerge-gui. I tried Arista, but again the subtitles get stripped out. Ditto for winff. I also tried Avidemux, but Avidemux will apparently only encode subs if they are in a separate file. I have DVD:rip, but I have never figured out how to use it.

I need some suggestions. I'll try anything.

---

### Post by shantiq on 2016-05-14
&#10122; have you tried handbrake from CLI   sometimes it might fly this way and not GUI

example of syntax:

```
 HandBrakeCLI -i inputfile.mkv -o outfile.mkv -e ffmpeg4 -b 3000 -E ac3 -B 192 -r 30 -s 1,2,3 --subtitle-default 2
```

from   ```
HandBrakeCLI -h
```



```
### Subtitle Options------------------------------------------------------

      --subtitle-lang-list Specifiy a comma separated list of subtitle
          <string>         languages you would like to select from the
                           source title. By default, the first subtitle
                           matching each language will be added to your
                           output. Provide the language's iso639-2 code
                           (fre, eng, spa, dut, et cetera)
      --all-subtitles      Select all subtitle tracks matching languages in
                           the specified language list
                           (--subtitle-lang-list).
                           Any language if list is not specified.
      --first-subtitle     Select first subtitle track matching languages in
                           the specified language list
                           (--subtitle-lang-list).
                           Any language if list is not specified.
  -s, --subtitle <string>  Select subtitle track(s), separated by commas
                           More than one output track can be used for one
                           input. "none" for no subtitles.
                           Example: "1,2,3" for multiple tracks.
                           A special track name "scan" adds an extra 1st
                           pass. This extra pass scans subtitles matching
                           the language of the first audio or the language 
                           selected by --native-language.
                           The one that's only used 10 percent of the time
                           or less is selected. This should locate subtitles
                           for short foreign language segments. Best used in
                           conjunction with --subtitle-forced.
  -F, --subtitle-forced    Only display subtitles from the selected stream
        <string>           if the subtitle has the forced flag set. The
                           values in "string" are indexes into the
                           subtitle list specified with '--subtitle'.
                           Separate tracks by commas.
                           Example: "1,2,3" for multiple tracks.
                           If "string" is omitted, the first track is
                           forced.
      --subtitle-burned    "Burn" the selected subtitle into the video
        <subtitle>         track. If "subtitle" is omitted, the first
                           track is burned. "subtitle" is an index into
                           the subtitle list specified with '--subtitle'
                           or "native" to burn the subtitle track that may
                           be added by the 'native-language' option.
      --subtitle-default   Flag the selected subtitle as the default
        <number>           subtitle to be displayed upon playback.  Setting
                           no default means no subtitle will be displayed
                           automatically. "number" is an index into the
                           subtitle list specified with '--subtitle'.
  -N, --native-language    Specifiy your language preference. When the first
      <string>             audio track does not match your native language
                           then select the first subtitle that does. When
                           used in conjunction with --native-dub the audio
                           track is changed in preference to subtitles.
                           Provide the language's iso639-2 code:
                               (fre, eng, spa, dut, et cetera)
      --native-dub         Used in conjunction with --native-language
                           requests that if no audio tracks are selected the
                           default selected audio track will be the first
                           one that matches the --native-language. If there
                           are no matching audio tracks then the first
                           matching subtitle track is used instead.
     --srt-file <string>   SubRip SRT filename(s), separated by commas.
     --srt-codeset         Character codeset(s) that the SRT file(s) are
       <string>            encoded in, separated by commas.
                           Use 'iconv -l' for a list of valid
                           codesets. If not specified, 'latin1' is assumed
     --srt-offset          Offset (in milliseconds) to apply to the SRT
       <string>            file(s), separated by commas. If not specified,
                           zero is assumed. Offsets may be negative.
     --srt-lang <string>   SRT track language as an iso639-2 code:
                               (fre, eng, spa, dut, et cetera)
                           Separated by commas. If not specified, then 'und'
                           is used.
     --srt-default         Flag the selected srt as the default subtitle
       <number>            to be displayed upon playback. Setting no default
                           means no subtitle will be automatically displayed
                           If "number" is omitted, the first SRT is the
                           default. "number" is an 1 based index into the
                           'srt-file' list
     --srt-burn            "Burn" the selected SRT subtitle into the
       <number>            video track. If "number" is omitted, the first
                           SRT is burned. "number" is an 1 based index
                           into the 'srt-file' list


```



**&#10123; second route**

using CLI mkvextract  

> sudo apt-get install mkvtoolnix

mkvmerge -i MovieFile.mkv
You&#8217;ll see a listing similar to this:

File 'MovieFile.mkv': container: Matroska
Track ID 1: subtitles (S_TEXT/ASS)
Track ID 2: audio (A_MPEG/L3)
Track ID 3: video (V_MPEG4/ISO/AVC)
[B]Next, use mkvextract to extract certain tracks / attachments based on the output from the above command:

mkvextract tracks yourfile.mkv 3:chinese.srt
2:theaudio.mp3 3:thevideo.mkv[/B]




and to add sub default

mkvmerge -o <output>.mkv --default-track 0 --language 0:<language> <subtitles>.srt <input> [replace --forced-track]
mkvmerge -o <output>.mkv --default-track 0 --language 0:eng <subtitles>.srt <input>

You can list the language codes by invoking mkvmerge with the --list-languages (e.g. eng for English, ger for German) parameter. The --default-track parameter just sets the newly muxed subtitles as default for the player to use. If you are muxing multiple subtitles, you of course have to change the language code preceding number.

---

### Post by John Jason Jordan on 2016-05-14
Thanks for the suggestions. 

I couldn't get the HandBrakeCLI code to work - too complicated for me unless I spent a long time studying it. But 'mkvextract tracks yourfile.mkv 3:chinese.srt' worked to extract the subs. The mkvmerge -i command found that there was both a .sub and an .srt file in the video, so first I extracted the .srt. I had a copy of the video (sans subs) that I had previously re-encoded with the mkvmerge-gui, and I knew that HandBrake would open it properly. So I used HandBrake to re-encode it with the .srt file, but HandBrake failed to add the subs. I opened the .srt file in aegisub, which bitched that the encoding was unknown - so that is probably why HandBrake failed to include them.

Then I went back to mkvextract and used it to extract the .sub and .idx files. These work fine, except that HandBrake cannot add .idx/.sub files, so I will have to add them manually in VLC.  This is not a problem, so I am calling the problem solved. And in the future I am going to user mkvmerge more and more, with the goal of learning it better.

Thanks again for your suggestions!

---

### Post by shantiq on 2016-05-15
ok so   now to complete you can mux soundless vid and newly extracted srt :]

```
 mkvmerge -o videowithsrt.mkv  yoursoundlessmkv.mkv --default-track 0 --language 0:eng yourextractedsrt.srt
```



PS set to --default-track   will mean you can toggle it off with v key

---

