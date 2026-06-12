---
title: "automated download, encode, upload to megaupload.com"
date: 2010-09-18
forum: Multimedia Software
---

### Post by mysoogal on 2010-09-18
automated download encode, upload clips to megaupload using terminal and plowshare

```
    #!/bin/bash
    # Remote Download - Encoded to MP4 & Theora - automated Upload to Megaupload.com
    # automated logic, mysoogals
    # linux dependency ubuntu 8.10 - 10.04 - linux mint 9- http://code.google.com/p/plowshare/
    # build qt-faststart - ffmpeg - http://ubuntuforums.org/showthread.php?t=786095

# remote url input
    wget="http://amd.co.at:8083/AFV_-_slide1.wmv"
# change filename.Extension to whatever it is like mp4,or mpg etc
    ffmpeg="AFV_-_slide1.wmv"
# just rename file do not touch .mp4
    loop="AFV_-_slide1.mp4"
    ffmpegout="$loop"
    qtinput="$loop"
    qtout="$loop"

    wget $wget && ffmpeg -i $ffmpeg -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 $ffmpegout && qt-faststart $ffmpegout $ffmpegout.qt.mp4 && plowup -a user:pass -d "$ffmpegout.qt.mp4" $ffmpegout.qt.mp4 megaupload && rm $ffmpeg && rm $ffmpegout && chmod 777 $ffmpegout.qt.mp4 && ffmpeg2theora $ffmpegout.qt.mp4 $ffmpegout.qt.ogv && chmod 777 $ffmpegout.qt.ogv && plowup -a user:pass -d "$ffmpegout.qt.ogv" $ffmpegout.qt.ogv megaupload
```

user:pass change to your megaupload account

questions, ask me in pm or here

---

### Post by mysoogal on 2010-09-18
local version, same thing but you can move the file somewhere else, later version will add support for remote ftp server upload 

```
    #!/bin/bash
    # Remote Download - Encoded to MP4
    # automated logic, mysoogals
    # linux dependency ubuntu 8.10 - 10.04 - linux mint 9 -
    # build qt-faststart -&- ffmpeg - http://ubuntuforums.org/showthread.php?t=786095


    class_wget="http://amd.co.at:8083/TheKnack_1.mpg"
    class_ffmpeg_reader="TheKnack_1.mpg"
    class_file_loop="TheKnack_1.mp4"
    ffmpegout="$class_file_loop"
    qtinput="$class_file_loop"
    qtout="$class_file_loop"

wget $class_wget && ffmpeg -i $class_ffmpeg_reader -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre slow -crf 22 -threads 0 $ffmpegout && qt-faststart $ffmpegout $ffmpegout.qt.mp4 && rm $class_ffmpeg_reader && rm $ffmpegout && chmod 777 $ffmpegout.qt.mp4 && mv $ffmpegout.qt.mp4 /var/www/uploads/
```

---

