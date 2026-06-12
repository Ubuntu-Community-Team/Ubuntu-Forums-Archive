---
title: "Creative Zen Video Convert Script"
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by Haegin on 2007-08-31
I pulled together a quick script to convert videos for my Creative Zen Vision:M this morning using mencoder and zenity and thought I would share. It dumps the encoded file in ~/Zen/Video. At some point I may expand this to encode whole directories at once if I decide I need that. At the moment it just asks for an input file and churns it through mencoder then tells you it's done. Let me know what you think.

```

#!/bin/bash
# Author:       HJMills < hjmills[at]gmail[dot]com >
# Title:        Creative Zen Vision:M Video Converter Script
# Version:      0.1
# Description:  Converts video into a format suitable for transfer to the Creative Zen Vision:M

# Conversion command used:
# mencoder file1.avi -o test1.avi -vf scale=320:240 -oac mp3lame -ovc xvid -xvidencopts bitrate=800

INPUT=`zenity --file-selection --title="Select the file to Convert"`
echo $INPUT
if [ "$INPUT" = "" ]; then
    echo "No input file selected - exiting"
    exit 0;
fi
FILENAME=`basename "$INPUT"`
if [ -d /home/$USER/Zen/Video ]; then
    echo "~/Zen/Video directory exists - using for output"
    OUTPUT="/home/$USER/Zen/Video/$FILENAME"
else
    echo "~/Zen/Video directory not found - creating and using for output"
    mkdir -p "/home/$USER/Zen/Video"
    OUTPUT="/home/$USER/Zen/Video/$FILENAME"
fi
echo $OUTPUT

echo 'mencoder "$INPUT" -o "$OUTPUT" -vf scale=320:240 -oac mp3lame -ovc xvid -xvidencopts bitrate=800'
mencoder "$INPUT" -o "$OUTPUT" -vf scale=320:240 -oac mp3lame -ovc xvid -xvidencopts bitrate=800
zenity --info --title="Encoding Completed" --text="$INPUT successfully encoded to $OUTPUT"

```

---

### Post by PhatBob55 on 2007-12-27
Hey

I like what you have done there 

Maybe you could help me with the problem I have with my Zen

see my post

[http://ubuntuforums.org/showthread.php?p=4021843#post4021843](http://ubuntuforums.org/showthread.php?p=4021843#post4021843)

Cheers

Bob

---

### Post by narehart on 2008-01-08
Nice script. Works for my Creative Zen 16GB as well.  Is there any way you could edit it to dump the video in my model?  Right now I have to transfer it over with a SD card.

Also, what would be the proper scale for fullscreen?

---

### Post by Explosive_Cornflake on 2008-01-09
I was testing this in work under cygwin.
```
$ ../MPlayer/mencoder.exe ./house.313.hdtv-lol.\[VTV\].avi -ovc lavc -lavcopts vcodec=mpeg4:v4mv:mbd=2:trell -vf expand=:::::4/3,scale=320:-11,harddup -oac mp3lame -lameopts fast:preset=medium -ffourcc DX50 -o House.S3E13.avi
```

That ended up at 193mb for 1 episode. I'll have to test it tongiht to see what it actually plays like though.

---

### Post by cdvddt on 2008-01-10
Hello,

Nice script.
I have a problem however :
When trying to convert flv file, I end up with a flv file too, where I expect a avi/wmv file : 
Creative zen can't play flv right ?

Thanks for your help.

Raphaël

---

### Post by spitf1r3 on 2008-01-11
I have a request: i have choosen the optimal encoding settings, for my ZEN Vision:M, using Mediacoder for windows, unfortunately it doesn't work well enough in linux, could you make a script using these settings?
Main problem is i want it to **encode XviD in 2-pass mode**..

1st pass:
```
mencoder.exe -vf pp=al:f,scale=320:240:0:0:0.00:0.50,hqdn3d=4:3:6,harddup -sws 2 "$(SourceFile)" -passlogfile "$(PassLogFile)" -ovc xvid -xvidencopts threads=1:autoaspect:qpel=:trellis:chroma_me:chroma_opt:hq_ac:quant_type=h263:bquant_ratio=150:bquant_offset=100:bvhq=1:me_quality=6:vhq=1:max_bframes=0:bitrate=$(VideoBitrate):turbo=1:pass=1 -oac pcm -o NUL
```

2nd pass:
```
mencoder.exe -vf pp=al:f,scale=320:240:0:0:0.00:0.50,hqdn3d=4:3:6,harddup -sws 2 "$(SourceFile)" -passlogfile "$(PassLogFile)" -ovc xvid -xvidencopts threads=1:autoaspect:qpel=:trellis:chroma_me:chroma_opt:hq_ac:quant_type=h263:bquant_ratio=150:bquant_offset=100:bvhq=1:me_quality=6:vhq=1:max_bframes=0:pass=2:bitrate=$(VideoBitrate) -af channels=2 -oac mp3lame -lameopts vbr=2:q=6:aq=2:highpassfreq=-1:lowpassfreq=-1 -o "$(DestFile)"
```

lame:
```
lame.exe --vbr-old -V 3 -q 0
```

Please help.

---

### Post by spitf1r3 on 2008-01-16
Anybody?:confused:

---

### Post by techforumz on 2008-02-25
spitf1r3:

There is absolutely no reason for you to use wine. All those programs are available in the main repository (Synaptic). So just install mencoder, mplayer, lame, and any other programs. Try that instead. Use the same command lines.

---

### Post by techforumz on 2008-03-01
The video works great. The audio... not so much. Mine read MPEG-1 Layer-3 at 48000Hz, and sounded like a broken FM radio.

---

### Post by bdjnk on 2008-03-09
> mencoder file1.flv -o file1.avi -vf scale=320:240 -oac mp3lame -ovc xvid -xvidencopts bitrate=800 This set of options for mencoder creates a slight audio sync issue with most converted videos. How could I ensure that the audio stays completely synced?

---

### Post by Morten on 2008-05-26
> **narehart said:**
> Nice script. Works for my Creative Zen 16GB as well.  Is there any way you could edit it to dump the video in my model?  Right now I have to transfer it over with a SD card.

I use Gnomad to transfer stuff to my Zen, works like a charm. Just plug in the Zen, and Gnomad recognizes it at once on startup.

---

