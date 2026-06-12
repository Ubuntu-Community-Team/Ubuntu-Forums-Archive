---
title: "split single lossless cuefile to tracks (flac/wv/mp3/ape/ogg)"
date: 2011-01-08
forum: Multimedia Software
---

### Post by shantiq on 2011-01-08
found [this]("http://www.webupd8.org/2011/01/split-single-lossless-audio-files-to.html") today on my travels


```


########################################################################
##        Split Lossless Audio by Cue File
##        By CokiDVD
##        Contains some code from: 
##        [http://forum.ubuntu.org.cn/viewtopic.php?f=74&t=67658](http://forum.ubuntu.org.cn/viewtopic.php?f=74&t=67658)
##
##        IMPORTANT:
##        Needs shntool >= 3.0.8 For WAVPACK files (ppa:adrian-m-benson/ppa)
########################################################################

#!/bin/bash

# Functions
# Input check for flac
is_flac ()
{
    file -b "$1" | grep 'FLAC' || echo $1 | grep -i '\.flac$'
}
# Input check for ape
is_ape ()
{
    file -b "$1" | grep 'Monkey' || echo $1 | grep -i '\.ape$'
}
# Input check for wavpack
is_wavpack ()
{
    file -b "$1" | grep 'data' || echo $1 | grep -i '\.wv$'
}
########################################################################
# Check for shntool package
if !(which shnsplit 2>/dev/null)
then
    zenity --error --title="ERROR" --text="This script requires the shntool package"
    exit 1
fi

# Check for cuetools package
if !(which cuetag 2>/dev/null)
then
    zenity --error --title="ERROR" --text="This script requires the cuetools package"
    exit 1
fi

# Check for flac package
if !(which flac 2>/dev/null)
then
    zenity --error --title="ERROR" --text="This script requires the flac package"
    exit 1
fi

# Check for mac package
if !(which mac 2>/dev/null)
then
    zenity --error --title="ERROR" --text="This script requires the mac package"
    exit 1
fi

# Check for wavpack package
if !(which wavpack 2>/dev/null)
then
    zenity --error --title="ERROR" --text="This script requires the wavpack package"
    exit 1
fi

# Check for lame package
if !(which wavpack 2>/dev/null)
then
    zenity --error --title="ERROR" --text="This script requires the lame package"
    exit 1
fi

# Check for mp3info package
if !(which mp3info 2>/dev/null)
then
    zenity --error --title="ERROR" --text="This script requires the mp3info package"
    exit 1
fi

########################################################################

# Some checks before start splitting

if  !(is_ape "$1" || is_flac "$1" || is_wavpack "$1")
then
    zenity --error --title="ERROR" --text="This script only takes FLAC, APE and WAVPACK files"
        exit 1
fi


file=`zenity --file-selection --file-filter "*.cue" --title="Select .cue file"`

      case $? in
               0)
                      echo "\"$file\" selected.";;
               1)
                      zenity --error --title="ERROR" --text="No .cue file selected";
      exit 1;;
              -1)
                     zenity --error --title="ERROR" --text="No .cue file selected";
      exit 1;;
      esac 

i=0
while [ -f "temp$i" ]; do
    i=$(($i+1))
done
> temp$i
iconv -f gb18030 -t utf8 *.cue > "temp$i" && mv "temp$i" *.cue
rm -f "temp$i"

tracks=`gawk -vRS="TRACK" 'END {print NR-1}' "$file"`

nperformer=`gawk -vRS="PERFORMER" 'END {print NR-1}' "$file"`

all_titles=`gawk -vRS='TRACK' -vFS='\n' \
        '{j=0;for(i=1;i<=NF;i++){if($i~/TITLE/){print $i;j=1}}};j==0 {print "TITLE \"#####\""}' "$file" | \
        gawk -F "\"" 'NR>=2 {printf("%s|",$2)}'`

if [ "$nperformer" -ne 1 ]
then
    all_artists=`gawk -vRS='TRACK' -vFS='\n' \
    '{j=0;for(i=1;i<=NF;i++){if($i~/PERFORMER/){print $i;j=1}}};\
    j==0 {print "PERFORMER \"#####\""}' "$file" | gawk -F "\"" 'NR>=2 {printf("%s|",$2)}'`
else
    oneartist=`gawk -vRS='TRACK' -vFS='\n' \
    '{j=0;for(i=1;i<=NF;i++){if($i~/PERFORMER/){print $i;j=1}}};j==0 {print "PERFORMER \"#####\""}' "$file" | \
    gawk -F "\"" 'NR==1 {printf("%s",$2)}'`
fi

album=`gawk -vRS='TRACK' -vFS='\n' \
'{j=0;for(i=1;i<=NF;i++){if($i~/TITLE/){print $i;j=1}}};j==0 {print "TITLE \"#####\""}' "$file" | \
gawk -F "\"" 'NR==1 {printf("%s",$2)}'`

date=$(egrep '^REM DATE ' "$file" | cut -c 10- | tr -d '\r')
genre=$(egrep '^REM GENRE ' "$file" | cut -c 11- | tr -d '\r')

oformat=$(zenity --title "Output Format" --text "Please Select the Output Format" --list --radiolist --column "Select" --column "Format" True Flac False Mp3-320kbps False Mp3-192kbps)

if [ $? = 1 ]
then
    exit 0
fi

if [ "$oformat" = "Flac" ]
    then
        shnsplit -f "$file" -o "flac flac -V --best -o %f -" "$1" -t "%n - %t" 2>&1 | \
        gawk -vvar=$tracks 'NR>=1 && NR<=var {print "#Track ",NR," of ", var;print (NR-1)*100/var};{fflush();}' | \
        (if `zenity --title="Splitting Tracks..." --progress --auto-close --percentage=0`;
        then
        echo 'done'
    else
      killall shnsplit
      exit 1
    fi)
        
        if [ $? = 1 ]
        then
            exit 0
        fi
        
        rm -f 00*pregap*

        j=1
        while [ $j -le $tracks ]
        do
            title=${all_titles%%|*}
            if [ "$nperformer" -ne 1 ]
            then
                artist=${all_artists%%|*}
            else
                artist=$oneartist
            fi
            num=`printf "%02d" $j`
            if [ "$title" != "#####" ]; then metaflac --set-tag=TITLE="$title" "${num} - $title.flac"; fi
            if [ "$artist" != "#####" ]; then metaflac --set-tag=ARTIST="$artist" "${num} - $title.flac"; fi
            if [ "$album" != "#####" ]; then metaflac --set-tag=ALBUM="$album" "${num} - $title.flac"; fi
            metaflac --set-tag=TRACKNUMBER="$j" --set-tag=DATE="$date" --set-tag=GENRE="$genre" "${num} - $title.flac"
            j=$(( $j + 1 ))
            all_titles=${all_titles#*|}
            all_artists=${all_artists#*|}
        done

    else
        if [ "$oformat" = "Mp3-320kbps" ]
            then
                shnsplit -f "$file" -o "cust ext=mp3 lame -b 320 - %f -" "$1" -t "%n - %t" 2>&1 | \
                gawk -vvar=$tracks 'NR>=1 && NR<=var {print "#Track ",NR," of ", var;print (NR-1)*100/var};{fflush();}' | \
                (if `zenity --title="Splitting Tracks..." --progress --auto-close --percentage=0`;
                then
                    echo 'done'
                else
                  killall shnsplit
                  exit 1
                fi)
                
                if [ $? = 1 ]
                then
                    exit 0
                fi
                
            else
                shnsplit -f "$file" -o "cust ext=mp3 lame -b 192 - %f -" "$1" -t "%n - %t" 2>&1 | \
                gawk -vvar=$tracks 'NR>=1 && NR<=var {print "#Track ",NR," of ", var;print (NR-1)*100/var};{fflush();}' | \
                (if `zenity --title="Splitting Tracks..." --progress --auto-close --percentage=0`;
                then
                    echo 'done'
                else
                  killall shnsplit
                  exit 1
                fi)
                
                if [ $? = 1 ]
                then
                    exit 0
                fi
    
        fi
        rm -f 00*pregap*
        
        j=1
        while [ $j -le $tracks ]
        do
            title=${all_titles%%|*}
            if [ "$nperformer" -ne 1 ]
            then
                artist=${all_artists%%|*}
            else
                artist=$oneartist
            fi
            num=`printf "%02d" $j`
            if [ "$title" != "#####" ]; then mp3info -t "$title" "${num} - $title.mp3"; fi
            if [ "$artist" != "#####" ]; then mp3info -a "$artist" "${num} - $title.mp3"; fi
            if [ "$album" != "#####" ]; then mp3info -l "$album" "${num} - $title.mp3"; fi
            mp3info -y "$date" -n "$j" -g "$genre" "${num} - $title.mp3"
            j=$(( $j + 1 ))
            all_titles=${all_titles#*|}
            all_artists=${all_artists#*|}
        done  

                fi

exit 0 
```

