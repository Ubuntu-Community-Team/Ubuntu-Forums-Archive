---
title: "mencoder"
date: 2009-03-19
forum: Multimedia Software
---

### Post by anarhell on 2009-03-19
hello everyone , i have to problem with mencoder, i find this scritp . this convert the archive in the folder

#!/bin/bash

for f in $(ls ./ |grep -E .mov |grep -v .avi ) ; do
echo $f
xv=`echo "$f" | sed 's/\.\w*$/.avi/'` ;
mencoder -o $xv -ovc xvid -xvidencopts bitrate=1500 -oac mp3lame -lameopts cbr:br=128 $f
echo $f converted to $xv ;
done

the problem is with the spaces in white for example:

14 01. Wrap Up.mov

it read in this form

14
01.
warp
up.mov


thx for the help

---

### Post by anarhell on 2009-03-23
anyone please :) is urgent .. any solution for the spaces in white

---

