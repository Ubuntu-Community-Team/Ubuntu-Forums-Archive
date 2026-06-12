---
title: "Looking for a Video Converter"
date: 2014-05-21
forum: Multimedia Software
---

### Post by jay-blayk on 2014-05-21
I have a few video files i need to convert from AVI to MP4, I've tried quite a few of the apps listed on various websites including different forum posts on here, the ones I found either didn't convert all my files (some files produced errors) some converted them incorrectly and i ended up with audio but no video, I've tried some of the popular windows conversion tools through wine but no success there hence I've made a new post for people who have had this exact problem, instead of replying to various posts across cyberspace, hence this isn't a duplicate post, 

I'm running ubuntu 12.04 with gnome3,
I'm not a beginner at this sort of thing but i'm not an expert either so step by step instructions would be appreciated

---

### Post by ssam on 2014-05-21
which programs did you try? what error messages did you get?

Also note that 12.04 is a 2 year old release (12 means 2012). 14.04 contains newer versions of applications that fix many bugs.

---

### Post by Yellow Pasque on 2014-05-21
What kind of video is in the avi container?
```
sudo apt-get install mediainfo
mediainfo file.avi
```

---

### Post by monkeybrain20122 on 2014-05-21
> **jay-blayk said:**
> I have a few video files i need to convert from AVI to MP4, I've tried quite a few of the apps listed on various websites including different forum posts on here, the ones I found either didn't convert all my files (some files produced errors) some converted them incorrectly and i ended up with audio but no video, I've tried some of the popular windows conversion tools through wine but no success there hence I've made a new post for people who have had this exact problem, instead of replying to various posts across cyberspace, hence this isn't a duplicate post, 

I'm running ubuntu 12.04 with gnome3,
I'm not a beginner at this sort of thing but i'm not an expert either so step by step instructions would be appreciated

Well if you have tried many things including those recommended by various forum posts and they don't work you should at least tell people what you have tried, if just to prevent people from giving you the same recommendations. ;) Of course it is also possible that you didn't do it right (say a wrong parameter in ffmpeg).

---

### Post by HiImTye on 2014-05-21
here's the script I use to convert to mp4 with ffmpeg```
#!/bin/bash

# new file name
F=${1##*/}
F="_converted/${F%.*}.mp4"
# if the file already exists then we have no work to do
if [ ! -f "$F" ]; then    

 # colorized output
 RS="\033[0m"    # reset
 HC="\033[1m"    # hicolor
 FRED="\033[31m" # foreground red
 FGRN="\033[32m" # foreground green
 FCYN="\033[36m" # foreground cyan
 # start our top display
 echo -e "$FCYN"\*\* 2mp4 settings \*\*"$RS"
 # check if $rate is defined
 if [ -z "$rate" ]; then
  # set it
  rate="29.985"
 fi
 # print our rate
 echo -e "$HC$FGRN"rate: "$rate$RS"
 # ditto, flags
 if [ -z "$flags" ]; then
  flags="+aic+mv4"
 fi
 echo -e "$HC$FGRN"flags: "$flags$RS"
 # check if we have extra switches
 if [ -n "$extraa" ]; then
  if [ -n "$extrav" ]; then
   # yes, both
   extra="$extraa $extrav"
  else
   # yes, audio
   extra="$extraa"
  fi
 elif [ -n "$extrav" ]; then
  # yes, video
  extra="$extrav"
 fi
 # check if extra was defined, above
 if [ -n "$extra" ]; then
  # it was, echo it
  echo -e "$FRED"extra options: "$extra$RS"
 fi
 # close our top display
 echo -e "$FCYN"\*\* \*\* \*\* \*\ *\* \*\* \*\*"$RS"

 # check if our output folder exists
 if [ ! -d "_converted" ]; then
  # no, create it
  mkdir _converted
 fi

 # check if we have extra switches
 if [ -n "$extraa" ]; then
  if [ -n "$extrav" ]; then
   # yes, both
   ffmpeg -i "$1" -r "$rate" -acodec aac -strict -2 -b:a 128k -ac 2 "$extraa" -vcodec mpeg4 -b:v 1200k "$extrav" -flags "$flags" "$F"
  else
   # yes, audio
   ffmpeg -i "$1" -r "$rate" -acodec aac -strict -2 -b:a 128k -ac 2 "$extraa" -vcodec mpeg4 -b:v 1200k -flags "$flags" "$F"
  fi
 elif [ -n "$extrav" ]; then
  # yes, video
  ffmpeg -i "$1" -r "$rate" -acodec aac -strict -2 -b:a 128k -ac 2 -vcodec mpeg4 -b:v 1200k "$extrav" -flags "$flags" "$F"
 else
  # no
  ffmpeg -i "$1" -r "$rate" -acodec aac -strict -2 -b:a 128k -ac 2 -vcodec mpeg4 -b:v 1200k -flags "$flags" "$F"
 fi

fi
```

---

### Post by mdalacu on 2014-05-22
Have you tried this : [http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html](http://dmsimpleapps.blogspot.ro/2014/04/dmmediaconverter.html)

---