need to make executable right click on your ape/flac/wav file and find your convert.sh file easy usage


**also really useful**


 this here with a gui called g[cue2tracks]("http://www.webupd8.org/2009/12/gcue2tracks-splits-compressed-audio-cd.html")

---

### Post by Spike-X on 2011-02-25
Finally, one that works! Thank you!

---

### Post by cokicd on 2011-05-19
Hi, I'm the developer of this script, there's a new version available.
Check: [http://code.google.com/p/split-lossless/](http://code.google.com/p/split-lossless/)

---

### Post by shantiq on 2011-05-19
thanx man it is such a cool and useful script

---

### Post by cokicd on 2011-05-20
> **shantiq said:**
> thanx man it is such a cool and useful script

I'm glad you like it :)

Cheers

---

### Post by normski9 on 2011-05-26
Hi
I am a noob - question where are the files saved?

great script by the way

---

### Post by shantiq on 2011-05-26
they go to your home folder:KS

---

### Post by normski9 on 2011-05-26
Hi Santiq
Thanks for the quick reply:o

Nope they aint there:confused:

---

### Post by normski9 on 2011-05-26
Ooops sorry Shantiq :rolleyes:

---

### Post by normski9 on 2011-05-27
Hi
Just downloaded latest update and now
files are in Home folder :)

Thanks a million cokicd :P :P

---

### Post by intel352 on 2011-06-02
Just use Flacon, it does splitting & conversion without any issues, it's fast, supports FLAC/APE/CUE, and is a native Ubuntu GUI/app.

Found it while combing the Software Center for something to convert my FLAC+CUE files, worked perfect :-D

---

### Post by shantiq on 2011-06-02
:KS  thanx never heard of it before  [** here**]("https://launchpad.net/~flacon/+archive/ppa") it is

really smooth

```
sudo add-apt-repository ppa:flacon/ppa
```


```
sudo apt-get update

```



```
sudo apt-get install flacon

```

---

### Post by shantiq on 2011-12-02
also PPA for split lossless


```
sudo add-apt-repository ppa:cokicd/split-lossless
sudo apt-get update
sudo apt-get install split-lossless
```

---

### Post by sonicb00m on 2012-01-17
Handy! Thanks!

---

