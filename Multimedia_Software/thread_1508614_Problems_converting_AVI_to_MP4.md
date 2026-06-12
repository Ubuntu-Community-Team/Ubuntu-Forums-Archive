---
title: "Problems converting AVI to MP4"
date: 2010-06-13
forum: Multimedia Software
---

### Post by fallenshadow on 2010-06-13
I am trying to convert AVI video to MP4 for a PSP.

I have tried both AcetoneISO and Mobile Media Converter... both fail.

The error message from AcetoneISO is:

> Unknown encoder 'libxvid'

This was from using the "Convert video for PSP" option under the "Video" menu.

Any help or advice would be appreciated.

---

### Post by nothingspecial on 2010-06-13
Follow [[COLOR="Magenta"]this guide[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095")

then copy and paste this 
```

#!/bin/bash

#convert avi to mp4
for f in *.avi 
    do 
    ffmpeg -i "$f" -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 \
    -flags +4mv -trellis 2  -cmp 2 -subcmp 2 -s 320x180 -metadata title="${f%.avi}.mp4" \
    "${f%.avi}.mp4"

done;
```


into a file and name it avi2mp4.sh

save it in the directory that has your avi files in it, then from the command line navigate to that directory and type ```
./avi2mp4.sh
```

I got tired trying to get different converters to do it properly for me. This has not failed.

---

### Post by fallenshadow on 2010-06-13
That script didn't work for me... I continued trying to solve my original problem and went according to this thread advice.

> [http://ubuntuforums.org/showthread.php?t=1017664](http://ubuntuforums.org/showthread.php?t=1017664)

My original problem was solved after reading that thread. However now AcetoneISO presents me with a different error message.

> Unknown encoder 'libfaac'

Obviously I need another package to solve this just like the first problem. Does anyone know what package I need?

---

### Post by nothingspecial on 2010-06-13
> **fallenshadow said:**
> That script didn't work for me... I continued trying to solve my original problem and went according to this thread advice.



My original problem was solved after reading that thread. However now AcetoneISO presents me with a different error message.



Obviously I need another package to solve this just like the first problem. Does anyone know what package I need?

Try ```
sudo apt-get install libfaac-dev 
```

---

### Post by fallenshadow on 2010-06-14
Installing that didn't work.. I have given up on using AcetoneISO.

As it turns out the video files PSP only accepts MP4's using the h.264 codec. I thought maybe I could use Pitivi to convert an avi into this codec.

However its not available in the Render options... the closest thing to it is h.263 but it doesn't work on the PSP.

Does somebody know how to get support for the h.264 codec?

---

### Post by bulletxt on 2010-06-19
> **fallenshadow said:**
> Installing that didn't work.. I have given up on using AcetoneISO.

As it turns out the video files PSP only accepts MP4's using the h.264 codec. I thought maybe I could use Pitivi to convert an avi into this codec.

However its not available in the Render options... the closest thing to it is h.263 but it doesn't work on the PSP.

Does somebody know how to get support for the h.264 codec?


What error do you get after installing libfaac?

---

### Post by ron999 on 2010-06-19
> **fallenshadow said:**
> 

Does somebody know how to get support for the h.264 codec?


Hi
The codec used by Ubuntu is x264.
To install this it needs the package libavcodec-extra-52.
There's a tutorial here that explains how to install ffmpeg and libavcodec-extra-52.
Use option **C. Medibuntu**. Here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1117283]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1117283")

When ffmpeg and x264 are installed you can use a program called **Winff**.
This has pre-sets for converting files for PSP.
Winff is here:- [http://winff.org/html_new/]("http://winff.org/html_new/")
Good luck
:guitar:

---

### Post by WinterRain on 2010-06-19
Get the ppa for Handbrake and use that. Very easy app to convert videos to mp4. [https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

---

