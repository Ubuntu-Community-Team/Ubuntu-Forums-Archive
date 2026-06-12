---
title: "Better display of srt/sub subtitles in Mythbunto 9.10"
date: 2010-02-15
forum: Mythbuntu
---

### Post by zzarko on 2010-02-15
I really don't like when subtitles are displayed over the movie instead in those black bars that occupy screen space anyway, so this is my solution for better subtitle support in Mythbuntu 9.10:

1. Use external player instead of internal one (Utilities / Setup -> Setup -> Media Settings -> Video Settings -> Player Settings -> Default Video Player) with this command:
mplayer %s

2. In home directory, create (if it doesn't exists) .mplayer/config file with following contents:
fs=1
quiet=1
vo=xv
cache=8192
cache-min=4
sws=0
sub-fuzziness=2
subfont-osd-scale=2
#subfont-encoding=windows-1250
osdlevel=3
***=1
***-font-scale=2
***-bottom-margin=100
***-use-margins=1
#***-force-style=Bold=1,Outline=2,Encoding=238
 ***-force-style=Bold=1,Outline=2
(replace *** with three letters: a s s; I'm not being rude, this is subtitle extension handled by libass and stupid politically-correct text-checking replaced all those three letters with ***).

This will use libass for subtitle display and they will be displayed in yellow color in black bar below the movie. Also, current time and movie duration will be displayed in upper left corner.

If anyone knows how to use different encodings with libass, please let me know (or, how to display default mplayer subtitles in black bar instead over the movie; they support different encodings). I tried to change font encoding using libass font styles (as described in mplayer documentation), but without success. I need eastern-european (windows-1250) encoding for a machine that I configured as a video player for my mom (she doesn't understand english and needs subtitles for all foreign movies).

---

