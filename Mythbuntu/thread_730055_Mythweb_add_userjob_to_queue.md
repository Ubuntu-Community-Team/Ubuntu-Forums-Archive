---
title: "Mythweb add userjob to queue"
date: 2008-03-20
forum: Mythbuntu
---

### Post by kameleon25 on 2008-03-20
I have been messing around with my userjobs the past few days and have finally found a nice compromise in the size/quality (2.2GB for an hour show is ridiculous IMO even for my 750GB drive). My problem is I now have to manually run the userjobs from the command line on each of the older recordings. I was hoping it would be possible to add the job back to the queue and it get processed by the mythbackend. I went into mythweb and found the setting to add a userjob to the queue but it never ran. The job list says it did but there is no way it completed that many jobs in the hour I was at lunch. Is there an easier way than having to do the command line?

I am using the latest mythtv from the repositories (.21) if that helps.

---

### Post by rhpot1991 on 2008-03-20
> **kameleon25 said:**
> I have been messing around with my userjobs the past few days and have finally found a nice compromise in the size/quality (2.2GB for an hour show is ridiculous IMO even for my 750GB drive). My problem is I now have to manually run the userjobs from the command line on each of the older recordings. I was hoping it would be possible to add the job back to the queue and it get processed by the mythbackend. I went into mythweb and found the setting to add a userjob to the queue but it never ran. The job list says it did but there is no way it completed that many jobs in the hour I was at lunch. Is there an easier way than having to do the command line?

I am using the latest mythtv from the repositories (.21) if that helps.

