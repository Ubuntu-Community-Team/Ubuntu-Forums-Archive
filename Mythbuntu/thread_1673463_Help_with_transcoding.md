---
title: "Help with transcoding"
date: 2011-01-22
forum: Mythbuntu
---

### Post by bcg30506 on 2011-01-22
I have a large number of archived recordings on my backend that I'd like to keep for later viewing but would also like to reduce in size to save disk space while preserving quality as much as possible.

I've written the following script that transcodes a video to x264 that seems to give good results.  However, it is run from the terminal and produces a file that is not in the recordings database.  I'd like to somehow incorporate this into mythfrontend so I can select it in job options for a recording and have it "replace" the original recording with this smaller one.

Questions: How do I do the above?  Can the internal recording player handle this type of file?  How can I save a backup of the original format recording file before transcoding so if something goes wrong I don't lose the show?

Thanks.
```
ffmpeg -i "$1" -y -f mp4 -vcodec libx264 -crf 28 -threads 0 -flags +loop -cmp +chroma -deblockalpha -1 -deblockbeta -1 -refs 3 -bf 3 -coder 1 -me_method hex -me_range 18 -subq 7 -partitions +parti4x4+parti8x8+partp8x8+partb8x8 -g 320 -keyint_min 25 -level 41 -qmin 10 -qmax 51 -qcomp 0.7 -trellis 1 -sc_threshold 40 -i_qfactor 0.71 -flags2 +mixed_refs+dct8x8+wpred+bpyramid -padcolor 000000 -padtop 0 -padbottom 0 -padleft 0 -padright 0 -acodec libfaac -ab 80kb -ar 48000 -ac 2 $2.mp4
```

---

### Post by FakeOutdoorsman on 2011-01-22
I don't know anything about mythfrontend, but your FFmpeg command is outdated. It's recommended to use presets when encoding with x264.  Especially if you occasionally update x264 and FFmpeg because there is a chance that the options will change or new ones might get added.
```
ffmpeg -i "$1" -vcodec libx264 -vpre medium -crf 28 -threads 0 -acodec libfaac -aq 100 -ac 2 -f mp4 "$2".mp4
```
You might have to change "medium" to "normal" if you're using an old FFmpeg. See [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for more info.

---

### Post by bcg30506 on 2011-01-22
Thanks for the tip on ffmpeg.  Now, does anyone know how to incorporate this into the "Job Options" transcoding menu in mythfrontend?  Or what are the transcoder settings I can set for medium quality in setup that will mimic the quality & size output of my ffmpeg command?

---

### Post by bcg30506 on 2011-01-24
Okay, I have my job setup as a User Job in the frontend recording context menu and am getting good size/quality results of the video file.  However, mythfrontend says there is no seek table so I cannot FF/Rew very well and cannot take screen shots or set bookmarks, etc.  I did run mythcommflag on it as part of my script.  The files were transcoded from the original mpeg2 recordings to mp4 x264 files using 2-pass ffmpeg.

2 questions:

1. How can I get a seektable correct for the transcoded recordings if mythcommflag doesn't appear to be doing it, even though it runs with no error?

2. I looked at the built-in Transcoder profiles and the options I can set and gave it a try.  The resulting file is roughly the same size but has a good seektable and looks very blocky when played.  Not nearly the same quality as ffmpeg.  Is it recommended to use mythfrontend's transcoders and if so, what settings will save space and still look close to the original quality?

Thanks.

---

### Post by bcg30506 on 2011-01-25
Playing around a bit more with the built-in transcoders and have been adjusting the Medium quality settings.  I have it set now to 2250 bitrate MPEG2->MPEG4, with adjust for pixel size checked, motion checked, and high quality checked.  It looks pretty good and close the the x264 ffmpeg transcodes, only they are about twice the size.

I'm not sure how to set the sound.  Right now I've got it at MP3 at 44100, quality of 2 and volume of 96.  What does volume do for the transcoder?

Lastly, the results play well and can FF/Rew and even be edited by the internal player.  What format are they?  I know it says MPEG4 but they are .nuv files.  How is this different than what ffmpeg can generate with libx264?

---

### Post by BicyclerBoy on 2011-01-25
.nuv is a nuppelvideo container. It can contain mpeg4 & RTjpeg.

I'm not sure what mpeg4 layer can be used or is used but based on the "time", guess it is a mpeg-4 layer2 ASP.
You can check with ffmpeg -i recording.mpg or mediainfo..

X264 app is an encoder for mpeg4 layer 10 H264-AVC.
Would think an H264 encoded file could be half the size at same quality as ASP.
Theoretically .nuv could contain mpeg4 layer 10 but mythtv does not have the encoder setup.

mythcommflag & mythtranscode can be used to manually repair/create seektables..
see the mythtv wiki..
AFAIK The container has a big effect on seeking. I have found .mkv to be very good.

Note: you can enable auto-seektable creation for DVD playback as well (deleted after 1 week).

---

### Post by bcg30506 on 2011-01-25
Thanks for the info, BicyclerBoy.  I knew about mythcommflag and mythtranscode, however, neither work to fix a seektable for ffmpeg transcoded x264 mp4 files.  I tried transcoding them into a mkv container and mythfrontend still says no seektable after running mythcommflag.

This is why I started looking at the mythtranscode internal profiles to see how they perform.  I like the extra space saving of x264 but don't want to lose all the features of my recordings playing in the internal player.

I'm attaching my scripts that do the user job for review and maybe to help someone else.  Please give me feedback on how they might be changed to make the seektable work as x264 but still give good quality per size.

