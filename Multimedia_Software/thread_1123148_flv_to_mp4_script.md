---
title: "flv to mp4 script"
date: 2009-04-11
forum: Multimedia Software
---

### Post by Ejas12 on 2009-04-11
Hi everyone, I wanted to make a script to get all the files in a folder converted from flv to mp4 (this with especial caracteristicas that are required by my cellphone) and i found one that looked promising here at the [URL="http://www.helmutgranda.com/2009/02/05/covert-mov-files-to-flv-with-ffmpeg/"]Helmut Granda page
[/URL]

I modified it to my needs, this is what i got  
```

#!/bin/bash
# Convert all flv in a directory to mp4 for rocker e2
ext=.mp4
for file in *.flv; do
currmov=$file$ext
ffmpeg -r 15  -i $file  -b 296k -s 320x240 -vcodec mpeg4 -acodec aac  $currmov
done

```
Now, as you may notice, this isnt flashy at all (because i am just an amateur, no programing skills at all :lolflag:) but it worked for my cellphone.
Anyway, what i wanted to ask is for help to make it better, i.e I wanted to make it delete the source files (because I just copy them in the folder that I need), and also get off the flv extension (this script maintains the full name, including the flv part).
Thanks in advance

---

### Post by mc4man on 2009-04-11
you could try this (using your parameters

```
#!/bin/bash
for f in *.flv; do ffmpeg -r 15 -i "$f" "${f%.flv}.mp4" -b 296k -s 320x240 -vcodec mpeg4 -acodec aac; done
rm *.flv
```

---

### Post by jmore9 on 2009-04-11
Or you could just install handbrake.  It works very well.  You have several options for conversions.

[http://handbrake.fr](http://handbrake.fr)

I have been using it for a while now.

---

### Post by Ejas12 on 2009-04-11
Thank you everyone
That new script rocks!!!!  :guitar:
As for HandBrake, I will give it a try thanks for the tip pal

---

### Post by sierd on 2011-03-02
i use:
```
#!/bin/bash
#
# Convert flv files to mp4 files
IFS=$'\t\n'

cd ~/Downloads/
dir=./tmp-dir_flv_to_mp4_convert
mkdir $dir/
for b in `find ./ -type f -name '*.flv'`; do
        e=`echo "$b"|sed 's/\.flv$'//`
        ffmpeg -i $b -acodec libmp3lame -ab 320k -vcodec mpeg4 -b 1200kb -r 25 $dir/$e.mp4
          mv ./$dir/$e.mp4 ../Video\'s/$e.mp4
          rm -f ./$b
done
rmdir $dir
exit

```
I hope someone else can use it to :)

---