A few things to check:
1.  Did you actually enable the running of the user jobs in mythtv-setup?
2.  When scheduling a recording from your frontend, there is an option to have the user job run on those recordings.  See the last screenshot here: [https://help.ubuntu.com/community/MythExport](https://help.ubuntu.com/community/MythExport)
3.  Check your backend logs to see if anything happened with the user jobs.

---

### Post by kameleon25 on 2008-03-20
Let me clarify. I have all the scheduled recordings doing this automatically now. BUT for those that I missed while I was figuring the proper settings to my liking I was wanting to run the same userjobs on them so I would have uniformity. I have the jobs setup properly for future shows (and a few have already ran properly). As far as the logs showing what happened to the jobs I did add via mythweb it just shows where the job started and litterally one second later it finished. There is no way. lol

---

### Post by nasha on 2008-03-21
kameleon25:
Just curious as to what settings your running for your compromise in size/quality? Im settings up transcoding at the moment, and im tired of messing around getting it right :P

---

### Post by kameleon25 on 2008-03-21
I am running nuvexport with ffmpeg around 2500 video bits and 128 on the audio. I can post my nuvexportrc file if that would help. The only thing is the files are alot CLOSER together in file size but not exact. They range from about 370-410MB per 30 minute show (minus the 10min in commercials so 20 minutes total). I tried mencoder with the "quantisataion" deal but the files for a 30 minute show ranged wildy between 150-ish MB to 680MB and I did not like that. Not that ffmpeg is any "faster" or "better" but it produces more consistant results than mencoder in my tests.Still not perfect. But useable. lol

---

### Post by kameleon25 on 2008-03-25
Just an update. I looked in the mythbackend logs and found the problem. Same as I had before the HD crash.
```
OSPEED was not set, defaulting to 9600 at /usr/local/share/nuvexport/nuv_export/shared_ut
ils.pm line 61
Can't find a valid termcap file at /usr/local/share/nuvexport/nuv_export/shared_utils.pm 
line 61
Compilation failed in require at /usr/local/bin/nuvexport-xvid line 45.
BEGIN failed--compilation aborted at /usr/local/bin/nuvexport-xvid line 45.
```

was the error. The solution is to edit /etc/init.d/myth-backend and add the following lines:
```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/bin/mythbackend
NAME="mythbackend"
DESC="MythTV server"
TERM=vt100
export TERM

```

Just add the last two lines and all will be well.

---

### Post by Kreker on 2008-03-25
can you post you nuvexport conf file and tell me how to set the user job with nuvexport runs @ end of all the new recordings?
thanks

---

### Post by kameleon25 on 2008-03-25
Sure thing. You will need to edit the file to suit your needs but I will try to mark where you need to adjust mostly. Mainly you just need to edit the line:
path = /var/lib/mythtv/videos/converted
to be whatever path you want to save the files to and make sure it exists and is writeable by the mythtv user.
If you want better quality or smaller files you can play with the "v_bitrate    = 2500" line under the Xvid settings. the smaller the number the worse the quality but smaller the file and vise versa.

```
#
# nuvexportrc:
#
#  This file contains the configuration for nuvexport, and should be installed
#    as /etc/nuvexportrc.  You can also copy this file to ~/.nuvexportrc, where
#    nuvexport will look first, if you wish to create settings local to a
#    specific user.
#
#  I try to use this file to document all of the commandline options supported
#    by nuvexport, but it is quite likely that a few slip through here and there
#    unnoticed.  Feel free to poke around in the code for add_arg() calls to see
#    all of the available options.
#

#
#  Anything placed within the <nuvexport> section will be interpreted
#    as a global option.  Use this section for options that don't relate
#    specifically to any particular exporter.
#
<nuvexport>

#
#  Set export_prog to ffmpeg, transcode or mencoder, depending on your
#    preference of program for exports.  This is equivalent to --ffmpeg,
#    --transcode or --mencoder
#
    export_prog=ffmpeg

#
#  Any other parameters set in this file are equivalent to using the equivalent
#    setting as a commandline option.  For boolean options like --deinterlace
#    (--nodeinterlace), use deinterlace=yes (or no, true or false) instead.
#    Actual commandline options will override anything in this file.
#

#
#  Preferred mode -- if you don't set this, nuvexport will ask you what you
#    would like to do.  Use --mode or any of the mode symlinks (like
#    nuvexport-xvid) to override.
#
    mode=xvid

#
#  Setting underscores to yes will convert whitespace in filenames to an
#    underscore character (which some people seem to prefer)
#
    underscores=yes

#
#  Setting require_cutlist to yes will tell nuvexport to show only those
#    recordings that have a cutlist
#
#    require_cutlist=no

#
#  By default, nuvexport picks what it thinks is a good name for your file
#    (doing its best to avoid printing "Untitled" into the filename).  Setting
#    name will let you change the output format of the filename generated by
#    nuvexport.  Even after this formatting, nuvexport will still do some basic
#    replacements to make sure that illegal filename characters (eg. /\:*?<>|)
#    are replaced with a dash (or " with a ').  The following format variables
#    are supported:
#
#    %T   -> Title (show name)
#    %S   -> Subtitle (episode name)
#    %R   -> Description
#    %C   -> Category
#    %U   -> RecGroup
#    %hn  -> Hostname of the machine where the file resides
#    %c   -> Channel:  MythTV chanid
#    %cn  -> Channel:  channum
#    %cc  -> Channel:  callsign
#    %cN  -> Channel:  channel name
#    %y   -> Recording start time:  year, 2 digits
#    %Y   -> Recording start time:  year, 4 digits
#    %n   -> Recording start time:  month
#    %m   -> Recording start time:  month, leading zero
#    %j   -> Recording start time:  day of month
#    %d   -> Recording start time:  day of month, leading zero
#    %g   -> Recording start time:  12-hour hour
#    %G   -> Recording start time:  24-hour hour
#    %h   -> Recording start time:  12-hour hour, with leading zero
#    %H   -> Recording start time:  24-hour hour, with leading zero
#    %i   -> Recording start time:  minutes
#    %s   -> Recording start time:  seconds
#    %a   -> Recording start time:  am/pm
#    %A   -> Recording start time:  AM/PM
#    %ey  -> Recording end time:  year, 2 digits
#    %eY  -> Recording end time:  year, 4 digits
#    %en  -> Recording end time:  month
#    %em  -> Recording end time:  month, leading zero
#    %ej  -> Recording end time:  day of month
#    %ed  -> Recording end time:  day of month, leading zero
#    %eg  -> Recording end time:  12-hour hour
#    %eG  -> Recording end time:  24-hour hour
#    %eh  -> Recording end time:  12-hour hour, with leading zero
#    %eH  -> Recording end time:  24-hour hour, with leading zero
#    %ei  -> Recording end time:  minutes
#    %es  -> Recording end time:  seconds
#    %ea  -> Recording end time:  am/pm
#    %eA  -> Recording end time:  AM/PM
#    %py  -> Program start time:  year, 2 digits
#    %pY  -> Program start time:  year, 4 digits
#    %pn  -> Program start time:  month
#    %pm  -> Program start time:  month, leading zero
#    %pj  -> Program start time:  day of month
#    %pd  -> Program start time:  day of month, leading zero
#    %pg  -> Program start time:  12-hour hour
#    %pG  -> Program start time:  24-hour hour
#    %ph  -> Program start time:  12-hour hour, with leading zero
#    %pH  -> Program start time:  24-hour hour, with leading zero
#    %pi  -> Program start time:  minutes
#    %ps  -> Program start time:  seconds
#    %pa  -> Program start time:  am/pm
#    %pA  -> Program start time:  AM/PM
#    %pey -> Program end time:  year, 2 digits
#    %peY -> Program end time:  year, 4 digits
#    %pen -> Program end time:  month
#    %pem -> Program end time:  month, leading zero
#    %pej -> Program end time:  day of month
#    %ped -> Program end time:  day of month, leading zero
#    %peg -> Program end time:  12-hour hour
#    %peG -> Program end time:  24-hour hour
#    %peh -> Program end time:  12-hour hour, with leading zero
#    %peH -> Program end time:  24-hour hour, with leading zero
#    %pei -> Program end time:  minutes
#    %pes -> Program end time:  seconds
#    %pea -> Program end time:  am/pm
#    %peA -> Program end time:  AM/PM
#    %oy  -> Original Airdate:  year, 2 digits
#    %oY  -> Original Airdate:  year, 4 digits
#    %on  -> Original Airdate:  month
#    %om  -> Original Airdate:  month, leading zero
#    %oj  -> Original Airdate:  day of month
#    %od  -> Original Airdate:  day of month, leading zero#    %f -> full path to the filename
#    %%   -> a literal % character
# ******** Change this if you want to adjust the naming scheme of the file you are encoding**************
    filename=%T-%S_%pY-%pm-%pd-%pH

#
#  By default, nuvexport uses an American-style date to represent showtimes in
#    lists and filenames.  Use --date to override that with the format of your
#    choosing.  See the UnixDate section `perldoc Date::Manip` for formatting
#    options.
#
    date=%m/%d,%i:%Mu_%p

#
#  Nuvexport has the option to crop a percentage of the border of each recording
#  in order to get rid of the unsightly edges of the tv signal.  The default 1.5%
#  approximates the overscan of an average TV, but you can alter this from 0 to
#  5% to fit your preferences.  Please keep in mind that this amount is removed
#  prior to making any aspect conversions like removing black bars from 4:3
#  recordings to make a 16:9 export.
#
    crop_pct = 0

#
#  Alternatively, you can override the general crop_pct to crop a different
#  amount from specific sides of the recording.
#
#   crop_top    = 2
#   crop_right  = 2
#   crop_bottom = 2
#   crop_left   = 2

#
#  You can also override the output aspect ratio.  This is useful in combination
#  with crop_top=12.5 and crop_bottom=12.5 to remove the black bars from the
#  top/bottom of recordings broadcast in fake widescreen.
#
#   out_aspect  = 16:9
#


#
#  Export a matching .txt file, which mythvideo can use to import information
#  about your exports, since it likely can't look them up in imdb.
#
   save_info = yes

#
#  Include recordings from some special recgroups that wouldn't normally be
#  available for export.
#
#   show_deleted = yes
#   show_livetv  = yes

#
#  Uncomment this setting to disable the encode's progress display.  You
#  should really only use this on the commandline for cron/user jobs where
#  you don't want the progress updates to fill up a log or email.
#   
#   noprogress = yes

</nuvexport>

#
#  The sections below work as above, with each more specific section overriding
#    the more generic.
#

<generic>

#
# Default to export to the current directory
#
# *************Change this to the path where you want your videos to be saved once exported.*********
    path = /var/lib/mythtv/videos/converted

#
# Use the cutlist (not to be confused with the commercial flag list) when
#    exporting.
#
    use_cutlist = yes

#
# Tell mythcommflag to generate a cutlist from the commercial flags before
#    exporting.  Don't forget to enable use_cutlist above, too.
#
   gencutlist = yes

#
# Contrary to popular belief, enabling multipass will not make your recordings
#    look better.  What it will do, however is guarantee that the bitrate you
#    choose will be the average bitrate of your entire encode (meaning that your
#    exports will end up being about the same size per-minute), and that you
#    will receive the best overall quality for a files of the same size.
#
    multipass = no

#
# Disabling noise reduction can speed up your exports dramatically, but at the
#    expense of some quality.  For your convenience, this is also aliased on
#    the commandline as --denoise (or --nodenoise), as well as
#    --noise_reduction.
#
    noise_reduction = no

#
# Deinterlace the video so that it looks better on software players.
#
    deinterlace     = yes

#
# Crop about 2% from the border of the recording before encoding.  This is done
#    to get rid of part of the broadcast signal that is usually obscured by the
#    tv's overscan.
#
    crop = no

#
#  You can create settings for each export module type.  These are the
#    second-most generic sections, and will only be reached if there are no
#    matches in the full or generic module names.
#
#  If you have a particularly dirty signal, you might want to try to disable
#    fast_denoise (it's actually part of yuvdenoise, which both the ffmpeg
#    and transcode exporters call).  It can be almost twice as slow as the
#    default "fast" normal noise reduction, but it considerably more effective.
#    The latest version of yuvdenoise (which is called directly by the ffmpeg
#    exporters) does not support this option, so it is ignored in that case.
#
    fast_denoise = no

#
#  If nuvexport is having trouble detecting the *input* aspect ratio of your
#    recordings (MythTV used to hard-code all software-encoded files as 1:1
#    regardless of the true aspect), set this option to one of the following:
#
#   force_aspect = [ 1:1 4:3 16:9 2.21:1 ]

</generic>

<ffmpeg>
#
#  ffmpeg is almost twice as fast if you disable noise reduction
#
   noise_reduction = no
#
#  By default, nuvexport's ffmpeg module lets ffmpeg handle deinterlacing.
#    I've found that this provides the best results, but if you wish to let
#    yuvdenoise do it instead, set deint_in_yuvdenoise to a true value.
#
#    deint_in_yuvdenoise = no
#
</ffmpeg>

<transcode>

#
#  Mythtranscode will always be used for nupplevideo recordings because
#    transcode can't read them, but setting force_mythtranscode to yes will
#    force nuvexport to call mythtranscode when using the transcode exporter for
#    mpeg recordings, too.  This may help problems that some people have been
#    having with transcode not recognizing certain dvb recordings, as well as
#    transcode not working properly on certain ivtv recordings.
#
    force_mythtranscode = yes

#
#  Setting both force_mythtranscode and mythtranscode_cutlist to yes will tell
#    nuvexport to use mythtranscode's built-in cutlist functions, rather than
#    having transcode use its own.  I've found that the cutlists for a handful
#    of ivtv recordings that do not work properly with transcode's internal
#    cutlist handler.
#
    mythtranscode_cutlist = yes

</transcode>

<mencoder>
</mencoder>

################################################################################

#
#  You can also create settings for generic export module names.  These will
#    only be overridden by full module names.
#

<XviD>

    vbr          = yes   # Enable vbr to get the multipass/quantisation options
                         # (enabling multipass or quantisation automatically enables vbr)
    multipass    = yes   # You get either multipass or quantisation; multipass will override
    quantisation = 4     # 4 through 6 is probably right...  1..31 are allowed (lower is better quality)

    a_bitrate    = 128   # Audio bitrate of 128 kbps
    v_bitrate    = 2500   # Remember, quantisation overrides video bitrate

    width        = 720   # Height adjusts automatically to width, according to aspect ratio
    height       = auto

</XviD>

#
#  The mp3 bitrate used by MythTV's software encoder is 128, so there is no
#    real need to go any higher in exports.  You can, of course, turn this up if
#    you get your recordings from other sources.
#
<MP3>
    bitrate = 128
</MP3>

################################################################################

#
#  If you want to provide settings for a very specific export module, you can
#    use its full name, and it will override any more generic settings.
#

#
# The MP4 encoder for ffmpeg has a few options unique to itself
#
<ffmpeg::MP4>

#
#  Codec to use (mpeg4 or h264).  Please note that h264 support requires the
#    SVN version of ffmpeg (not CVS!).  In fact, even the mpeg4 codec works
#    better with the SVN version.
#
#    Note:  The h.264 files exported by nuvexport seem to play fine on ipods,
#    but lack the atom necessary to be recognized by iTunes, so you will have to
#    find other means to get the exports onto your ipod (gtkpod works great).
#
    mp4_codec = h264

#
#  Framerate to use:  auto, 25, 23.97, 29.97.  PAL will always be 25 fps, and
#    auto will set 29.97 for everything over 320x288 and 23.97 for the rest.
#
    mp4_fps = auto

#
#  Enable ipod compatibility mode.  Aside from forcing a max resolution of
#    640x480, this basically just sets motion detection reference frames (-refs)
#    to 2 instead of 7 (the ipod can only handle 2), and thus a small drop in
#    motion detection quality.
#
    ipod = yes

</ffmpeg::MP4>

#
# As does the PSP exporter
#
<ffmpeg::PSP>

# PSP framerate (high=29.97, low=14.985)
    psp_fps = low

# PSP resolution (320x240, 368x208 or 400x192)
    psp_resolution = 320x240

# PSP video bitrate (high=768, low=384)
    psp_bitrate = high

# Create a thumbnail to go with the PSP video export?
    psp_thumbnail = yes

</ffmpeg::PSP>

#
# You can also add flags to the one and only mencoder option
#
<mencoder::XviD>

    multipass = no

</mencoder::XviD>

################################################################################

#
#  You can also make specific profiles called with the --profile parameter that
#    will override other config options (but not commandline arguments).
#
#    For example, you could make a profile that would encode your favorite show
#    with your favorite settings.
#
<profile::sample>

    title       = test

    export_prog = transcode
    mode        = xvid
    confirm     = true

</profile::sample>

#
#  Or crop the black bars off of the top/bottom of fake widescreen shows.
#
<profile::samplewide>

    title       = test

    export_prog = ffmpeg
    mode        = mp4

    out_aspect  = 16:9

    crop_pct    = 0
    crop_top    = 12.5
    crop_bottom = 12.5

    width        = 528
    height       = 360

</profile::samplewide>


```

Beyond that I just added the line:
nuvexport-xvid --nice 8 --input="%FILE%"
to one of the Userjob entries in the backend setup. You can also set it to autorun on every recording. You can set that in mythweb by placing the above line in UserJob1 (or 2, 3, or 4), change the AutoRunUserJob1 (or whatever number you set it in) from 0 to 1, and change the UserJobDesc1 (or again whichever number you used) to reflect whatever you want to name it. I named mine "Xvid convert FFMPEG"

That should get you going. Also add the TERM settings as in my previous post and all should be good.

---

