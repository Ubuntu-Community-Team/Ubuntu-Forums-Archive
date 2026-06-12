---
title: "Real Audio to MP3"
date: 2008-11-02
forum: Multimedia Software
---

### Post by rmarc71 on 2008-11-02
I forget how to do this all the time, and I end up rewriting it again and again (I only want real audio streams occasionally, when I run out of news podcasts to listen too).

Anyway, here's a simple method:

Requires pacpl and mplayer, the URL in question is the rstp stream.
Note: I had to download a bunch of audio perl modules when I upgraded from 8.04 to 8.10 (Audio::WMA, Audio::Musepack and CDDB_get; I forget what their ubuntu package names are but it's pretty obvious in synaptic).

[PHP]
#!/bin/bash

if [ ! "$1" ] 
then
        echo "usage: rip.real.sh <url>"
        exit;
fi

FILE=`echo $1 | perl -e 'while (<STDIN>) { chomp; my ($file) = /\S+\/(\S+\.rm)\?\S+/; print $file,"\n"; }'`

MPLAYER=`which mplayer`;
echo $MPLAYER
if [ ! -x $MPLAYER ];
then
        echo no mplayer 
        exit;
fi

# Download real file
MPLAYER_ARGS="-v -bandwidth 1111111 -noframedrop -dumpfile $FILE -dumpstream"
$MPLAYER $MPLAYER_ARGS $1

# Now convert to MP3
pacpl --to mp3 $FILE

[/PHP]

---

### Post by rmarc71 on 2009-12-20
Just found the need for this again, in 9.10, all that was necessary was to get pacpl and lame via apt-get 

R. Marc

---

