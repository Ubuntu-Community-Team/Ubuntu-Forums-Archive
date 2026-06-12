---
title: "Idiot transcode question"
date: 2011-01-02
forum: Mythbuntu
---

### Post by nunrgguy on 2011-01-02
On a new 10.10 install, transcode autodetect (btw all transcode jobs were failing until I went in and saved all the settings, no changes just had to save them???), transcode is INCREASING disk usage not decreasing it - 4.9GB becomes 7.2G???
ATM MP4 is setup as per default but doesn't this strike as being rather odd re disk usage?

---

### Post by ian dobson on 2011-01-02
Hi,

Could it be that the transcoder isn't deleting the old files?

Regards
Ian Dobson

---

### Post by nunrgguy on 2011-01-02
Not sure, would mythweb report file size of 7G if that was the case?

---

### Post by nunrgguy on 2011-01-02
Not sure, would mythweb report file size of 7G if that was the case?

---

### Post by ian dobson on 2011-01-02
Hi,

If mythweb is showing a larger size, then transcoding is actually increasing the file size.

Do you see anything interesting in your log files (/var/log/mythtv/)?

Regards
Ian Dobson

---

### Post by nunrgguy on 2011-01-03
Hmm, something very odd, tried a transcode on another file to get a log to check and this time it's transcoded down fine. All I could see really in the log re te other file was some errors re audio and missed frames.

---

### Post by nunrgguy on 2011-01-05
Nope, it's definitely still doing it. file size increases every time:
Backend log



[http://pastebin.com/Y9NdNLc3]("http://pastebin.com/Y9NdNLc3")

---

### Post by ian dobson on 2011-01-05
Hi,

OK, your transcoding to NUV format, NUV was the format that MythTV used to save videos in if the tuner card didn't support hardware encoding. NUV requires almost no CPU for playback (It's just jpeg compressed pictures) but the compression ratio for video is not that good.

Maybe try transcoding to x264 or mpeg4 format, that should reduce the file size alot, but it's really slow.

woops, it looks as if mythtranscode doesn't support many formats:-
```

/usr/bin/mythtranscode <--chanid <channelid>>
        <--starttime <starttime>> <--profile <profile>>
        [options]

        --mpeg2          or -m: Perform MPEG2 to MPEG2 transcode.
        --ostream <type> or -e: Output stream type.  Options: dvd, ps.
        --chanid         or -c: Takes a channel id. REQUIRED
        --starttime      or -s: Takes a starttime for the
                                recording. REQUIRED
        --infile         or -i: Input file (Alternative to -c and -s)
        --outfile        or -o: Output file
        --profile        or -p: Takes a profile number or 'autodetect'
                                recording profile. REQUIRED
        --honorcutlist   or -l: Specifies whether to use the cutlist.
                          Optionally takes a cutlist as an argument
                                when used with --infile.
        --inversecut          : Specifies a list of frames to keep
                                while cutting everything else out.
                                Only works with --infile.
        --allkeys        or -k: Specifies that the output file
                                should be made entirely of keyframes.
        --fifodir        or -f: Directory to write fifos to
                                If --fifodir is specified, 'audout' and 'vidout'
                                will be created in the specified directory
        --fifosync            : Enforce fifo sync
        --buildindex     or -b: Build a new keyframe index
                                (use only if audio and video fifos are read independantly)
        --video               : Specifies that this is not a mythtv recording
                                (must be used with --infile)
        --showprogress        : Display status info to the stdout
        --recorderOptions <OPTIONS>
                        or -ro: Pass a comma-separated list of
                                recordingprofile options to override
                                values in the database.
        --verbose level  or -v: Use '-v help' for level info
        --help           or -h: Prints this help statement.
```

Maybe try playing with the transcoder profiles.

Regards
Ian Dobson

---

### Post by nunrgguy on 2011-01-05
Hmm. OK I'll check it out. It's supposed to be set for mpeg4 though afaik , just the defaults from the install. Nothing has been changed apart from it wouldn't tx at all for a start until I went into them all and clicked through till finish.

---

