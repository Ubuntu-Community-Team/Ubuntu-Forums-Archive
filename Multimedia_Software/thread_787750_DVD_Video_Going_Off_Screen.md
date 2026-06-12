---
title: "DVD Video Going Off Screen"
date: 2008-05-09
forum: Multimedia Software
---

### Post by john.hall on 2008-05-09
I&#12288;have several .avi files that I burn to DVD.  This is the script that I am using:

```

#!/usr/bin/env sh

if [ $# -eq 0 ]; then
  echo "usage: $0 FILE..."
  exit 1
fi

for avi in $*
do
  mpg=$avi.mpg
  ffmpeg -y -i $avi -target ntsc-dvd -aspect 4:3 $mpg
  dvdauthor -o dvd$$/ -t $mpg
done

dvdauthor -o dvd$$/ -T
mkisofs -dvd-video -o dvd$$.iso dvd$$/

```

Then I burn it with growisofs -dvd-compat -Z /dev/dvd=<the_iso>.

The problem is that when I take the DVD to my DVD player and watch it on TV, the video extends past the edge of the screen, so you can't see all of it.

Why is this happening, and how do I fix it?  Thanks.

---

