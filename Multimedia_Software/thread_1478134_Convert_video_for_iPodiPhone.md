---
title: "Convert video for iPod/iPhone?"
date: 2010-05-09
forum: Multimedia Software
---

### Post by h4x0rmx on 2010-05-09
I know this question has been asked before, but I couldn't find any recent topics.
What's a good program in Linux/Ubuntu to convert any video file to .mp4 for an iPod/iPhone?

---

### Post by chiwi on 2010-05-10
mencoder and ffmpeg. However these two apps are run from the command line, but there are quite some GUIs for them you may need to search.

this is a script I got from the internet (credits to the creator), that I only added support for subtitles. (the script calls mencoder and pastes the subtitles into the video. The subtitles should be named the same as the video file, only changing the extension. If you want to remove the sub support, simply remove the  -sub option when calling the command)

After a huge research, this is the best script that I could find, it works great with my ipod 5th gen:

```

#!/bin/bash

quiet=""
passes="2"
codec="lavc"
bitrate="448"
bitratemax="960"
width="320"
height="240"

usage () {
    echo "
Usage: `basename "$0"` [-q] [-1|-2] [-L|-H] [-b BITRATE ] [-m MAX_BITRATE] [-w WIDTH] [-h HEIGHT] MOVIE_FILE
-q              Quieter output.
-1              Use 1 pass encoding.
-2              Use 2 passes (default).
-L              Use lavc (default). Much quicker, but not as high quality.
-H              Use h264.  Slow, but high quality.
-b BITRATE      Defaults to 448, 192 for low quality, 768 for high
-m MAX_BITRATE  Defaults to 960, 768 for low quality, 1500 for high
-w WIDTH        Defaults to 320, ipod screen width.  Use 640 for tv out.
-h HEIGHT       Defaults to 240, ipod screen height.  Use 480 for tv out.
"
}

[ "$#" -lt 1 ] && usage && exit -1

while getopts "q12LHb:m:w:h:" Option; do
    case "$Option" in
        q) quiet="-quiet" ;;
        1) passes="1" ;;
        2) passes="2" ;;
        b) bitrate="$OPTARG" ;;
        m) bitratemax="$OPTARG" ;;
        w) width="$OPTARG" ;;
        h) height="$OPTARG" ;;
        L) codec="lavc" ;;
        H) codec="h264" ;;
        *) usage; exit -1 ;;
    esac
done
shift $(( $OPTIND - 1 ))

while [ "$1" ]; do
    infile="$1"
    ! [ -f "$infile" ] && echo Error, file not found \"$infile\"  && usage && exit -1

    outfile="ipod/${1%.*}.m4v"

    num=1
    while [ -f "$outfile" ]; do
        echo "output file exists, adding number"
        outfile="${1%.*}-$num.m4v"
        let "num += 1"
    done

    pass=0
    if [ "$codec" = "lavc" ]; then
        while [ "$pass" -lt "$passes" ]; do
            let "pass += 1"
            echo --- Pass $pass of $passes Pass LAVC Encoding ---
            echo $outfile
            echo $width x $height, $bitrate-$bitratemax
            sleep 1
            encopts="aglobal=1:vglobal=1:vcodec=mpeg4:vbitrate=$bitrate:acodec=libfaac:abitrate=128"
            [ "$passes" -gt "1" ] && encopts="$encopts:vpass=$pass"
            echo $encopts
            sleep 1
            mencoder "$infile" $quiet -ofps 30 -sws 9 -of lavf -lavfopts format=ipod \
                -vf scale=-10:$height,dsize=$width:$height:0,harddup \
                -ovc lavc \
                -lavcopts $encopts \
                -oac faac \
                -alang en \
                -sub "${infile/${infile: -3}/srt}" \
                -srate 22050 \
                -o "$outfile"
            EXIT_CODE="$?"
            [[ "$?" != "0" ]] && exit "$EXIT_CODE"
        done

    elif [ "$codec" = "h264" ]; then
        while [ "$pass" -lt "$passes" ]; do
            let "pass += 1"
            echo --- Pass $pass of $passes Pass H264 Encoding ---
            echo $outfile
            echo $width x $height, $bitrate-$bitratemax
            sleep 1
            encopts="bitrate=$bitrate:vbv_maxrate=$bitratemax:vbv_bufsize=2000:nocabac:me=hex:subq=4:frameref=2:trellis=1:level_idc=30:global_header:threads=auto"
            [ "$passes" -gt "1" ] && encopts="$encopts:pass=$pass"
            echo $encopts
            sleep 1
            mencoder "$infile" $quiet -ofps 30 -sws 9 -of lavf -lavfopts format=ipod \
                -vf scale=-10:$height,dsize=$width:$height:0,harddup \
                -ovc x264 \
                -x264encopts $encopts \
                -oac faac \
                -alang en \
                -faacopts mpeg=4:object=2:br=160:raw -channels 2 \
                -srate 48000 \
                -sub "${infile/${infile: -3}/srt}" \
                -o "$outfile"
            EXIT_CODE="$?"
            if [[ "$?" != "0" ]]; then exit "$EXIT_CODE"; fi
        done
    fi

    shift
done

```

---

### Post by FakeOutdoorsman on 2010-05-10
> **h4x0rmx said:**
> I know this question has been asked before, but I couldn't find any recent topics.
What's a good program in Linux/Ubuntu to convert any video file to .mp4 for an iPod/iPhone?

See the iPod example in:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095).

You may need to enable some additional encoders (*libx264* and *libfaac* specifically). If you don't want to compile FFmpeg as shown in the above link, see:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Note that you will need to change the preset in the iPod example from *-vpre slow* to *-vpre hq* if you decide not to compile FFmpeg.

---

### Post by sn1ckers on 2010-05-11
I use [Handbrake]("http://www.handbrake.fr") which is a pretty easy to use converter which also offers a command line interface. It also has pre configured settings for iPod/iPhone. Follow [this thread]("http://ubuntuforums.org/showthread.php?t=1452967&page=2") at Ubuntuforums. 

Then I use gtkpod (available in Synaptic) to transfer the movie to the iPhone. Just remember to also install libmp4v2-0 using the Synaptic package manager. The sad part with gtkpod is that you have to use [FONT=Fixedsys]ifuse[FONT=Arial] [/FONT][/FONT]and [FONT=Fixedsys]fusermount[/FONT]. See the [Ubuntu wiki]("https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20with%20GTKpod") for more info.

---

