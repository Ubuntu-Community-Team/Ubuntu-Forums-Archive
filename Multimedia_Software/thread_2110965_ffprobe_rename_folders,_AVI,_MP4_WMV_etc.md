---
title: "ffprobe rename folders, AVI, MP4 WMV etc"
date: 2013-01-31
forum: Multimedia Software
---

### Post by sohlinux on 2013-01-31
Hello,

I have a script which was kindly written by evilsoup, the script renames directories from info of the videos within, it adds the bit rate, resolution and duration to the folder name.

How can I change the script so it will process all video types, AVI, MPG, WMV, MP4, etc in both upper and lowercase?

Also how can I make it change the file name rather than the folder name?

thanks

```

#!/bin/bash

find . -maxdepth 1 -mindepth 1 -type d -exec readlink -f '{}' \; | while read dir
do
vid=$(find "$dir" -type f -name "*.avi" | head -n 1)

    bitrate=$(ffprobe "$vid" 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p')
    resolution=$(ffprobe "$vid" 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')
    duration=$(ffprobe "$vid" 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1kbps/p')

    mv "$dir" "$dir $bitrate $resolution $duration"
done

exit 0


```

---

### Post by papibe on 2013-01-31
Hi sohlinux.

If you use the option -iname instead of -name, matches will be case insensitive.

As for including more file extensions, you can use a conditional 'or' to your search:
```
 find -type f \( -iname '*.avi' -or -iname '*.mkv' -or -iname '*.mp4' \)
```
As a side note, I would recommend testing your script first before actually moving your files. I would change the 'mv' line for an echo:
```
...
echo mv "$dir" "$dir $bitrate $resolution $duration"
...
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by sohlinux on 2013-01-31
> **papibe said:**
> Hi sohlinux.

If you use the option -iname instead of -name, matches will be case insensitive.

As for including more file extensions, you can use a conditional 'or' to your search:
```
 find -type f \( -iname '*.avi' -or -iname '*.mkv' -or -iname '*.mp4' \)
```
As a side note, I would recommend testing your script first before actually moving your files. I would change the 'mv' line for an echo:
```
...
echo mv "$dir" "$dir $bitrate $resolution $duration"
...
```
Hope it helps. Let us know how it goes.
Regards.

thanks, that worked! :p

```
find . -maxdepth 1 -mindepth 1 -type d -exec readlink -f '{}' \; | while read dir
do
vid=$(find "$dir" -type f -iname "*.avi" -or -iname "*.mkv" -or -iname "*.mp4" -or -iname "*.mpg" -or -iname "*.wmv" -or -iname "*.mpeg" -or -iname "*.mov" | head -n 1)
    bitrate=$(ffprobe "$vid" 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p')
    resolution=$(ffprobe "$vid" 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')
    duration=$(ffprobe "$vid" 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1/p')
    mv "$dir" "$dir $resolution $bitrate $duration"
done
exit 0

```

Do you know what needs to be changed to write the info to the file name instead of the folder name?

---

### Post by evilsoup on 2013-01-31
IMO, a neater way of getting find to search for multiple strings is to use regular expressions.

```

find . -type f -regextype posix-extended -regex ".*avi|.*mkv|.*mp4"

```.* is the regex equivalent of * in bash globbing, and '|' means 'or'. You can cut out the '-regextype posix-extended' if you want, but then you'll have to use '\|' instead of '|'.

To get case-insensitive search, use '-iregex' instead.

To do every file in a directory - recursively - you could do something like this:

```

#!/bin/bash

find . -type f -regextype posix-extended -iregex ".*avi|.*mkv|.*mp4|.*mpg|.*wmv|.*mpeg|.*mov" -exec readlink -f '{}' \; | while read vid
do
    bitrate=$(ffprobe "$vid" 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p')
    resolution=$(ffprobe "$vid" 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')
    duration=$(ffprobe "$vid" 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1/p')

##  ${vid%.*} strips the extension from $vid
## ${vid##*.} strips everything BUT the extension from $vid
    mv "$vid" "${vid%.*} $resolution $bitrate $duration.${vid##*.}"
done

exit 0

```

---

### Post by sohlinux on 2013-02-01
> **evilsoup said:**
> IMO, a neater way of getting find to search for multiple strings is to use regular expressions.

```

find . -type f -regextype posix-extended -regex ".*avi|.*mkv|.*mp4"

```.* is the regex equivalent of * in bash globbing, and '|' means 'or'. You can cut out the '-regextype posix-extended' if you want, but then you'll have to use '\|' instead of '|'.

To get case-insensitive search, use '-iregex' instead.

To do every file in a directory - recursively - you could do something like this:

```

#!/bin/bash

find . -type f -regextype posix-extended -iregex ".*avi|.*mkv|.*mp4|.*mpg|.*wmv|.*mpeg|.*mov" -exec readlink -f '{}' \; | while read vid
do
    bitrate=$(ffprobe "$vid" 2>&1 | sed -n '/bitrate:/s/.* \([0-9]*\) .*/\1kbps/p')
    resolution=$(ffprobe "$vid" 2>&1 | sed -n '/Video:/s/.* \([0-9]*x[0-9]*\).*/\1/p')
    duration=$(ffprobe "$vid" 2>&1 | sed -n '/Duration:/s/.* \([0-9]*:[0-9]*:[0-9]*\)\..*/\1/p')

##  ${vid%.*} strips the extension from $vid
## ${vid##*.} strips everything BUT the extension from $vid
    mv "$vid" "${vid%.*} $resolution $bitrate $duration.${vid##*.}"
done

exit 0

```

thanks :)

---

