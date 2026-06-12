---
title: "Script To Shuffle Your TV Without Updating Playlists"
date: 2009-11-10
forum: Multimedia Software
---

### Post by VH-BIL on 2009-11-10
I use mplayer to play my TV episodes. I used to have playlists to play my episodes shuffled in mplayer. What became a problem is adding new episodes then having to recreate new playlist files.

I now play TV episodes that I want shuffled through this script I have created which will  generate the playlist file and then play with mplayer.

The script has an array for TV shows that you would like to have shuffled, and also an array of TV shows you would like combined into a single shuffled TV playlist. 

The script is easy to edit to add your own TV shows and set your own paths. It is one of the first scripts I have created and the first useful script I have created.

Let me know what you think
```

#!/bin/bash
# ================================================================================
#    Project      : TV Shuffle
#    Author       : Bill Payne
#    Date         : 10th Nov 2009
#    Info         :
# The "DestPath" variable holds the path of where to write all the
# playlists.
#
# The variable "MixedDestPath" holds the path and filename for the playlist
# of the mixed tv.
#
# The "TV_Count" variable is then number of individual tv shows to be
# displayed in the menu.
#
# Arrays "TV_Name" and "TV_Path" hold information about the tv shows in
# the menu. "TV_Name" is the name of the TV show and "TV_Path" is the path
# to where all the tv episodes are stored. The number of tv episodes must
# be recorded in "TV_Count"
#
# The "Mixed_Count" variable is the number of tv shows to be put combined
# into the mixed TV playlist.
#
# Just like the "TV_Name" and "TV_Path" variables the "Mixed_Name" and
# Mixed_Path hold the name and file path of the TV shows to be in the
# mixed TV playlist.
#
# This is one of the first scripts I have made. I work as a programmer
# but as a C# programmer. I wanted an easy way of playing my TV shows shuffled
# while not having to update playlists when adding new episodes. 
# ================================================================================

# The Destination Path Of All The Playlists
DestPath="/home/bill/playlists/"
# The Path And Filename Of The Mixed TV Playlist
MixedDestPath="/home/bill/playlists/MixedTV.plist"

# Colour Codes
black='\E[30;40m'
red='\E[31;40m'
green='\E[32;40m'
yellow='\E[33;40m'
blue='\E[34;40m'
magenta='\E[35;40m'
cyan='\E[36;40m'
white='\E[37;40m'

# TV Shows
TV_Count=17
TV_Name[0]="Air Crash Investigation"
TV_Path[0]="/Repository/Media/TV/Air Crash Investigations"
TV_Name[1]="American Dad"
TV_Path[1]="/Repository/Media/TV/American Dad"
TV_Name[2]="How I Met Your Mother"
TV_Path[2]="/Repository/Media/TV/How I Met Your Mother"
TV_Name[3]="Junkyard Wars"
TV_Path[3]="/Repository/Media/TV/Junkyard Wars"
TV_Name[4]="Kenny vs Spenny"
TV_Path[4]="/Repository/Media/TV/Kenny vs Spenny"
TV_Name[5]="My Name Is Earl"
TV_Path[5]="/Repository/Media/TV/My Name Is Earl"
TV_Name[6]="MythBusters"
TV_Path[6]="/Repository/Media/TV/MythBusters"
TV_Name[7]="Numb3rs"
TV_Path[7]="/Repository/Media/TV/Numb3rs"
TV_Name[8]="Red Dwarf"
TV_Path[8]="/Repository/Media/TV/Red Dwarf"
TV_Name[9]="Scrubs"
TV_Path[9]="/Repository/Media/TV/Scrubs"
TV_Name[10]="Seinfeild"
TV_Path[10]="/Repository/Media/TV/Seinfeild"
TV_Name[11]="South Park"
TV_Path[11]="/Repository/Media/TV/South Park"
TV_Name[12]="Testees"
TV_Path[12]="/Repository/Media/TV/Testees"
TV_Name[13]="The Simpsons"
TV_Path[13]="/Repository/Media/TV/The Simpsons"
TV_Name[14]="The Universe"
TV_Path[14]="/Repository/Media/TV/The Universe"
TV_Name[15]="Trailer Park Boys"
TV_Path[15]="/Repository/Media/TV/Trailer Park Boys"
TV_Name[16]="XFiles"
TV_Path[16]="/Repository/Media/TV/XFiles"

# Mixed TV
Mixed_Count=7
Mixed_Name[0]="How I Met Your Mother"
Mixed_Path[0]="/Repository/Media/TV/How I Met Your Mother"
Mixed_Name[1]="Seinfeild"
Mixed_Path[1]="/Repository/Media/TV/Seinfeild"
Mixed_Name[2]="South Park"
Mixed_Path[2]="/Repository/Media/TV/South Park"
Mixed_Name[3]="The Simpsons"
Mixed_Path[3]="/Repository/Media/TV/The Simpsons"
Mixed_Name[4]="Trailer Park Boys"
Mixed_Path[4]="/Repository/Media/TV/Trailer Park Boys"
Mixed_Name[5]="Two And A Half Men"
Mixed_Path[5]="/Repository/Media/TV/Two And A Half Men"
Mixed_Name[6]="X-Files"
Mixed_Path[6]="/Repository/Media/TV/XFiles"


DisplayMenu()
{
  echo -en $white
  clear
  echo -en $white
  echo "TV Shuffle Script"
  echo -en $red
  echo "================="
  echo
  for ((cnt=0 ; cnt<=TV_Count-1 ; cnt++))
  do
    if [ $cnt -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo ${TV_Name[cnt]}
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $cnt
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo ${TV_Name[cnt]}
    fi
  done
    if [ $TV_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Mixed TV"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Mixed TV"
    fi
    let "TV_Count += 1"
    if [ $TV_Count -lt 10 ]
    then
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ")  "
      echo -en $white
      echo "Display Mixed TV"
    else
      echo -en $cyan
      echo -n "("
      echo -en $blue
      echo -n $TV_Count
      echo -en $cyan
      echo -n ") "
      echo -en $white
      echo "Display Mixed TV"
    fi
    let "TV_Count -= 1"
  echo
  echo -n "Make A Selection :"
}

DisplayMixedTV()
{
  echo  
  for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    echo -en $white
    echo ${Mixed_Name[cnt]}
  done
  echo
}

ShuffleEpisode()
{
  cd /
  find "${TV_Path[$1]}" > "$DestPath${TV_Name[$1]}.plist"
  mplayer -playlist "$DestPath${TV_Name[$1]}.plist" -shuffle
}

MixedTV()
{
  echo "" > $MixedDestPath
  cd /
    for ((cnt=0 ; cnt<=Mixed_Count-1 ; cnt++))
  do
    find "${Mixed_Path[$cnt]}" > "$DestPath${Mixed_Name[$cnt]}.plist"
    echo "" > $MixedDestPath"_cat"
    cat "$DestPath${Mixed_Name[$cnt]}.plist" $MixedDestPath > $MixedDestPath"_cat"
    rm $MixedDestPath
    mv $MixedDestPath"_cat" $MixedDestPath
  done
  mplayer -playlist $MixedDestPath -shuffle
}

DisplayMenu
read input

if [ $input -eq $TV_Count ]
then
  MixedTV
fi

let "TV_Count += 1"
if [ $input -eq $TV_Count ]
then
  DisplayMixedTV
fi
let "TV_Count -= 1"

if [ $input -lt $TV_Count ]
then
  ShuffleEpisode $input
fi

```

I have added the script as code and attached it as a file.

---

