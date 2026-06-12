---
title: "How can I convert an AVI to MP4 for use on PS3"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by morpheous64 on 2007-10-31
Hi guys, noob here. I have recently said good bye to windows in favour of Ubuntu 7.04, all is great so far but i need to convert an AVI video to MP4 for use on my PS3, when on windows I used allok to do the job. Does anyone have any suggestions of a prog that can help.

Thanks guys

:popcorn:

---

### Post by timcredible on 2007-10-31
ffmpeg will do this.  it's command line though, so after installing it from synaptic, open the terminal program and do a ffmpeg --help to get the correct command for converting.  you may need other codecs downloaded also, which may require a little googling.

---

### Post by damvcoool on 2007-10-31
I posted the answer here.
[http://ubuntuforums.org/showthread.php?t=598291](http://ubuntuforums.org/showthread.php?t=598291)

using Avidemux, Video FFMPEG4 (lavc), audio FAAC, and container (MP4)

also in FFMPEG i was using a script that i will post some other day because i'm not at home.

the script was to convert all avi on a folder to a mp4 PS3 compatible :D

also i am looking for the comand line for avidemux to do this because since gutsy my ffmpeg script is getting files too smail and with bad quality.

---

### Post by damvcoool on 2007-11-02
ok I'm Back and here is the script.

i took the script from avidemux documentation and nodified it a little bit

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

echo ffmpeg -y -i \"$INPUT\" -acodec aac -ac 2 -ab 128 -vcodec mpeg4 -r 24 -b 800 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 \"$OUTPUT\" >> $VAR1

done
chmod 755 $VAR1
./$VAR1
rm $VAR $VAR1


```

---

### Post by timcredible on 2007-11-02
nice script!

---

### Post by damvcoool on 2007-11-02
the script above will only wotk on Feisty with the ffmpeg from [http://www.medibuntu.org](http://www.medibuntu.org) repository.

to make it work with Gutsy i had to modify it a little bit.

Gutsy Modified (you still need ffmpeg from [http://www.medibuntu.org](http://www.medibuntu.org))
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

Enjoy :D

---

### Post by chacham23 on 2007-11-02
can u explian me how I run this script?(stupid.... :P )

thanks :)

---

### Post by damvcoool on 2007-11-02
sure just copy this into a text file name the file script.sh and the make it executable.

put it on a folder with avi files and the double click, and if it asks something choose run from terminal.

---