---

### Post by BicyclerBoy on 2011-01-25
AFAIK A seektable can only be created for recordings imported into the mythtv database.
This includes recordings, DVD playback & videos storage group (after scan updates).
So all I can suggest is that the transcoded recording neesd to be imported first & then seek-table fixed.

I have never used x264 encoder with MythTV internal transcode because:
-   didn't think you could
-  All my recordings are H264.
-  Lossless transcode cutlists do not work with mpeg4/10 H264.
-  can only transcode to mpeg2 & cut-lists do not work.

So external tools only..
I have .mkv videos using H264AVC (Handbrake x264) that seek fine.
I don't create seek-tables for any videos..

DVD playback seek-tables allow you to book-mark & exit to watch something else.

Your script cmd mythcomflag has two -rebuild options ?
Maybe mythcomflag & mythtranscode do not understand mpeg4/10 key frames.
Mythtranscode appears to only work with mpeg2.
I have never seen mythcomflag work (H264).

Why de-interlace ?
This reduces picture quality at the same bit rate.
A well configured video playback setup makes interlaced video impossible to detect.
e.g. vdpau  2x de-interlace VA feasture set C hq scaling etc

---

### Post by bcg30506 on 2011-01-25
Thanks.  I don't think I'm explaining something correctly.  These are recordings made by mythbackend and are all in MPEG-2 format.  I first cut commericals and do a lossless MPEG-2 transcode in mythfrontend so I'm left with only the show I wish to keep in its original recording format sans commercials.

Then I run my User Job on them consisting of the scripts attached in my earlier reply.  These transcode the MPEG2 to x264 using ffmpeg (also tried Handbrake and it was a disaster), updates the recorded table to update the basename and filesize, then runs mythcommflag to rebuild the seektable (also tried it where I just delete the recordedseek table entries for the recording).

This leaves me with a "recording" in H264/MPEG-4 format presumably that the internal player plays.  However, FF/Rew are a little hit-or-miss and if I try to edit or set a bookmark, it says 'no seektable' even though mythcommflag ran with no error codes.

So I tried the mythtranscode job at medium quality which goes from MPEG-2 to MPEG-4 but stores into a Nuppelvideo file and the quality isn't as good unless I crank the size up.  However, these files play, seek, edit, and bookmark fine.

I hope this makes sense, and thanks for the help.

---

### Post by BicyclerBoy on 2011-01-25
Okay
My H264 recordings are mpeg2-ts not mpeg2-ps & not mpeg4 containers.
The mpeg2-ts can have mpeg1,2,4/10 video. 
I have never been able to try any commflag lossless transcoding.

The .nuv file generated is mpeg4 ASP so is bigger.

It could well be that recordings (with seektable) must be mpeg2-ts or nuv container only.
Put your transcodes into videos..

MythTV HD transcoding is in a half working state as a new approach is on the horizon.

