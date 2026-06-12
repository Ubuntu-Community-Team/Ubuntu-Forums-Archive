---
title: "Nuvexport"
date: 2008-08-21
forum: Mythbuntu
---

### Post by perhagge on 2008-08-21
Nuvexport is not working. I'm trying to make Xvid of some recorded shows. "nuvexport --mencoder" and then  I select shows and so on, the process starts and when it reaches 99.9% it dies, se below.

[COLOR="Blue"]Encode started:  Thu Aug 21 12:49:48 2008
Waiting for mythtranscode to set up the fifos.
Starting mencoder.
processed:  53040 of 53913 frames (98.38%), 26.80 fps
mythtranscode finished.
processed:  53861 of 53913 frames (99.90%), 26.81 fps

mythtranscode died early.Please use the --debug option to figure out what went wrong.[/COLOR]

Then with -- debug option I get following in the start.


[COLOR="blue"]perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "sv_SE.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").[/COLOR]


then i make the selections and get:
[COLOR="blue"]
system call:
mkdir -m 0755 /tmp/fifodir_6237/

forking:
/usr/bin/nice -n19 /usr/bin/mythtranscode --showprogress -p '0' -c '1002' -s '2008-06-04T20:00:00' -f "/tmp/fifodir_6237/" --honorcutlist 2>&1

forking:
/usr/bin/nice -n19 mencoder -aspect 1.77777777777778 -noskip -idx /tmp/fifodir_6237/vidout -audiofile /tmp/fifodir_6237/audout   -demuxer 20 -audio-demuxer 20 -rawaudio rate=48000:channels=2 -demuxer 26 -rawvideo w=720:h=576:fps=25.000    -ovc xvid  -oac mp3lame -lameopts vbr=3:br=128 -xvidencopts fixed_quant=3 -o './SÃ¶derlÃ¤ge.avi' -vf lavcdeint,scale=512:288  2>&1

Cleaning up temp files.[/COLOR]

Could the first error about loclae setting be the problem? and how to fix it?

I live in sweden and using some swedish letters could it be the problem

Thanks,
/Pär

---

### Post by ian dobson on 2008-08-21
Hi,

Maybe try from terminal:-

export LANGUAGE="sv_SE.UTF-8"
export LC_ALL ="sv_SE.UTF-8"

then mythtranscode with debug enabled.

I don't know if that would help but it's worth a try.

Regards
Ian Dobson

---

