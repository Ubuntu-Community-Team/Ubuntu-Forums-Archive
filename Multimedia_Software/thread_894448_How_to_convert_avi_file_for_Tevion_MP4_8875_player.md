---
title: "How to convert avi file for Tevion MP4 8875 player"
date: 2008-08-19
forum: Multimedia Software
---

### Post by duncs on 2008-08-19
Following on from previous comments I found in this  [thread]("http://ubuntuforums.org/showthread.php?t=711548")
and also this [thread](http://ubuntuforums.org/showthread.php?t=646164) I have managed to convert an avi to full screen size by using the following command with good audio

```
amv-ffmpeg-linux-i386-20071030 -i <AVI FILE> -f amv -s 208x176 -r 10 -acodec adpcm_ima_amv -ab 352k -ac 1 -ar 22050 -qmin 3 -qmax 3 <AMV FILE>
```

I originally found I have a bad audio echo but reducing the fps to 10 (rather than the suggested 16) the echo went but its still watchable on the Tevion.

In case it makes life (even) easier for people, I wrapped this in a small script as follows:

```

#!/usr/bin/bash

avi=$1
amv=${avi%.avi}.amv

if [ -z "$avi" ] || [ ! -f $avi ]; then
    echo "$0 Usage:"
    echo "  $0 <avi>"
    exit 255
fi

case $avi in
    *.avi) ;;
    *)
        echo "Fatal: input is not an AVI file"
        exit 255
    ;;
esac

if [ -f $amv ]; then
    rm $amv
fi

amv-ffmpeg-linux-i386-20071030 -i $avi -f amv -s 208x176 -r 10 -acodec adpcm_ima_amv -ab 352k -ac 1 -ar 22050 -qmin 3 -qmax 3 $amv

```

Not the best script, thrown together, but it works for me.

Hope this will help someone out there as I have been banging my head against the wall on this all day.

  Duncs

---

