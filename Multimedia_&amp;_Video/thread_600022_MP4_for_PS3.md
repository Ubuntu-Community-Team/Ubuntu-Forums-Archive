---
title: "MP4 for PS3"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by damvcoool on 2007-11-01
I have successfully created a script that will transform AVI to MP4 but since i upgraded to gutsy i am not able to make the script work anymore.

```

#!/bin/bash

## Initialing Variables Used by the script
VAR="files.txt"
VAR1="exe.sh"

## Creating Second Script with the actual ffmpeg Values
echo \#/bin/bash >> $VAR1



ls *.avi | sort > $VAR # Collect the files in the current directory
cat $VAR | while read line; do
  INPUT=$(echo ${line}) # Grab the nxt new filename
OUTPUT=${INPUT%.avi}
OUTPUT+=".mp4"

[COLOR="Blue"]echo ffmpeg -y -i \"$INPUT\" -acodec aac -ac 2 -ab 128 -vcodec mpeg4 -r 24 -b 800k -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 \"$OUTPUT\" >> $VAR1[/COLOR] ## command line itself


done
chmod 755 $VAR1
./$VAR1
rm $VAR $VAR1


```

now i found that this was because the default ffmpeg does not support mp4 container as output so i compiled my own, but now i get very bad quallity videos no matter what setting i modify.


i have since been converting my files with avidemux but i am now tired of having to click so many times.

has anyone know a line to conver from divX or Xdiv or anything from avi container to mp4 with transcode or mencoder, or even avidemux.

I know avidemux has command line option but i have not been succesful in learning it.

[COLOR="Blue"]NOTE: if you want the same quality that you get on the AVI just add [COLOR="Red"]-sameq[/COLOR] [COLOR="SeaGreen"]BEFORE[/COLOR] [COLOR="Red"]-acodec[/COLOR][/COLOR]

---

### Post by damvcoool on 2007-11-02
no i have found a fix :D i just looked into man ffmpeg and took out what was not there.

this version of the script will work on Gutsy but we have to install the ffmpeg from [http://www.medibuntu.org](http://www.medibuntu.org) Repository.

```

#!/bin/bash

## Initialing Variables Used by the script
VAR="files.txt"
VAR1="exe.sh"

## Creating Second Script with the actual ffmpeg Values
echo \#/bin/bash >> $VAR1

ls *.avi | sort > $VAR # Collect the files in the current directory
cat $VAR | while read line; do
  INPUT=$(echo ${line}) # Grab the nxt new filename
OUTPUT=${INPUT%.avi}
OUTPUT+=".mp4"

echo ffmpeg -y -i \"$INPUT\" -acodec aac -ac 2 -ab 128 -vcodec mpeg4 -r 24 -b 800k -mbd 2 -aic 2 \"$OUTPUT\" >> $VAR1


done
chmod 755 $VAR1
./$VAR1
rm $VAR $VAR1


```

---

### Post by damvcoool on 2007-11-05
Please Take advantage of this script.

 the first post has a good script now, I modified it now works on Feisty and  Gutsy (I tested it).

please add feedback.

---

### Post by specvthis on 2007-11-15
This is incredible.  Even though they are adding support I am currently trying to convert all my videos to mp4.  I will be psyched if it works, and I do not have to install ubuntu on my ps3.  I would rather have my videos in mp4 anyways...This rocks!  Will let you know if my ps3 recognizes the files

---

### Post by hebetude on 2007-11-22
"aac" not found, used libfaac instead.  I compile ffmpeg from source, but I can't imagine medibuntu rewrote the codec names.  

AVI's work great, I was disappointed that I still can't convert any of my HD stuff with these ffmpeg settings.  On the topic of Avidemux, even if you use the commandline you have to have an active Xsession.  Thus, making the commandline capabilities of avidemux useless.

Thanks for writing this I will use it a lot, probably in a single mode way instead of mass transcoding all the files in a directory :P.

---

### Post by soc91 on 2007-11-23
Im starting to give up on this transcoding all my avi´s to mp4 for my ps3. Every time I have transcoded something, the ps3 recognize the file as unknown data. Does anyone else have the same problem?

---

### Post by hebetude on 2007-11-23
How are you transcoding and is your PS3 updated?

---

### Post by soc91 on 2007-11-23
Yes  my ps3 is updated. I know what I was doing wrong now. I had forgot to update ~/.mediatomb/config.xml with the following: <protocolInfo extend="yes"/>.
Now it works fine :)

---

### Post by grapnell on 2008-07-20
I have tried everything possible.  I have searched thousands of threads, but I cannot, for the life of me, create a playable video file for my PS3.  My PS3 will play almost any .mpg video that I download from the net, but if its not mpg format, it won't play.  Also, If I try to transcode it to mpg, my ps3 just says data corrupted, or unsupported data.  Even though these transcoded files will play just fine on my computer.  I have tried transcoding these videos a million different ways, using mencoder, ffmpeg, avidemux, the list goes on and on.  I have tried transcoding them to both MP4 and MPG formats, yet the PS3 will not read them.  I have tried various GUIs such as kino, vlc, vive, winff etc etc.  All I want to do is transcode some of my Southpark videos, some are in avi and some are in mp4 format when I download them.  BTW, I though PS3 was supposed to be able to play MP4, why won't it play the ones I download?  Can some give me a command that will convert xxx.mp4 to PS3 readable format.  and the same for xxx.avi 2 ps3 format.  I would greatly appreciate it.

Thanks,
Grap

---

### Post by Dark4eons on 2008-07-23
well first things first, did you update your ps3 to the latest firmware available?
and if yes, I'd suggest you network your ps3 & computer and use mediatomb
btw the ps3 has some problems with xvid playback and I don't even mention mkv, mp4 & divx which randomly works from time to time... stick with your pc for media files or buy a good media center for the living room

---

