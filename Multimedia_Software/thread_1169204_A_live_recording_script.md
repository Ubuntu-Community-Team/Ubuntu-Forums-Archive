---
title: "A live recording script"
date: 2009-05-24
forum: Multimedia Software
---

### Post by xzero1 on 2009-05-24
This script is designed to record live video unattended with an option to shutdown and poweroff afterwards. The script also computes the current and estimated total file size, bps as well as the time left for the recording in a running live mode. It can be interrupted and warns the user of possible impending shutdown.

Although designed specifically for a hauppauge hd-pvr recorder, this script can be adopted for other uses.

```
#!/bin/bash

trap 'pkill -ALRM cat;echo;exit' SIGINT 

while getopts "t:b:v:p:hS" options; do
  case $options in
    t ) time=$OPTARG;;
    b ) bps=$OPTARG;;
    v ) dev=$OPTARG;;
    h ) help=1;;
    S ) shtdwn=1;;
    ? ) echo $usage
        exit 1;;
  esac
done

shift $(($OPTIND - 1))
fname=$1

if  [ $# -eq 0 ] || [ $help ]
then
  printf "Usage: [options] filename

  Optional Arguments:
     -h help
     -t (time) recording time h:mm
     -b (mbps) megabits per secound 
     -v (n) video device index
     -S shutdown and poweroff when finished\n\n"
  exit
fi

if [ $dev ] 
then 
  index=$dev
else
  index=0  # DEFAULT
fi

if [ $bps ]
then
    if [ $bps -gt 13 ]
    then
       bitrate=13500000
       echo 'MAX BITRATE SET'
    else
       bitrate=$(($bps*1000000))
    fi
    v4l2-ctl --device=/dev/video$index --set-ctrl=video_bitrate=$bitrate
    sleep .2
    v4l2-ctl --device=/dev/video$index -l
    sleep .2
fi

# EXECUTABLE STATEMENT
cat /dev/video$index > $fname &

if [ $time ]
then
  mins=${time:2}
  hours=${time:0:1}
  mins=$((mins+$hours*60))
  echo $mins
  echo
# NOTE SUDOERS FILE MUST BE ADJUSTED FOR THIS TO WORK
  if [ $shtdwn ]
  then
    sudo shutdown -P +$(($mins+10)) & 
    sleep 1 # GIVE TIME FOR SHUTDOWN NOTICE
  fi

  printf "\nDone    time left      avg bps           est size          cur size\n"  
  for ((t=1; t <= $mins ; t++))
  do
    sleep 1m
    size=`du -b $fname`
    size=`expr match "$size" '\([0-9]*\)'`    
    printf "(%3d%s) %3d%s     %9d bps        ~%4d MB     %9d MB\r" "$((100*t/$mins))" "%" "$(($mins-t))" " mins" "$((8*size/(t*60)))" "$(($mins*size/(t*1024*1024)))" "$((size/(1024*1024)))"
  done                           # A construct borrowed from 'ksh93'.
  pkill -ALRM cat

fi
echo




```Sample run snapshot:

```
kdog@kdog-desktop:~/FOO$ tr.sh -t 2:00 -b 14 -v 1 -S test.ts
MAX BITRATE SET
                     brightness (int)  : min=0 max=255 step=1 default=134 value=134 flags=slider
                       contrast (int)  : min=0 max=255 step=1 default=128 value=128 flags=slider
                     saturation (int)  : min=0 max=255 step=1 default=128 value=128 flags=slider
                            hue (int)  : min=0 max=255 step=1 default=128 value=128 flags=slider
                      sharpness (int)  : min=0 max=255 step=1 default=128 value=128 flags=slider
                 audio_encoding (menu) : min=3 max=4 default=3 value=4 flags=update
                 video_encoding (menu) : min=2 max=2 default=2 value=2
             video_bitrate_mode (menu) : min=0 max=1 default=1 value=0 flags=update
                  video_bitrate (int)  : min=1000000 max=13500000 step=100000 default=6500000 value=13500000
             video_peak_bitrate (int)  : min=1100000 max=20200000 step=100000 default=9000000 value=20200000
120


Broadcast message from root@kdog-desktop
    (unknown) at 18:20 ...

The system is going down for power off in 130 minutes!

Done    time left      avg bps           est size          cur size
(  3%) 116 mins       5787374 bps        ~4967 MB           165 MB

```

---

### Post by Ginger The Cat on 2010-02-09
This script is just what I'm looking for but I want unattended audio recording using a simple microphone plugged directly into my laptop.

Can anyone help with modifying it?

Thanks

Mike

---

