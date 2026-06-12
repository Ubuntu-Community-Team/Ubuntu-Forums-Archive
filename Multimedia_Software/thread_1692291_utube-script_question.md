---
title: "utube-script question"
date: 2011-02-21
forum: Multimedia Software
---

### Post by hobels on 2011-02-21
Hi! A friend of mine gave me following script to convert utube-links to mp3. ```
#!/bin/bash
  [ -e ~/music/uTube ] || mkdir ~/music/uTube
  url=
     while [ -z "$url" ]; do
       read -p "
##################################
copy utube-url here
################################## " url ;
       [ -z "$url" ] && echo "
##########################################
type something!
##########################################"
     done

  if [ -z $2 ]
     then
        read -p "
##################################
mp3's name??? 
################################## " of ;
     else
        of=$2
  fi

  youtube-dl --max-quality=FORMAT --output=tmpout.mp4 ${url} ;

  ffmpeg -i ./tmpout.mp4 -acodec libmp3lame -ab 192k "${of}".mp3
  lame -hb 192 ./"${of}".mp3 ./a"${of}".mp3
  mv ./a"${of}".mp3 ~/music/uTube/"${of}".mp3

  rm "${of}".mp3
  rm tmpout.mp4
```now my question. is it possible to change the the "read" in "mp3's name???" so i can not only type but also use the arrow keys to switch the position of the cursor in the bash so i can edit the name in case i forgot something. every time i try to do so i get following ```
^[[D
``` instead that the cursor goes left. Would really appreciate your help here! :)

greets

---

### Post by aeiah on 2011-02-21
try read -e instead of read -p

it'll let you arrow back and forth, although the script may now not read what you put. worth a shot :p

---