Any clues in these scripts (developer)
[http://www.mythtv.org/wiki/User:Iamlindoro](http://www.mythtv.org/wiki/User:Iamlindoro)

AFAIK This script is a basis for the new approach where MythTV will externalize all transcoding operations.

---

### Post by bcg30506 on 2011-01-26
Okay, first off, thanks to everyone for their help thus far and to the myth development team for giving us such an awesome free Tivo replacement plus etc.

Also, this will be a long post as I am pasting the scripts directly instead of attaching a zip file for clarity in helping others hopefully.  I've made some good progress and am very close to being fully satisfied with my solution.

A little background:  I need to keep these recordings as recordings even after transcoding for clear use and ease of use for my wife.  Videos are where we store our home camcorder videos and anything ripped from DVD or online like YouTube.  Recordings are for TV.  She lets me experiment with the living room setup, so I'm not gonna rock the boat on that issue. ;)

I ended up using Handbrake in my script and it mostly gives good results.  The only problem I have now is it is changing the frame size of my videos.  In reading it seems it auto removes black borders, but I don't want it to.  I'm not sure how to prevent this.  Does someone know?  From their manual:
```
--crop: controls the cropping values.
The cropping has to be in the form Top:Bottom:Left:Right, so to crop 60pixels from the top, 58 from the bottom, 2 from the left, and 6 from the right, use --crop 60:58:2:6 ...
do note that this is different from cropping in some other programs, like MEncoder.
If you don't enter this setting, HandBrake will automatically detect how many pixels to crop to remove black borders.
```
I'm sure it has something to do with that but I have no idea how to set it to tell it don't crop anything.

Using the scripts pasted below, I am transcoding MPEG2 recordings into MKV files containing H264 videos at very little quality loss and about a 2.5:1 space savings.  They play fine in the Internal player and I can FF and Rew.  The only things that do not work are Edit Recording, which is no biggie since I cut commercials BEFORE transcoding using lossless MPEG2 in mythfrontend, and generating a thumbnail from a bookmark, which I've solved with another script shown below.

So with no further delay, here are the scripts and user job to make it all happen.  If anyone finds it useful, please let me know.  If someone has an answer about preventing cropping so my videos are the same resolution as before using Handbrake, also please reply with it.  Thanks!

User job command & description:
[PHP]/usr/local/bin/transcode_mp4 -f %FILE%
Convert to small HD quality[/PHP]
Parent script (place in /usr/local/bin):
[PHP]#!/usr/bin/perl -w
# ============================================================================
# = NAME
# copy_and_transcode.pl
#
# = PURPOSE
# Copy a recording before transcoding, so the user can re-cut the original
#
# = USAGE
my $usage = 'Usage:
copy_and_transcode.pl -f %FILE% -p autodetect
copy_and_transcode.pl -j %JOBID% -p autodetect
copy_and_transcode.pl --file file [--debug] [--noaction]  [transcode-arguments]
';
# The first two forms would invoke this as a MythTV User Job
#
# = DESCRIPTION
# The existing mythtranscode system is designed for replacing a recording
# with a transcoded copy. There is a setting which causes the backend to
# keep the original file, but both the seektable and the cutlist are deleted.
# If you are using transcode to extract multiple clips from a recording,
# this is very inconvenient.
#
# This script transcodes a recording into a new recording,
# with a trivially different starttime.
# If the original recording had a cutlist, that should be honoured in the copy.
#
# = INSTALLATION
# Copy this script to a known location, and then add the command
# in mythtv-setup as a User Job (pg. 7 & 9 of General button) e.g.
#
# cp copy_and_transcode.pl /usr/local/bin
# UserJob1     /usr/local/bin/copy_and_transcode.pl -f %FILE% -p autodetect
# UserJobDesc1 Copy and Transcode
#
# = Original AUTHOR
# Nigel Pearson
# ============================================================================

use strict;
use MythTV;

# What file are we copying/transcoding?
my $file  = '';
my $jobid = -1;

# do nothing?
my $noexec = 0;

# extra console output?
my $DEBUG = 1;

# some globals
my ($chanid, $command, $query, $ref, $starttime);
my ($newfilename, $newstarttime);

my $mt = new MythTV();
my $db = $mt->{'dbh'};


# ============================================================================
sub Die($)
{
   print STDERR "@_\n";
   exit -1;
}
# ============================================================================
# Parse command-line arguments, check there is something to do:
#
if ( ! @ARGV )
{   Die "$usage"  }

while ( @ARGV && $ARGV[0] =~ m/^-/ )
{
    my $arg = shift @ARGV;

    if ( $arg eq '-d' || $arg eq '--debug' )
    {   $DEBUG = 1  }
    elsif ( $arg eq '-n' || $arg eq '--noaction' )
    {   $noexec = 1  }
    elsif ( $arg eq '-j' || $arg eq '--jobid' )
    {   $jobid = shift @ARGV  }
    elsif ( $arg eq '-f' || $arg eq '--file' )
    {   $file = shift @ARGV  }
    else
    {
        unshift @ARGV, $arg;
        last;
    }
}

if ( ! $file && $jobid == -1 )
{
    print "No file or job specified. $usage";
    exit;
}

if ( $noexec )
{   print "NoExecute mode. No transcoding or SQL database changes.\n"  }

# ============================================================================
# If we were supplied a jobid, lookup chanid
# and starttime so that we can find the filename
#
if ( $jobid != -1 )
{
    $query = $db->prepare("SELECT chanid, starttime " .
                          "FROM jobqueue WHERE id=$jobid;");
    $query->execute || Die "Unable to query jobqueue table";
    $ref       = $query->fetchrow_hashref;
    $chanid    = $ref->{'chanid'};
    $starttime = $ref->{'starttime'};
    $query->finish;

    if ( ! $chanid || ! $starttime )
    {   Die "Cannot find details for job $jobid"  }

    $query = $db->prepare("SELECT basename FROM recorded " .
                          "WHERE chanid=$chanid AND starttime='$starttime';");
    $query->execute || Die "Unable to query recorded table";
    ($file) = $query->fetchrow_array; 
    $query->finish; 

    if ( ! $file )
    {   Die "Cannot find recording for chan $chanid, starttime $starttime"  }

    if ( $DEBUG )
    {
        print "Job $jobid refers to recording chanid=$chanid,",
              " starttime=$starttime\n"
    }
}
else
{
    if ( $file =~ m/(\d+)_(\d\d\d\d)(\d\d)(\d\d)(\d\d)(\d\d)(\d\d)/ )
    {   $chanid = $1, $starttime = "$2-$3-$4 $5:$6:$7"  }
    else
    {
        print "File $file has a strange name. Searching in recorded table\n";
        $query = $db->prepare("SELECT chanid, starttime " .
                              "FROM recorded WHERE basename='$file';");
        $query->execute || Die "Unable to query recorded table";
        ($chanid,$starttime) = $query->fetchrow_array;
        $query->finish;

        if ( ! $chanid || ! $starttime )
        {   Die "Cannot find details for filename $file"  }
    }
}

# A commonly used SQL row selector:
my $whereChanAndStarttime = "WHERE chanid=$chanid AND starttime='$starttime'";

# ============================================================================
# Find the directory that contains the recordings, check the file exists
#

my $dir  = undef;
my $dirs = $mt->{'video_dirs'};

foreach my $d ( @$dirs )
{
    if ( ! -e $d )
    {   Die "Cannot find directory $dir that contains recordings"  }

    if ( -e "$d/$file" )
    {
        $dir = $d;
        #print "$d/$file exists\n";
        last
    }
    else
    {   print "$d/$file does not exist\n"   }
}

if ( ! $dir )
{   Die "Cannot find recording"  }

# ============================================================================
# Do the transcode
#
$newfilename = $file;
$newfilename =~ s/mpg/mkv/;

$command = "2x264 '$dir/$file' '$dir/$newfilename'";

if ( $DEBUG || $noexec )
{   print "# $command\n"  }

if ( ! $noexec )
{
    chdir $dir;
    system $command;

    if ( ! -e "$newfilename" )
    {   Die "Transcode failed\n"  }
}

if ( $DEBUG && ! $noexec )
{
    print 'Old file size = ' . (-s "$dir/$file")        . "\n";
    print 'New file size = ' . (-s "$dir/$newfilename") . "\n";
}

# ============================================================================
# Last, copy the existing recorded details with the new file name.
#
$query = $db->prepare("SELECT * FROM recorded $whereChanAndStarttime;");
$query->execute || Die "Unable to query recorded table";
$ref = $query->fetchrow_hashref;
$query->finish;

my $filesize = -s "$dir/$newfilename";
$command = "UPDATE recorded SET basename='$newfilename', filesize='$filesize' $whereChanAndStarttime;";

if ( $DEBUG || $noexec )
{   print "# $command\n"  }

if ( ! $noexec )
{   $db->do($command)  || Die "Couldn't update recording's record"   }

# Update the seek table
$command = "mythcommflag --rebuild -c $chanid -s '$starttime' --rebuild";
print "# $command\n";
system $command;

# Just delete the seek table
# $command = "delete from recordedseek $whereChanAndStarttime;";
# if ( $DEBUG || $noexec )
# {   print "# $command\n"  }
# if ( ! $noexec )
# {   $db->do($command)  || Die "Couldn't update recording's record"   }

$db->disconnect;

# rename old file
$command = "rename 's/mpg/old/' '$dir/$file'";
system $command;

# rename thumbnail
$command = "rename 's/mpg/mkv/' '$dir/$file.png'";
system $command;

# touch thumbnail
$command = "touch '$dir/$newfilename.png'";
system $command;
1;[/PHP]
Child script to do xcode (place in /usr/local/bin):
[PHP]#!/bin/bash
HandBrakeCLI -i "$1" -o "$2" -f mkv -e x264 -b 2200 -E faac -B 192 -R 48 -d slow -5 -8 medium[/PHP]
BASH script to make a thumbnail from a timestamp in the video:
(put anywhere and run from a terminal while in recordings dir)
[PHP]#!/bin/bash
ffmpeg -y -i $1 -vframes 1 -ss $2 -an -s 320x180 $1.png[/PHP]
And finally, the results as reported by ffmpeg -i on the original recording and the transcoded one.  This also shows the resize/crop that handbrake did without my wanting it to.
```
original:
Input #0, mpeg, from '1046_20090501170000.mpg':
  Duration: 00:41:06.12, start: 0.360000, bitrate: 4973 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 6000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s

transcoded:
Input #0, matroska, from '1046_20090501170000.mkv':
  Duration: 00:41:06.01, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 704x384, PAR 1:1 DAR 11:6, 29.97 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
```

---

### Post by bcg30506 on 2011-01-26
I think I figured out my cropping issue with Handbrake and what's more, thanks to a nifty background in scripting and Unix shell programming, I adapted by 2x264 script from the above post to now always match the original video pixel dimensions.

Here is the updated script:
[PHP]#!/bin/bash
HandBrakeCLI -i "$1" -o "$2" -f mkv -e x264 -b 2200 -E faac -B 192 -R 48 -d slow -5 -8 medium --crop 0:0:0:0 `ffmpeg -i "$1" 2>&1 1>/dev/null | grep Video: | awk '{print $6}' | awk 'BEGIN{FS="x"}{print "--width "$1" --height "$2}' | sed 's/,*$//'`[/PHP]
So you can see I've added the --crop 0:0:0:0 parameter as well as forcing the width and height to match the input.  These numbers are gotten from running ffmpeg -i on the input file and then thru some scripting magic (I love awk) are outputted in the correct format.

Here is a sample run I did echoing the command output for verficiation:
```
2x264 1046_20110121072359.mpg output-nocrop.mkv

command echo:
HandBrakeCLI -i 1046_20110121072359.mpg -o output-nocrop.mkv -f mkv -e x264 -b 2200 -E faac -B 192 -R 48 -d slow -5 -8 medium --crop 0:0:0:0 --width 720 --height 480
```
ffmpeg info for input file:
```
Input #0, mpeg, from '1046_20110121072359.mpg':
  Duration: 00:11:42.06, start: 0.316900, bitrate: 5973 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 7000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s
```
ffmpeg info of the output file:
```
Input #0, matroska, from 'output-nocrop.mkv':
  Duration: 00:11:42.06, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 720x480, PAR 1:1 DAR 3:2, 29.97 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
```
And finally for completeness sake, some of the command stdout from HandBrakeCLI:
```
[15:05:01] Title is likely interlaced or telecined (9 out of 10 previews). You should do something about that.
[15:05:01] scan: title (0) job->width:704, job->height:384
[15:05:01] libhb: scan thread found 1 valid title(s)
+ title 1:
  + stream: 1046_20110121072359.mpg
  + duration: 00:11:42.06
  + size: 720x480, pixel aspect: 32/27, display aspect: 1.78, 29.970 fps
  + autocrop: 0/30/10/6
  + chapters:
    + 1: cells 0->0, 0 blocks, duration 00:41:10
  + audio tracks:
    + 1, Unknown (MPEG) (2.0 ch) (iso639-2: und)
  + subtitle tracks:
  + combing detected, may be interlaced or telecined
[15:05:01] 1 job(s) to process
[15:05:01] starting job
[15:05:01] sync: expecting 74068 video frames
[15:05:01] job configuration:
[15:05:01]  * source
[15:05:01]    + 1046_20110121072359.mpg
[15:05:01]    + title 1, chapter(s) 1 to 1
[15:05:01]  * destination
[15:05:01]    + outcrop-nocrop.mkv
[15:05:01]    + container: Matroska (.mkv)
[15:05:01]  * video track
[15:05:01]    + decoder: mpeg2
[15:05:01]      + bitrate 6000 kbps
[15:05:01]    + frame rate: same as source (around 29.970 fps)
[15:05:01]    + dimensions: 720 * 480 -> 720 * 480, crop 0/0/0/0, mod 0
[15:05:01]    + filters
[15:05:01]      + Decomb (default settings)
[15:05:01]      + Deinterlace (ffmpeg or yadif/mcdeint) (default settings)
[15:05:01]      + Denoise (hqdn3d) (default settings)
[15:05:01]    + encoder: x264
[15:05:01]      + bitrate: 2200 kbps, pass: 0
```
I hope somebody finds this useful.

---

### Post by nickrout on 2011-01-26
Is there a reason to keep the original pixel sizing? Post #11 seems to resize to square pixels, which is what I usually see in transcoded files, eg that the "scene" produces. Post #12 keeps the original pixel sizing, which in (SD) broadcast in any event is usually non-square. ie in your case the picture is broadcast in 720x480, but the display aspect ratio is 16:9 so the picture you actually see is more like 854x480.

So is there a reason you prefer to do it the post #12 way? (Other than to show off your awk skills LOL)

By the way thanks for sharing your hard work on this! It may be worth a page in the mythtv wiki.

---

### Post by bcg30506 on 2011-01-26
nickrout, I thought there was so it would display better in mythfrontend on my 16:9 TV and match what is recorded and plays fine before transcoding.  However, I've just since learned about PAR/DAR and discovered that my transcoded videos display at a different ratio that I must override in myth to fill my screen.

I just finished reading a ton of info here about strict vs. loose anamorphic PAR encoding with HandBrake:
[Anamorphic Guide]("https://trac.handbrake.fr/wiki/AnamorphicGuide")
and now that my head is spinning, I'm not sure what I need.

Maybe someone can help me?  I have recorded shows from 3 sources: an analog PVR-150, analog HVR-1950 (both MPEG-2 at 720x480) with some of the stations in different aspects like Fox News which seems to broadcast in 14:9 (maybe?), and HD video from QAM cable using the HDHomeRun so the sizes can be 720x480 or 1280x720, I think.

I want all these to be able to be transcoded and still look right and fill the screen with no loss of picture or black borders on a 16:9 LCD TV.  Is loose anamorphic with auto-crop what I want?

Please feel free to state your opinions.

EDIT: FWIW, I seem to get the best aspect, size, quality, and playback results with the original command minus all the cool awk/sed/bash script tricks to set the width and height.  So I only disable autocrop.  I have not been pleased with any of the anamorphic settings.
```
HandBrakeCLI -i "$1" -o "$2" -f mkv -e x264 -b 2200 -E faac -B 192 -R 48 -d slow -5 -8 medium --crop 0:0:0:0
```

---

### Post by bcg30506 on 2011-01-27
More trial & error and Googling and reading, and I've come up with what I think is the correct command line to handle most of my needs.  See if you think these parameters make sense to keep the aspect similar to the original.
```
HandBrakeCLI -i input.mpg -o output.mkv -f mkv -e x264 -b 2200 -E faac -B 192 -R 48 --crop 0:0:0:0 --custom-anamorphic --keep-display-aspect
```
Here are the results per ffmpeg -i and my notes about how what it takes to make them look right and fill most of the screen in mythfrontend using Aspect Ratio and Adjust Fill.
```
FILE 1 (SD letterboxed; plays back at 16:9 with V.Stretch fill)

Input #0, mpeg, from '1046_20110121072359.old':
  Duration: 00:11:42.06, start: 0.316900, bitrate: 5973 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 7000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s

Input #0, matroska, from '1046_20110121072359-NoCrop-CA_KDR.mkv':
  Duration: 00:11:42.03, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 720x480, PAR 186:157 DAR 279:157, 29.97 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16



FILE 2 (HD widescreen; plays back at 16:9 with no fill)

Input #0, mpeg, from '../TVarchives/5273_20110119195900.old':
  Duration: 00:04:17.92, start: 0.333033, bitrate: 14431 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 20000 kb/s, 59.96 tbr, 90k tbn, 119.88 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x81]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s

Input #0, matroska, from '5273_20110119195900-NoCrop-CA_KDR.mkv':
  Duration: 00:04:17.90, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 59.92 tbr, 1k tbn, 119.88 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16



FILE 3 (SD fullscreen; plays back at 16:9 with no fill)

Input #0, mpeg, from '../TVarchives/1033_20110120230405.old':
  Duration: 01:16:50.03, start: 0.300411, bitrate: 5981 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 7000 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s

Input #0, matroska, from '1033_20110120230405-NoCrop-CA_KDR.mkv':
  Duration: 00:00:45.07, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 720x480, PAR 186:157 DAR 279:157, 29.97 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16

(SD fullscreen; plays back at 16:9 with no fill)
One more using no crop parameter and --strict-anamorphic:

Input #0, matroska, from '1033_20110120230405-Autocrop-SA.mkv':
  Duration: 00:00:45.34, start: 0.000000, bitrate: N/A
    Stream #0.0(eng): Video: h264, yuv420p, 710x472, PAR 199:168 DAR 70645:39648, 29.97 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16

```

---

### Post by bcg30506 on 2011-01-28
I have my final solution that is working well.  The final transcoder script my user job script calls is:
[PHP]#!/bin/bash

width=`ffmpeg -i "$1" 2>&1 1>/dev/null | grep Video: | awk '{print $6}' | awk 'BEGIN{FS="x"}{print $1}' | sed 's/,*$//'`

if [ "$width" != "1280" ]; then
  quality=19
else
  quality=22
fi

HandBrakeCLI -i "$1" -o "$2" -f mkv -e x264 -q $quality -E faac -B 192 -R 48 --strict-anamorphic -d slow -5 -8 medium
[/PHP]
You can read all the details of my issues and the advice given to solve them starting here then following the thread below it to the long post about my test results:
[Handbrake Forum]("https://forum.handbrake.fr/viewtopic.php?uid=24347&f=6&t=16097&start=25#p91515")

Also, here is the user job script called by mythbackend which in turn uses the script above:
[PHP]#!/usr/bin/perl -w
# ============================================================================
# = NAME
# transcode_mp4
#
# = USAGE
my $usage = 'Usage:
copy_and_transcode.pl -f %FILE% -p autodetect
';
# = Original AUTHOR
# Nigel Pearson
# ============================================================================

use strict;
use MythTV;

# What file are we copying/transcoding?
my $file  = '';
my $jobid = -1;

# do nothing?
my $noexec = 0;

# extra console output?
my $DEBUG = 1;

# some globals
my ($chanid, $command, $query, $ref, $starttime);
my ($newfilename, $newstarttime);

my $mt = new MythTV();
my $db = $mt->{'dbh'};


# ============================================================================
sub Die($)
{
   print STDERR "@_\n";
   exit -1;
}
# ============================================================================
# Parse command-line arguments, check there is something to do:
#
if ( ! @ARGV )
{   Die "$usage"  }

while ( @ARGV && $ARGV[0] =~ m/^-/ )
{
    my $arg = shift @ARGV;

    if ( $arg eq '-d' || $arg eq '--debug' )
    {   $DEBUG = 1  }
    elsif ( $arg eq '-n' || $arg eq '--noaction' )
    {   $noexec = 1  }
    elsif ( $arg eq '-j' || $arg eq '--jobid' )
    {   $jobid = shift @ARGV  }
    elsif ( $arg eq '-f' || $arg eq '--file' )
    {   $file = shift @ARGV  }
    else
    {
        unshift @ARGV, $arg;
        last;
    }
}

if ( ! $file && $jobid == -1 )
{
    print "No file or job specified. $usage";
    exit;
}

if ( $noexec )
{   print "NoExecute mode. No transcoding or SQL database changes.\n"  }

# ============================================================================
# If we were supplied a jobid, lookup chanid
# and starttime so that we can find the filename
#
if ( $jobid != -1 )
{
    $query = $db->prepare("SELECT chanid, starttime " .
                          "FROM jobqueue WHERE id=$jobid;");
    $query->execute || Die "Unable to query jobqueue table";
    $ref       = $query->fetchrow_hashref;
    $chanid    = $ref->{'chanid'};
    $starttime = $ref->{'starttime'};
    $query->finish;

    if ( ! $chanid || ! $starttime )
    {   Die "Cannot find details for job $jobid"  }

    $query = $db->prepare("SELECT basename FROM recorded " .
                          "WHERE chanid=$chanid AND starttime='$starttime';");
    $query->execute || Die "Unable to query recorded table";
    ($file) = $query->fetchrow_array; 
    $query->finish; 

    if ( ! $file )
    {   Die "Cannot find recording for chan $chanid, starttime $starttime"  }

    if ( $DEBUG )
    {
        print "Job $jobid refers to recording chanid=$chanid,",
              " starttime=$starttime\n"
    }
}
else
{
    if ( $file =~ m/(\d+)_(\d\d\d\d)(\d\d)(\d\d)(\d\d)(\d\d)(\d\d)/ )
    {   $chanid = $1, $starttime = "$2-$3-$4 $5:$6:$7"  }
    else
    {
        print "File $file has a strange name. Searching in recorded table\n";
        $query = $db->prepare("SELECT chanid, starttime " .
                              "FROM recorded WHERE basename='$file';");
        $query->execute || Die "Unable to query recorded table";
        ($chanid,$starttime) = $query->fetchrow_array;
        $query->finish;

        if ( ! $chanid || ! $starttime )
        {   Die "Cannot find details for filename $file"  }
    }
}

# A commonly used SQL row selector:
my $whereChanAndStarttime = "WHERE chanid=$chanid AND starttime='$starttime'";

# ============================================================================
# Find the directory that contains the recordings, check the file exists
#

my $dir  = undef;
my $dirs = $mt->{'video_dirs'};

foreach my $d ( @$dirs )
{
    if ( ! -e $d )
    {   Die "Cannot find directory $dir that contains recordings"  }

    if ( -e "$d/$file" )
    {
        $dir = $d;
        #print "$d/$file exists\n";
        last
    }
    else
    {   print "$d/$file does not exist\n"   }
}

if ( ! $dir )
{   Die "Cannot find recording"  }

# ============================================================================
# Do the transcode
#
$newfilename = $file;
$newfilename =~ s/mpg/mkv/;

$command = "2x264 '$dir/$file' '$dir/$newfilename'";

if ( $DEBUG || $noexec )
{   print "# $command\n"  }

if ( ! $noexec )
{
    chdir $dir;
    system $command;

    if ( ! -e "$newfilename" )
    {   Die "Transcode failed\n"  }
}

if ( $DEBUG && ! $noexec )
{
    print 'Old file size = ' . (-s "$dir/$file")        . "\n";
    print 'New file size = ' . (-s "$dir/$newfilename") . "\n";
}

# ============================================================================
# Last, copy the existing recorded details with the new file name.
#
$query = $db->prepare("SELECT * FROM recorded $whereChanAndStarttime;");
$query->execute || Die "Unable to query recorded table";
$ref = $query->fetchrow_hashref;
$query->finish;

my $filesize = -s "$dir/$newfilename";
$command = "UPDATE recorded SET basename='$newfilename', filesize='$filesize', subtitle=concat(subtitle,' (H264)') $whereChanAndStarttime;";

if ( $DEBUG || $noexec )
{   print "# $command\n"  }

if ( ! $noexec )
{   $db->do($command)  || Die "Couldn't update recording's record"   }

# Just delete the seek table
$command = "delete from recordedseek $whereChanAndStarttime;";
if ( $DEBUG || $noexec )
{   print "# $command\n"  }
if ( ! $noexec )
{   $db->do($command)  || Die "Couldn't update recording's record"   }

$db->disconnect;

# rename old file
$command = "rename 's/mpg/old/' '$dir/$file'";
system $command;

# rename thumbnail
$command = "rename 's/mpg/mkv/' '$dir/$file.png'";
system $command;

# touch thumbnail
$command = "touch '$dir/$newfilename.png'";
system $command;

1;[/PHP]

---

### Post by bcg30506 on 2011-01-30
Slight correction :oops: to my 2x264 helper script in the previous post.  I checked the if statement for width backwards to determine HD or SD.  HD resolutions, I now know, can change (1080i or 720p).  SD resolution is fixed by my capture card setting in mythtv-setup at 720x480.  So I instead should check for a width of 720 for SD and else encode as HD.  This will prevent HD sizes other than 1280x720 from using the SD rate.

So SD=quality of 19.5, and HD=quality of 22.
```
#!/bin/bash

width=`ffmpeg -i "$1" 2>&1 1>/dev/null | grep Video: | awk '{print $6}' | awk 'BEGIN{FS="x"}{print $1}' | sed 's/,*$//'`

if [ "$width" == "720" ]; then
  quality=19.5
else
  quality=22
fi

HandBrakeCLI -i "$1" -o "$2" -f mkv -e x264 -q $quality -E faac -B 192 -R 48 --strict-anamorphic -d slow -5 -8 medium

```

---

### Post by bcg30506 on 2011-01-31
Okay, one last modification to the parent script that is called by mythbackend as a user job.  I just discovered that when running a large HD file through it, the MySQL connection times out so it the script errors instead of completing the user job.

So I now close the first connection before the actual transcode command is called, then when it completes, I create a new DB connection to finish updating the recording tables.

Here is the corrected script:
[PHP]#!/usr/bin/perl -w
# ============================================================================
# = NAME
# transcode_mp4
#
# = PURPOSE
# Encode a recording as an H264 mkv file
#
# = USAGE
my $usage = 'Usage:
transcode_mp4 -f %FILE% -p autodetect
transcode_mp4 -j %JOBID% -p autodetect
transcode_mp4 --file file [--debug] [--noaction]  [transcode-arguments]
';
# The first two forms would invoke this as a MythTV User Job
#
# = AUTHOR
# Brad Grant
# ============================================================================

use strict;
use MythTV;

# What file are we copying/transcoding?
my $file  = '';
my $jobid = -1;

# do nothing?
my $noexec = 0;

# extra console output?
my $DEBUG = 1;

# some globals
my ($chanid, $command, $query, $ref, $starttime);
my ($newfilename, $newstarttime);

my $mt = new MythTV();
my $db = $mt->{'dbh'};

# ============================================================================
sub Die($)
{
   print STDERR "@_\n";
   exit -1;
}
# ============================================================================
# Parse command-line arguments, check there is something to do:
#
if ( ! @ARGV )
{   Die "$usage"  }

while ( @ARGV && $ARGV[0] =~ m/^-/ )
{
    my $arg = shift @ARGV;

    if ( $arg eq '-d' || $arg eq '--debug' )
    {   $DEBUG = 1  }
    elsif ( $arg eq '-n' || $arg eq '--noaction' )
    {   $noexec = 1  }
    elsif ( $arg eq '-j' || $arg eq '--jobid' )
    {   $jobid = shift @ARGV  }
    elsif ( $arg eq '-f' || $arg eq '--file' )
    {   $file = shift @ARGV  }
    else
    {
        unshift @ARGV, $arg;
        last;
    }
}

if ( ! $file && $jobid == -1 )
{
    print "No file or job specified. $usage";
    exit;
}

if ( $noexec )
{   print "NoExecute mode. No transcoding or SQL database changes.\n"  }

# ============================================================================
# If we were supplied a jobid, lookup chanid
# and starttime so that we can find the filename
#
if ( $jobid != -1 )
{
    $query = $db->prepare("SELECT chanid, starttime " .
                          "FROM jobqueue WHERE id=$jobid;");
    $query->execute || Die "Unable to query jobqueue table";
    $ref       = $query->fetchrow_hashref;
    $chanid    = $ref->{'chanid'};
    $starttime = $ref->{'starttime'};
    $query->finish;

    if ( ! $chanid || ! $starttime )
    {   Die "Cannot find details for job $jobid"  }

    $query = $db->prepare("SELECT basename FROM recorded " .
                          "WHERE chanid=$chanid AND starttime='$starttime';");
    $query->execute || Die "Unable to query recorded table";
    ($file) = $query->fetchrow_array; 
    $query->finish; 

    if ( ! $file )
    {   Die "Cannot find recording for chan $chanid, starttime $starttime"  }

    if ( $DEBUG )
    {
        print "Job $jobid refers to recording chanid=$chanid,",
              " starttime=$starttime\n"
    }
}
else
{
    if ( $file =~ m/(\d+)_(\d\d\d\d)(\d\d)(\d\d)(\d\d)(\d\d)(\d\d)/ )
    {   $chanid = $1, $starttime = "$2-$3-$4 $5:$6:$7"  }
    else
    {
        print "File $file has a strange name. Searching in recorded table\n";
        $query = $db->prepare("SELECT chanid, starttime " .
                              "FROM recorded WHERE basename='$file';");
        $query->execute || Die "Unable to query recorded table";
        ($chanid,$starttime) = $query->fetchrow_array;
        $query->finish;

        if ( ! $chanid || ! $starttime )
        {   Die "Cannot find details for filename $file"  }
    }
}

# A commonly used SQL row selector:
my $whereChanAndStarttime = "WHERE chanid=$chanid AND starttime='$starttime'";

# ============================================================================
# Find the directory that contains the recordings, check the file exists
#

my $dir  = undef;
my $dirs = $mt->{'video_dirs'};

foreach my $d ( @$dirs )
{
    if ( ! -e $d )
    {   Die "Cannot find directory $dir that contains recordings"  }

    if ( -e "$d/$file" )
    {
        $dir = $d;
        #print "$d/$file exists\n";
        last
    }
    else
    {   print "$d/$file does not exist\n"   }
}

if ( ! $dir )
{   Die "Cannot find recording"  }

# ============================================================================
# Do the transcode
#
$db->disconnect;
$newfilename = $file;
$newfilename =~ s/mpg/mkv/;

$command = "2x264 '$dir/$file' '$dir/$newfilename'";

if ( $DEBUG || $noexec )
{   print "# $command\n"  }

if ( ! $noexec )
{
    chdir $dir;
    system $command;

    if ( ! -e "$newfilename" )
    {   Die "Transcode failed\n"  }
}

if ( $DEBUG && ! $noexec )
{
    print 'Old file size = ' . (-s "$dir/$file")        . "\n";
    print 'New file size = ' . (-s "$dir/$newfilename") . "\n";
}

# ============================================================================
# Last, copy the existing recorded details with the new file name.
#
$mt = new MythTV();
$db = $mt->{'dbh'};
$query = $db->prepare("SELECT * FROM recorded $whereChanAndStarttime;");
$query->execute || Die "Unable to query recorded table";
$ref = $query->fetchrow_hashref;
$query->finish;

my $filesize = -s "$dir/$newfilename";
$command = "UPDATE recorded SET basename='$newfilename', filesize='$filesize', subtitle=concat(subtitle,' (H264)') $whereChanAndStarttime;";

if ( $DEBUG || $noexec )
{   print "# $command\n"  }

if ( ! $noexec )
{   $db->do($command)  || Die "Couldn't update recording's record"   }

# Just delete the seek table
$command = "delete from recordedseek $whereChanAndStarttime;";
if ( $DEBUG || $noexec )
{   print "# $command\n"  }
if ( ! $noexec )
{   $db->do($command)  || Die "Couldn't update recording's record"   }

# Update the seek table
# $command = "mythcommflag --rebuild -c $chanid -s '$starttime' --rebuild";
# print "# $command\n";
# system $command;

$db->disconnect;

# rename old file
$command = "rename 's/mpg/old/' '$dir/$file'";
system $command;

# rename thumbnail
$command = "rename 's/mpg/mkv/' '$dir/$file.png'";
system $command;

# touch thumbnail
$command = "touch '$dir/$newfilename.png'";
system $command;

1;[/PHP]

---

### Post by novellahub on 2011-02-16
Thank you for creating these scripts.  I am having a issue executing your helper script 2x264.  Do I need to create symbolic link to it?  Here is the message in the log file:

```
# 2x264 '/myth3/tv/1091_20110211190000.mpg' '/myth3/tv/1091_20110211190000.mkv'
sh: 2x264: not found
Transcode failed
```

The 2x264 script is in /usr/local/bin and is executable. 

Thanks,

Joe

---

### Post by bcg30506 on 2011-02-16
I'm not sure. It says what it says: Not found.  Are you very certain /usr/local/bin is in your path and the script is in there and executable by all (chmod a+x 2x264)?

No other linking is necessary.  It simply needs access to the script to run it.  Can you type the following and paste the results?
```
cd /usr/local/bin
ls -l 2x264*
```

Also, have you tried running the command manually once to see that it runs and what feedback you get?

---

### Post by novellahub on 2011-02-16
Here you go:

```
novellahub@mythtvmaster:/usr/local/bin$ ls -la
total 20
drwxr-xr-x  2 root root 4096 2011-02-16 20:30 .
drwxr-xr-x 10 root root 4096 2009-10-27 12:15 ..
-rwxr-xr-x  1 root root  321 2011-02-16 20:30 2x264
-rwxr-xr-x  1 root root 6255 2011-02-16 18:20 transcode_mp4

```

I got it running now.  I deleted my first child 2x264 script and then re-created it.  It is running now :)

---

### Post by bcg30506 on 2011-02-16
Good deal.  Glad you got it.

---

### Post by laffer98 on 2012-03-16
I am not having any luck on getting your job/script running.  It shows queued, but it never runs.

---

### Post by bcg30506 on 2012-03-20
I'm not sure what your trouble might be.  I'm no expert, but it does work for me.  Can you post the backend log so we can see if it is reporting any errors?

---

