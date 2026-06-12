---
title: "how do i get file info with mplayer?"
date: 2010-02-01
forum: Multimedia Software
---

### Post by jfca283 on 2010-02-01
hi
what do i need to write to get the mediafile info from mplayer?
i mean...from console with mplayer...
thanks

---

### Post by andrew.46 on 2010-02-01
Hi jfca,

Best way is to use the midentify.sh script that comes with the MPlayer source:

```

#!/bin/sh
#
# This is a wrapper around the -identify functionality.
# It is supposed to escape the output properly, so it can be easily
# used in shellscripts by 'eval'ing the output of this script.
#
# Written by Tobias Diedrich <ranma+mplayer@tdiedrich.de>
# Licensed under GNU GPL.

if [ -z "$1" ]; then
	echo "Usage: midentify.sh <file> [<file> ...]"
	exit 1
fi

mplayer -vo null -ao null -frames 0 -identify "$@" 2>/dev/null |
	sed -ne '/^ID_/ {
	                  s/[]()|&;<>`'"'"'\\!$" []/\\&/g;p
	                }'

```

All the best,

Andrew

---

### Post by sports.car.guy on 2010-02-01
> **jfca283 said:**
> hi
what do i need to write to get the mediafile info from mplayer?
i mean...from console with mplayer...
thanks


A little more specifics would be a good thing. Are you talking like codec information, meta information, what?

---

### Post by jfca283 on 2010-02-04
i mean...audio/video codecs, FPS, channels and subtitles

---

### Post by andrew.46 on 2010-02-04
Hi jfca,

Perhaps you might be happiest with [mediainfo]("http://mediainfo.sourceforge.net/en")? There is an 'official' PPA that can be added as follows if you are using Karmic (this is a single command):

```

sudo add-apt-repository ppa:shiki/mediainfo && \
sudo apt-get update && \
sudo apt-get install mediainfo mediainfo-gui

```

and then open your media file with the command:

```
mediainfo -f ***[COLOR="Blue"]myfile.mp4[/COLOR]***
```

while substituting 'myfile.mp4' for the name of your own file. Full usage can be seen by running *mediainfo --help* from the commandline. There is a gui also which should appear under 'Sound and Video', I personally find the commandline interface a little cleaner...

All the best,

Andrew

---

### Post by jfca283 on 2010-02-06
thanks andrew...it worked
SOLVED

---

### Post by andrew.46 on 2010-02-06
Hi jfca,

> **jfca283 said:**
> thanks andrew...it worked

Excellent news :). I suspect you will find that mediainfo provides much for comprehensive information than FFmpeg or MPlayer.

All the best,

Andrew

---

