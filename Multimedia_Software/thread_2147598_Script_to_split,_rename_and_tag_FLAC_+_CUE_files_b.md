---
title: "Script to split, rename and tag FLAC + CUE files by txust"
date: 2013-05-22
forum: Multimedia Software
---

### Post by mikeym on 2013-05-22
Hi Everybody,

I came across a script on this forum for splitting and renaming FLAC + CUE file combinations: [http://ubuntuforums.org/showthread.php?t=1084840](http://ubuntuforums.org/showthread.php?t=1084840)

It was posted by [txust]("http://ubuntuforums.org/member.php?u=781922"). 

I decided to make use of it, but found that there were a few bugs. It failed if there were spaces in the file-names. It also had a problem that a program it relied on "cuebreakpoints" fails with one type of CUE file. 

I fixed it and was going to post it on the original thread but it, was closed - it was from 2009. So I'm posting it here and notifying the original author. No sure that he's active any more though.

Any maybe it will be of use to someone else, it was for me. :)

```

#!/bin/bash

clear

# Introduction

echo
echo
echo                   "FLACCUE2FLAC"
echo
echo
echo
echo "This script will convert, split and tag FLAC files with an associated cue sheet"
echo
echo
echo "WARNING: THIS SCRIPT WILL AUTOMATICALLY INSTALL SOME NECESSARY PACKAGES IF NOT ALREADY INSTALLED"
echo
echo
echo
echo

# Filenaming template

# %a author
# %A album
# %g genre
# %n track number
# %t title
# %d date
# %c comments

# This is obviously the *correct* naming convetion :P
TEMPLATE='%A - %n - %a - %t'

# This will check if all packages needed are present in the system, and will install them if not.

FLAC=`which flac`
if [ -z "$FLAC" ]; then
  echo "ERROR (Don't worry) ;-)"
  echo "FLAC is not in your system, automatically installing..."
  sudo apt-get update && sudo apt-get install flac -y
  clear
  echo "OK NOW, PROCEEDING..."
  echo
fi

CUE=`which cuebreakpoints`
if [ -z "$CUE" ]; then
  echo "ERROR (Wish every error were like this one...) ;-)"
  echo
  echo "cuetools not present, automatically installing..."
  sudo apt-get update && sudo apt-get install cuetools -y
  clear
  echo "OK NOW, PROCEEDING..."
  echo
fi

SHN=`which shntool`
if [ -z "$SHN" ]; then
  echo "ERROR (Not the end of the world, anyway) ;-)"
  echo
  echo "shntool is not around here, let's get it..."
  sudo apt-get update && sudo apt-get install shntool -y
  clear
  echo "OK, PROCEEDING..."
  echo
fi

LL=`which lltag`
if [ -z "$LL" ]; then
  echo "OH, MY GOD! ;-)"
  echo
  echo "lltag is not in your computer, installing..."
  sudo apt-get update && sudo apt-get install lltag -y
  clear
  echo "AT LAST, PROCEEDING..."
  echo
fi

# Now it will check if we have chosen a cue file

for i in "$@"; do
  # There's no point in checking for a  mixed case file extension if we're 
  # going to rely on it having a lower case extenstion later on
  case "$i" in
    *.cue)
      echo "Checking if file $i is a .cue file...";;
    *)
      echo "Warning: File $i is not a .cue file. Aborting."
      continue
  esac
  
  # Processing files
  
  FILENAME=$(basename "$i" .cue)
  TMPCUE=$(mktemp --suffix=.cue)
  cp "$FILENAME.cue" "$TMPCUE"
  
  # Try to "fix" incompatible cue files (this is a guess but works for me)
  if grep "^\s*INDEX 00 00:00:00\s*$" "$TMPCUE" > /dev/null; then
    echo "Attempting to fix incompatible cue file..."
    sed -i -e "/^\s*INDEX 01/d" -e "s/^\(\s*\)INDEX 00/\1INDEX 01/" "$TMPCUE"
  fi

  echo "Splitting files..."
  cuebreakpoints  "$TMPCUE"
  shnsplit -o flac -f "$TMPCUE" "$FILENAME.flac"
  
  echo "Adding tags..."
  cuetag "$TMPCUE" split-track*.flac
  
  # This will rename files using the strucure "track-number title", the one I like, but it can be easyly changed using common parameters. Please read lltag manual for more information.
  
  echo "Renaming files..."
  lltag --yes --no-tagging --rename "$TEMPLATE" $(ls split-track*.flac)
  echo
  echo
  echo "Process ended."
done

# cleaning up
rm "$TMPCUE"

```

---

### Post by txust on 2013-05-22
Hi!! I'm so happy this was useful to you. It worked fine for me, but commands and so might have changed in the mean time. I'll check your changes out and tell you my feedback. Thank you for your work, enjoy!!

---

### Post by mikeym on 2013-05-23
Hi txust, 

Good to see you're still active. :) 

Yes, thanks for the script. The issues fixed were mainly the ones mentioned on the original thread (nothing major). You'd missed putting quotes around some of filenames so the script balked at input files (cue / flac) which had spaces in them. There was an issue with *cuebreakpoints*, which had nothing to do with your script, where it fails with one of the variants of *cue* layouts which I've attempted to *fix* with a big old hack. And a very minor thing, I changed *aptitude* to *apt-get* because not everyone has the former installed but everyone has the latter.

So nothing to major to change, it still worked great after a few years. :)

---

### Post by UbuntAlec on 2014-04-21
Thank-you so much for this handy little script! I've been using it with 12.04 for over a year (much handier than my previous commandline approach) and have just upgraded to 14.04 and it works fine with it as well.

Cheers,
Alec

---

